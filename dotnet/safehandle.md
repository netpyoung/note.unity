SafeHandle
==========

https://sites.google.com/site/gsfzero1/


https://blogs.msdn.microsoft.com/bclteam/2005/03/15/safehandles-the-best-v2-0-feature-of-the-net-framework-ravi-krishnaswamy/

C#에서 C++ DLL 사용하기
https://libsora.so/posts/csharp-cpp-dll/


Managed Resource
- SafeHandle객체와 같이 내부에 Unmanaged Resource를 가지고 있더라도, 안전하게 해제되는 매커니즘을 갖춤.

Unmanaged Resource
- garbage Collector 로 객체 추적 해제 불가능
- IntPtr핸들 제어 등등.



문제
* loader-lock
* double P/Invoke


종결자가 있는 객체의 종료처리는 복잡하고 시간이 걸리기 때문에 종결자 보다는 IDisposable.Dispose( )를 사용하는 것이 좋다


magazine
msdn.microsoft.com/en-us/magazine/bb985010.aspx


SafeHandleZeroOrMinusOneIsInvalid


[SuppressUnmanagedCodeSecurity]
  internal static class MyNativeMethods {
     [DllImport(“myNativeDll”, SetLastError=true), ReliabilityContract(Consistency.WillNotCorruptState, Cer.MayFail)]
      private static extern Int32 CreateHandle(out Int32 handle);

      [DllImport(“myNativeDll”, SetLastError=true), ReliabilityContract(Consistency.WillNotCorruptState, Cer.Success)]
      private static extern bool CloseHandle(IntPtr handle);

  }


## pinvoke
Platform Invocation Services (PInvoke) allows managed code to call unmanaged functions that are implemented in a DLL.
[Platform Invoke Tutorial](https://msdn.microsoft.com/en-us/library/aa288468(v=vs.71).aspx)




https://blogs.msdn.microsoft.com/bclteam/2006/06/23/how-to-use-safehandle-in-a-resilient-library-brian-grunkemeyer/
