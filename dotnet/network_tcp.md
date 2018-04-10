# [TcpClient](https://github.com/dotnet/corefx/blob/master/src/System.Net.Sockets/src/System/Net/Sockets/TCPClient.cs)

``` csharp
public class TcpClient : IDisposable

public NetworkStream GetStream();
```

* fixed message length
* using message length packet
* using Custom message marker




# Timeout
asyncResult = searchSocket.BeginConnect(address, port, null, null);
isTimeout = asyncResult.AsyncWaitHandle.WaitOne(timeoutMillisec, false);
searchSocket.EndConnect(asyncResult);
https://www.codeproject.com/Articles/31514/Implementation-of-Connecting-a-Socket-with-Timeout

# NetworkStream
https://github.com/dotnet/corefx/blob/master/src/System.Net.Sockets/src/System/Net/Sockets/NetworkStream.cs
https://github.com/kerryjiang/SuperSocket.ClientEngine/blob/master/Core/NetworkStream.cs
.Flush()




# Socket

# SocketAsyncEventArgs
https://github.com/tangxuehua/SocketAsyncEventArgsSample/blob/master/SocketAsyncClient/SocketClient.cs
https://github.com/dotnet/corefx/blob/master/src/System.Net.Sockets/src/System/Net/Sockets/SocketAsyncEventArgs.cs







======

## TcpListener - connection / TcpClient

Start()
Stop()
AcceptTcpClient()



APM (Asynchronous Programming Model)
 APM 방식은 BeginAcceptTcpClient() / EndAcceptTcpClient() 와 같이 Begin* / End* 2개의 메서드를 쌍으로 사용하는 방식으로 Backward Compatibility를 위해 사용된다.

TAP (Task-based Asynchronous Pattern)
 TAP 방식은 AcceptTcpClientAsync() 와 같이 끝에 Async 가 붙는 메서드를 C# await 와 함께 사용하는 방식으로 비동기 처리를 단순화한 현대적 방식이다.



SocketOptionLevel.Tcp
BsdUrgent Boolean 0, 1 Urgent data as defined in RFC-1122.
Expedited Boolean 0, 1 Expedited data as defined in RFC-1122.
NoDelay Boolean 0, 1 Disallow delay for data merging (Nagle’s
algorithm).

========
SocketException
public override int ErrorCode {get;}
public virtual string Message {get;}


TcpClient client = new TcpClient(server, port);
BinaryWriter out = new BinaryWriter(new BufferedStream(client.GetStream()));


## TCP/IP Sockets in C# - chapter 4 Beyond the Basics
