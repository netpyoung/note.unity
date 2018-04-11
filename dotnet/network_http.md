HTTP
=====


https://github.com/restsharp/RestSharp/blob/master/RestSharp/Http.Async.cs

http://seesaawiki.jp/w/haruyama_seigo/d/%bf%a6%be%ec%a4%cb%cb%be%a4%e0%a4%e2%a4%ce





# HttpWebRequest
http://www.matlus.com/httpwebrequest-asynchronous-programming/

HttpWebRequests
ServicePointManager.DefaultConnectionLimit = connectionLimit; // default = 2;
ServicePointManager.Expect100Continue = false;
var servicePoint = ServicePointManager.FindServicePoint(new Uri("http://www.google.ca"));
servicePoint.UseNagleAlgorithm = false; // api서버에선 true로 해야할듯.

# no proxy
HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create("http://mywebsite.com");
req.Proxy = null;

# specify proxy
string proxyUrl = "proxy.myproxy.com";
int proxyPort = 8080;
WebProxy myProxy = new WebProxy(proxyUrl, proxyPort);
HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create("http://mywebsite.com");
req.Proxy = myProxy;





# HttpClient

http://www.matlus.com/httpclient-net-4-5/

tcp 천이도 : http://www.tcpipguide.com/free/t_TCPOperationalOverviewandtheTCPFiniteStateMachineF-2.htm


http://www.e-reading.club/bookreader.php/136904/TCP%7CIP_Sockets_in_C:_Practical_Guide_for_Programmers.pdf
https://www.codeproject.com/Articles/884583/Advanced-TCP-socket-programming-with-NET

TCP/IP Sockets in C#: Practical Guide for Programmers (The Practical Guides) 1st Edition
