## LEARN YOU THE NODE.JS FOR MUCH WIN!  <font color=#8A8A8A>为了赢得更多学习 Node.js</font>
 
HTTP FILE SERVER (Exercise 11 of 13)  
<font color=#8A8A8A>HTTP 文件服务器 (习题11)</font>

Write an HTTP server that serves the same text file for each request it receives.  
<font color=#8A8A8A>编写一个HTTP服务器，为每个接收到的请求提供相同的文本文件。</font>

Your server should listen on the port provided by the first argument to your program.  
<font color=#8A8A8A>你的服务器应该监听你的程序第一个命令行参数所提供的端口</font>

You will be provided with the location of the file to serve as the second command-line argument. You must use the fs.createReadStream() method to stream the file contents to the response.  
<font color=#8A8A8A>你的程序的第二个命令行参数会提供给你所需要的文本文件的位置。你必须使用 fs.createReadStream() 方法将文件内容流式传输到响应</font>
 ─────────────────────────────────────────────────────────────────────────────  
   
### HINTS

### <font color=#8A8A8A>提示</font>
  
   
Because we need to create an HTTP server for this exercise rather than a generic TCP server, we should use the http module from Node core. Like the net module, http also has a method named http.createServer() but this one creates a server that can talk HTTP.  
<font color=#8A8A8A>因为我们需要创建一个 HTTP 服务而不是通用的 TCP 服务来完成这个练习，所以我们应该使用来自 Node 核心的 http 模块。和 net 模块类似，http 模块也拥有一个叫做 http.createServer() 的方法，但是它所创建的是一个可以与 HTTP 通信的服务器。</font>

http.createServer() takes a callback that is called once for each connection received by your server. The callback function has the signature:  
<font color=#8A8A8A>http.createServer() 接收一个回调函数作为参数，回调函数会在你的服务器每一次进行连接的时候执行，这个回调函数有以下的特征：</font>

   
     function callback (request, response) { /* ... */ }  
   
Where the two arguments are objects representing the HTTP request and the corresponding response for this request. request is used to fetch properties, such as the header and query-string from the request while response is for sending data to the client, both headers and body.  
<font color=#8A8A8A>在这里，这两个参数是代表的是 HTTP 请求的对象以及对此请求的相应响应。request 用来从请求中获取一些的属性，例如请求头和查询字符串，而 response 会将数据发送给客户端，包括响应头和响应主体。</font>
 
Both request and response are also Node streams! Which means that you can use the streaming abstractions to send and receive data if they suit your use-case.  
<font color=#8A8A8A>因为 request 和 response 都是 Node 流！这意味着，如果适合你的使用情况的话，你可以使用流式抽象来实现发送和接收数据。</font> 
   
http.createServer() also returns an instance of your server. You must call server.listen(portNumber) to start listening on a particular port.  
<font color=#8A8A8A>http.createServer() 会返回一个 HTTP 服务器的实例。你必须调用 server.listen(portNumber) 方法去监听一个特定的端口。</font>
   
A typical Node HTTP server looks like this:  
<font color=#8A8A8A>一个典型的 Node HTTP 服务器将会是这个样子：</font>
   
     var http = require('http')  
     var server = http.createServer(function (req, res) {  
       // request handling logic...  
     })  
     server.listen(8000)  
   
Documentation on the http module can be found by pointing your browser here: 
<font color=#8A8A8A>http 模块的文档你可以使用浏览器访问如下路径来查看：</font> 
  file:///Users/dllo/.nvm/versions/node/v8.9.4/lib/node_modules/learnyounode/node_apidoc  
  /http.html  
   
  The fs core module also has some streaming APIs for files. You will need to use the fs.createReadStream() method to create a stream representing the file you are given as a command-line argument. The method returns a stream object which you can use src.pipe(dst) to pipe the data from the src stream to the dst stream. In this way you can connect a filesystem stream with an HTTP response stream.  
<font color=#8A8A8A>fs 这个核心模块也含有一些 stream API 用来处理文件。你需要使用 fs.createReadStream() 方法给命令行参数提供的文件创建一个 stream。这个方法会返回一个 stream 对象，这个对象可以使用 src.pipe(dst) 的方法把数据从 src 流传输到 dst 流中。通过这种形式，你可以把一个文件系统的 流和 HTTP 响应流连接起来。</font>
   
 ─────────────────────────────────────────────────────────────────────────────  
   
   » To print these instructions again, run: learnyounode print                   
   <font color=#8A8A8A>要再次打印这些说明，请运行：learnyounode print</font>  
   » To execute your program in a test environment, run: learnyounode run program.js  
   <font color=#8A8A8A>要在测试环境中执行程序，执行：learnyounode 运行 program.js</font>                                                                 
   » To verify your program, run: learnyounode verify program.js       
   <font color=#8A8A8A>要验证您的程序，请运行：learnyounode verify program.js</font>           
   » For help run: learnyounode help  
   <font color=#8A8A8A>需要帮助请运行：learnyounode help</font>