# Information

# namespace
## using System.Net; // For Dns, IPHostEntry, IPAddress
## using System.Net.Sockets; // For SocketException



# data
## [IPEndPoint](https://github.com/dotnet/corefx/blob/master/src/System.Net.Primitives/src/System/Net/IPEndPoint.cs)
* private IPAddress _address;
* ip + port

``` csharp
class IPEndPoint : EndPoint


IPAddress address = new IPAddress(hostname);
byte[] ipbytes = address.GetAddressBytes();
IPAddress[] addresses = Dns.GetHostAddresses(hostname);
```

## [EndPoint](https://github.com/dotnet/corefx/blob/master/src/System.Net.Primitives/src/System/Net/EndPoint.cs)
``` csharp
abstract class EndPoint

public virtual AddressFamily
public virtual SocketAddress Serialize()
public virtual EndPoint Create(SocketAddress socketAddress)
```

## [SocketAddress](https://github.com/dotnet/corefx/blob/master/src/Common/src/System/Net/SocketAddress.cs)
* how to format the memory buffers that the platform uses for network addresses.

``` csharp
internal / public class SocketAddress
```

## [IPAddress](https://github.com/dotnet/corefx/blob/master/src/System.Net.Primitives/src/System/Net/IPAddress.cs)
* /// Provides an Internet Protocol (IP) address.
* ip address:  string  <-> long
* HostToNetworkOrder
* NetworkToHostOrder

``` csharp
class IPAddress
public static bool TryParse(string ipString, out IPAddress address)
```

## [Dns](https://github.com/dotnet/corefx/blob/master/src/System.Net.NameResolution/src/System/Net/DNS.cs)
``` csharp
static class Dns
IPHostEntry hostInfo = Dns.GetHostByName("www.contoso.com");
```


``` csharp
IPAddress[] addresses = Dns.GetHostAddresses(hostname);

foreach (IPAddress address in addresses)
{
    Debug.Assert(address.AddressFamily == AddressFamily.InterNetwork ||
                 address.AddressFamily == AddressFamily.InterNetworkV6);

    if ((address.AddressFamily != AddressFamily.InterNetwork || !Socket.OSSupportsIPv4) &&
        !Socket.OSSupportsIPv6)
    {
        continue;
    }

```


## [IPHostEntry](​https://github.com/dotnet/corefx/blob/master/src/System.Net.NameResolution/src/System/Net/IPHostEntry.cs)

* ip + hostname
``` csharp
class IPHostEntry
private IPAddress[] _addressList;

// DNS : hostname -> ip
IPHostEntry hostEntry = Dns.Resolve(hostname);
IPHostEntry hostEntry = Dns.GetHostEntry("www.google.com");
hostEntry.HostName
hostEntry.AddressList

// Reverse DNS : ip -> host/domain
IPAddress ipaddr = IPAddress.Parse("10.11.8.124");
IPHostEntry hostEntry = Dns.GetHostEntry(ipaddr);
```


# ref
* http://www.csharpstudy.com/
* https://github.com/dotnet/corefx
* TCP/IP Sockets in C#
