# overview
Actor
* 상태를 가짐
* 메시지를 받음
* 한번에 하나의 메시지를 처리
Props
* Actor를 만들어 내는 템플릿
ActorSystem
* An ActorSystem is a heavyweight structure that will allocate 1...N Threads, so create one per logical application.
*
ActorContext
* 접근 가능 Parent/Children/Sender

ActorSelection
* I need to take advantage of wildcard selection in actor paths for some reason.
* I need to communicate with an actor on a remote actor system, and I don’t have an actor reference for it yet.

ActorRef
* Actor는 ActorRef라는 핸들로 접근
* ActorRef를 통해 Actor에 메시지를 전송
Akka.Remote
* 원격 Actor를 만들 수 있음
* 원격 Actor에 메시지를 보낼 수 있음
Akka.Cluster
* Remote확장
Actor Life Cycle
* https://github.com/petabridge/akka-bootcamp/blob/master/src/Unit-1/lesson6/README.md

ReceiveActor
* message handing


BecomeStacked / UnbecomeStacked

HOCON (Human-Optimized Config Object Notation)

Guardians
* /
* /user
* /system - for framework level.

Schedular - ActorSystem


IWithBoundedStash / IWithUnboundedStash


Router
* A Router actually is an actor, but with one critical difference: it can process more than one message at a time.
* The purpose of a Router is to route messages onward, NOT to process them.
* There are two types of routers: Pool routers, and Group routers.

RoutingStrategys
* Broadcast
* Random
* ConsistentHash
Group

Pool
* The key difference is that pool routers create and manage their routees, whereas group routers do not.

ReceiveTimeout

PipeTo
* Async message processing using
* https://github.com/petabridge/akka-bootcamp/blob/master/src/Unit-3/lesson4/README.md




https://github.com/petabridge/akka-bootcamp/blob/master/src/Unit-1/lesson1/README.md
http://wiki.webnori.com/display/AKKA/ReceiveActor


#akka.interfaced

https://github.com/SaladLab/Akka.Interfaced/blob/15ba21baa89bc2c4f6fe267a66de718f4573b75b/samples/SlimHttp/Program.Client/SlimRequestWaiter.cs




## Akka.net
https://pt.slideshare.net/veblush/akkanet-ndc2016


interface!!!
http://veblush.github.io/ko/posts/akkanet-online-game-works-for-the-last-2-months/



akka.net

http://getakka.net/docs/Getting%20started


https://www.codeproject.com/Articles/1007161/A-Look-At-Akka-NET

https://github.com/petabridge/akka-bootcamp


// 메시지(패킷) 구조
Greet : message

// 엑터 : 메시지 처리
GreetingActor : ReceiveActor
Receive<X>(data => { ... });


// 새로운 시스템을 만들고
system = Actor.System.Create("MySystem");

// 시스템에서 엑터를 얻어와서,
greeter = system.ActorOf<GreetingActor>("greeter");

// 엑터에게 메시지를 보낸다.
greeter.Tell(new Greet("World"));


// typed actor
facadeTypedActor.doStuff()
facadeActor.tell(DoStuff)

// akka.config
// var config = ConfigurationFactory.ParseString(File.ReadAllText
