# HTTP详解 (Anatomy of an HTTP Transaction)
- 创建Server (Create the Server)
- Method, URL and Headers
- Request Body
- A Quick Thing About Errors
- What We've Got so Far
- HTTP Status Code
- Setting Response Headers
- Explicitly Sending Header Data
- Sending Response Body
- Another Quick Thing About Errors
- Put It All Together
- Echo Server Example

>The purpose of this guide is to impart a solid understanding of the process of Node.js HTTP handling. We'll assume that you know, in a general sense, how HTTP requests work, regardless of language or programming environment. We'll also assume a bit of familiarity with Node.js EventEmitters and Streams. If you're not quite familiar with them, it's worth taking a quick read through the API docs for each of those.

本指南的目的是让您充分了解Node.js中`HTTP`模块的工作的原理。在不考虑何种编程语言的情况下,我们假设您已经知晓HTTP请求是如何工作的。同时假设您了解一点Node.js中关于[EventEmitters](https://nodejs.org/api/events.html)和[Streams](https://nodejs.org/api/stream.html)的知识。如果你不是十分熟悉它们，建议花点时间去快速的浏览一下API Docs中的关于它们的介绍。

## 创建Server (Create the Server)
>Any node web server application will at some point have to create a web server object. This is done by using createServer.

在某些时候，任何一个Node web服务器程序都必须创建web Server对象。 创建Web Server对象是通过使用`createServer()`方法实现的。
```
const http = require('http');

const server = http.createServer((request, response) => {
  // magic happens here!
});
```

>The function that's passed in to createServer is called once for every HTTP request that's made against that server, so it's called the request handler. In fact, the Server object returned by createServer is an EventEmitter, and what we have here is just shorthand for creating a server object and then adding the listener later.

一旦向服务器发起HTTP请求，传入`createServer(function(){})`方法的函数就会被调用。因此该函数被称为**请求处理程序**。实际上，`createServer()`方法返回的`Server`对象是一个`EventEmitter`(事件触发器)。我们这里只是简单的创建了一个Server对象，稍后会添加监听器。

```
const server = http.createServer();
server.on('request', (request, response) => {
  // the same kind of magic happens here!
});
```
>When an HTTP request hits the server, node calls the request handler function with a few handy objects for dealing with the transaction, request and response. We'll get to those shortly.

当一个HTTP请求访问服务器的时候，node(使用几个方便的对象来)调用请求处理函数来处理请求和响应。

>In order to actually serve requests, the listen method needs to be called on the server object. In most cases, all you'll need to pass to listen is the port number you want the server to listen on. There are some other options too, so consult the API reference.

为了处理实际的服务器请求，需要在`Server`对象上调用`listen()`方法。在大多数情况下，你要做的是把需要服务器监听的端口号传递给`listen()`。还有一些其他选项，请参考[API reference](https://nodejs.org/dist/latest-v10.x/docs/api/net.html#net_server_listen)

## Method, URL and Headers
>When handling a request, the first thing you'll probably want to do is look at the method and URL, so that appropriate actions can be taken. Node makes this relatively painless by putting handy properties onto the request object.

在处理请求的时候，你要做的第一件事可能就是查看请求所使用的`method`(方法)和url(请求地址)，以便采取相应的操作。Node通过在请求对象上设置的一些属性让这件事变得相对轻松。

```
const { method, url } = request;
```

>Note: The request object is an instance of IncomingMessage.

注：`request`对象是`IncomingMessage`类的一个实例。

>The method here will always be a normal HTTP method/verb. The url is the full URL without the server, protocol or port. For a typical URL, this means everything after and including the third forward slash.

这里的`method`始终都是一个普通的HTTP`method`。`url`是一个完整的`url`（没有服务器、协议、端口号)，一个典型的`URL`应该包括第三个斜杠及之后的所有内容。(测试失败：发起URL:http://localhost/products  返回URL: '/')

>Headers are also not far away. They're in their own object on request called headers.

请求头的相关信息可以从`request`对象的`header`对象中获取。

```
const { headers } = request;
const userAgent = headers['user-agent'];
```

>It's important to note here that all headers are represented in lower-case only, regardless of how the client actually sent them. This simplifies the task of parsing headers for whatever purpose.

在这里需要注意的是，不管客户端发送请求头的形式，所有的请求头都需要用小写表示。这样可以简化解析请求头的任务。


>If some headers are repeated, then their values are overwritten or joined together as comma-separated strings, depending on the header. In some cases, this can be problematic, so rawHeaders is also available.

如果重复请求头，根据请求头的不同，它们的值可能会被覆盖，也可能使用逗号链接在一起。在某些情况下，这可能会出问题，因此`rawHeaders也是可用的。

## Request Body
>When receiving a POST or PUT request, the request body might be important to your application. Getting at the body data is a little more involved than accessing request headers. The request object that's passed in to a handler implements the ReadableStream interface. This stream can be listened to or piped elsewhere just like any other stream. We can grab the data right out of the stream by listening to the stream's 'data' and 'end' events.

当收到`POST`或`PUT`请求时，对app来说，请求正文可能会很重要。获取正文数据比访问请求头复杂一些。传递给处理程序的请求对象实现了`ReadableStream`接口。就像任何其他`stream`一样，可以监听或传输这个`stream`到其他地方。通过监听`stream`的`data`和`end`事件，我们可以直接从`stream`中获取数据。

>The chunk emitted in each 'data' event is a Buffer. If you know it's going to be string data, the best thing to do is collect the data in an array, then at the 'end', concatenate and stringify it.

每个`data`事件中触发的数据块是一个buffer。如果你知道它会是字符串数据，那么最好的方法是在数组中收集数据，然后在`end`事件中连接并字符串化。

```
let body = [];
request.on('data', (chunk) => {
  body.push(chunk);
}).on('end', () => {
  body = Buffer.concat(body).toString();
  // at this point, `body` has the entire request body stored in it as a string
});
```

>Note: This may seem a tad tedious, and in many cases, it is. Luckily, there are modules like concat-stream and body on npm which can help hide away some of this logic. It's important to have a good understanding of what's going on before going down that road, and that's why you're here!

注意：这看起来有点单调乏味，而且在很多情况下都是如此。 幸运的是，在npm上有像concat-stream和body这样的模块可以帮助简化一些逻辑。 在走这条路之前，要很好地了解正在发生的事情，这就是为什么你在这里！


## A Quick Thing About Errors
>Since the request object is a ReadableStream, it's also an EventEmitter and behaves like one when an error happens.

由于`request`对象是一个ReadableStream，所以它也是一个EventEmitter，行为像错误发生时的行为。

>An error in the request stream presents itself by emitting an 'error' event on the stream. If you don't have a listener for that event, the error will be thrown, which could crash your Node.js program. You should therefore add an 'error' listener on your request streams, even if you just log it and continue on your way. (Though it's probably best to send some kind of HTTP error response. More on that later.)

请求流中的错误通过触发stream上的`error`事件展示的。如果你没有该事件的监听器，则会抛出error，并可能导致Node.js程序崩溃。你应该在你的请求流上添加`error`监听器，即使你仅是记录它并继续下一步。(尽管发送某种HTTP erroe响应可能是最好的)

```
request.on('error', (err) => {
  // This prints the error message and stack trace to `stderr`.
  console.error(err.stack);
});
```
>There are other ways of handling these errors such as other abstractions and tools, but always be aware that errors can and do happen, and you're going to have to deal with them.

还有其他方式来处理这些错误，比如其他abstractions和工具。但始终要注意错误确实可能会发生，你将不得不处理它们。

## What We've Got so Far
At this point, we've covered creating a server, and grabbing the method, URL, headers and body out of requests. When we put that all together, it might look something like this:

此刻，我们已经学习了创建server对象，并从请求中获取`method` `url` `headers`和`body`。当我们把这些放在一起，它可能看起来像这样：
```
const http = require('http');

http.createServer((request, response) => {
  const { headers, method, url } = request;
  let body = [];
  request.on('error', (err) => {
    console.error(err);
  }).on('data', (chunk) => {
    body.push(chunk);
  }).on('end', () => {
    body = Buffer.concat(body).toString();
    // At this point, we have the headers, method, url and body, and can now
    // do whatever we need to in order to respond to this request.
  });
}).listen(8080); // Activates this server, listening on port 8080.
```

>If we run this example, we'll be able to receive requests, but not respond to them. In fact, if you hit this example in a web browser, your request would time out, as nothing is being sent back to the client.

运行上面这个例子，我们可以收到request,但是不会响应请求。事实上，如果你在浏览器中运行它，你的请求会超时，因为没有任何内容发送回客户端。

>So far we haven't touched on the response object at all, which is an instance of ServerResponse, which is a WritableStream. It contains many useful methods for sending data back to the client. We'll cover that next.

到目前为止，我们还没有讨论`response`对象，`response`对象是`ServerResponse`类的一个实例,它是一个`WritableStream`。它包含许多有用的方法用于返回数据给客户端。接下来，我们将介绍。


## HTTP Status Code
>If you don't bother setting it, the HTTP status code on a response will always be 200. Of course, not every HTTP response warrants this, and at some point you'll definitely want to send a different status code. To do that, you can set the statusCode property.

如果你不进行设置，HTTP响应的状态码始终为200.当然不是每个HTTP响应都能保证这一点。在某些时候，你肯定希望发送不同的状态码。为此，可以设置`statusCode`属性。

```
response.statusCode = 404; // Tell the client that the resource wasn't found.
```

>There are some other shortcuts to this, as we'll see soon.

有许多其他一些快捷方式，我们很快会看到。

## Setting Response Headers
>Headers are set through a convenient method called setHeader.

通过`setHeader()`方法可以很方便的设置响应头。

```
response.setHeader('Content-Type', 'application/json');
response.setHeader('X-Powered-By', 'bacon');
```

>When setting the headers on a response, the case is insensitive on their names. If you set a header repeatedly, the last value you set is the value that gets sent.

当设置响应头的时候，响应头的名字是区分大小写的。如果你重复设置响应头，最后一个值会被发送。

## Explicitly Sending Header Data
>The methods of setting the headers and status code that we've already discussed assume that you're using "implicit headers". This means you're counting on node to send the headers for you at the correct time before you start sending body data.

我们已经讨论了设置响应头和状态码的方法,假设您使用的是隐式响应头，这意味着在开始发送正文数据之前，要指望node在正确的时间，为你发送响应头。

>If you want, you can explicitly write the headers to the response stream. To do this, there's a method called writeHead, which writes the status code and the headers to the stream.

如果需要，你可以显式的将响应头写入响应流。为此，有一个名为`writeHead()`的方法，可以将状态码和响应头写入流。

```
response.writeHead(200, {
  'Content-Type': 'application/json',
  'X-Powered-By': 'bacon'
});
```
>Once you've set the headers (either implicitly or explicitly), you're ready to start sending response data.

一旦你设置了响应头(隐式或显式)，你可以准备发送响应数据了。

## Sending Response Body
>Since the response object is a WritableStream, writing a response body out to the client is just a matter of using the usual stream methods.

因为`response`对象是一个`WritableStream`，所以写给客户端的响应正文仅使用常用的流方法即可。

```
response.write('<html>');
response.write('<body>');
response.write('<h1>Hello, World!</h1>');
response.write('</body>');
response.write('</html>');
response.end();
```


>The end function on streams can also take in some optional data to send as the last bit of data on the stream, so we can simplify the example above as follows.

`end`函数也可以接收一些可选的数据作为流上的最后一位数据发送，因此我们可以简化上面的示例。

```
response.end('<html><body><h1>Hello, World!</h1></body></html>');
```

>Note: It's important to set the status and headers before you start writing chunks of data to the body. This makes sense, since headers come before the body in HTTP responses.

注意：在开始向正文写入数据库之前，设置状态码和响应头是很重要的，因为在HTTP响应中，响应头在前，响应正文在后。

## Another Quick Thing About Errors
>The response stream can also emit 'error' events, and at some point you're going to have to deal with that as well. All of the advice for request stream errors still applies here.

responese流也可以触发`error`事件，在某些时候，你还必须处理这些事件。所有关于请求流的错误的建议在这里仍然适用。

## Put It All Together
>Now that we've learned about making HTTP responses, let's put it all together. Building on the earlier example, we're going to make a server that sends back all of the data that was sent to us by the user. We'll format that data as JSON using JSON.stringify.

现在我们已经了解了如何创建HTTP响应。让我们把他们放在一起。在前面示例的基础上，我们将创建一个服务器，返回所有用户发送给我们的数据。我们会使用`JSON.stringify`方法将数据格式化为JSON。


```
const http = require('http');

http.createServer((request, response) => {
  const { headers, method, url } = request;
  let body = [];
  request.on('error', (err) => {
    console.error(err);
  }).on('data', (chunk) => {
    body.push(chunk);
  }).on('end', () => {
    body = Buffer.concat(body).toString();
    // BEGINNING OF NEW STUFF

    response.on('error', (err) => {
      console.error(err);
    });

    response.statusCode = 200;
    response.setHeader('Content-Type', 'application/json');
    // Note: the 2 lines above could be replaced with this next one:
    // response.writeHead(200, {'Content-Type': 'application/json'})

    const responseBody = { headers, method, url, body };

    response.write(JSON.stringify(responseBody));
    response.end();
    // Note: the 2 lines above could be replaced with this next one:
    // response.end(JSON.stringify(responseBody))

    // END OF NEW STUFF
  });
}).listen(8080);
```

## Echo Server Example
>Let's simplify the previous example to make a simple echo server, which just sends whatever data is received in the request right back in the response. All we need to do is grab the data from the request stream and write that data to the response stream, similar to what we did previously.

让我们

```
const http = require('http');

http.createServer((request, response) => {
  let body = [];
  request.on('data', (chunk) => {
    body.push(chunk);
  }).on('end', () => {
    body = Buffer.concat(body).toString();
    response.end(body);
  });
}).listen(8080);
Now let's tweak this. We want to only send an echo under the following conditions:

The request method is POST.
The URL is /echo.
In any other case, we want to simply respond with a 404.

const http = require('http');

http.createServer((request, response) => {
  if (request.method === 'POST' && request.url === '/echo') {
    let body = [];
    request.on('data', (chunk) => {
      body.push(chunk);
    }).on('end', () => {
      body = Buffer.concat(body).toString();
      response.end(body);
    });
  } else {
    response.statusCode = 404;
    response.end();
  }
}).listen(8080);
```

>Note: By checking the URL in this way, we're doing a form of "routing". Other forms of routing can be as simple as switch statements or as complex as whole frameworks like express. If you're looking for something that does routing and nothing else, try router.

注意：通过这种方式检查URL，我们正在做一种“路由”形式。 其他形式的路由可以像switch语句一样简单，也可以像express这样的框架一样复杂。 如果您正在寻找可以进行路由的东西，请尝试使用路由器。


>Great! Now let's take a stab at simplifying this. Remember, the request object is a ReadableStream and the response object is a WritableStream. That means we can use pipe to direct data from one to the other. That's exactly what we want for an echo server!

太好了！现在让我们来简化一下吧。 请记住，请求对象是ReadableStream，响应对象是WritableStream。 这意味着我们可以使用管道将数据从一个引导到另一个。 这正是我们想要的echo服务器！


```
const http = require('http');

http.createServer((request, response) => {
  if (request.method === 'POST' && request.url === '/echo') {
    request.pipe(response);
  } else {
    response.statusCode = 404;
    response.end();
  }
}).listen(8080);
```
>Yay streams!
We're not quite done yet though. As mentioned multiple times in this guide, errors can and do happen, and we need to deal with them.
To handle errors on the request stream, we'll log the error to stderr and send a 400 status code to indicate a Bad Request. In a real-world application, though, we'd want to inspect the error to figure out what the correct status code and message would be. As usual with errors, you should consult the Error documentation.
On the response, we'll just log the error to stderr.

Yay streams!

我们还没有完成。 正如本指南中多次提到的，错误可以而且确实发生，我们需要处理它们。

为了处理请求流上的错误，我们将错误记录到stderr并发送400状态代码以指示错误请求。 但是，在实际应用程序中，我们需要检查错误以确定正确的状态代码和消息是什么。 像往常一样有错误，您应该查阅错误文档。

在响应中，我们只是将错误记录到stderr。

```
const http = require('http');

http.createServer((request, response) => {
  request.on('error', (err) => {
    console.error(err);
    response.statusCode = 400;
    response.end();
  });
  response.on('error', (err) => {
    console.error(err);
  });
  if (request.method === 'POST' && request.url === '/echo') {
    request.pipe(response);
  } else {
    response.statusCode = 404;
    response.end();
  }
}).listen(8080);
```
>We've now covered most of the basics of handling HTTP requests. At this point, you should be able to:
- Instantiate an HTTP server with a request handler function, and have it listen on a port.
- Get headers, URL, method and body data from request objects.
- Make routing decisions based on URL and/or other data in request objects.
- Send headers, HTTP status codes and body data via response objects.
- Pipe data from request objects and to response objects.
- Handle stream errors in both the request and response streams.

我们现在已经介绍了处理HTTP请求的大部分基础知识。 在这一点上，你应该能够
- 从`request`对象中获取headers, URL , method 和 body data
- 根据`request`对象中的URL和/或其他数据确定路由
- 通过`response`对象发送headers,HTTP状态码和响应报文
- 从`request`对象输送数据到`response`对象
- 处理`request`流和`response`流中的stream错误

>From these basics, Node.js HTTP servers for many typical use cases can be constructed. There are plenty of other things these APIs provide, so be sure to read through the API docs for EventEmitters, Streams, and HTTP.

根据这些基础知识，可以构建适用于许多典型用例的Node.jsHTTP服务器。这些API还提供了很多其他功能，因此请务必通读EventEmitter、Streams和HTTP的API文档。


## 参考
- [Anatomy of an HTTP Transaction
](https://nodejs.org/en/docs/guides/anatomy-of-an-http-transaction/)