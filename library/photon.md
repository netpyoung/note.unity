# Photon
* PUN :  The Ease-of-use of Unity's Networking with the Performance & Reliability of Photon Realtime
* Realtime :  Cross-Platform Networking Engine with Advanced Relay for Global Low-latency Games  -- world cloud
* Quantum :  Deterministic Engine for fast Paced Realtime Multiplayer Action Games.  - expensive
* Bolt :  Client-hosted Networking for Unity that Always Connects Your Players  - LAN & WiFi


sadf

# api reference
https://doc-api.exitgames.com/en/pun/current/class_photon_player.html

굳이 상속받지 않더라도  IPunCallbacks 에 정의된 대로 콜백을 받을 수 있음..


# 로그
PhotonNetwork.logLevel = PhotonLogLevel.Full


Photon.MonoBehaviour는 단순히 PhotonView를 캐쉬해놓는 역활만함.

# PunRPC
NetworkingPeer가 관리

PhotonNetwork.PhotonServerSettings.RpcList 에서 관리

https://doc.lagout.org/Others/Game%20Development/Programming/


photon : http://www.urablog.xyz/archive/2016/9


---------------



포톤 접속
OnConnectedToPhoton
OnConnectedToMaster

방만들기
OnPhotonCustomRoomPropertiesChanged(ExitGames.Client.Photon.Hashtable propertiesThatChanged)
OnCreatedRoom
OnJoinedRoom

다른 방에 접속시
OnPhotonPlayerPropertiesChanged
OnPhotonCustomRoomPropertiesChanged
OnJoinedRoom

다른이가 방에 들어왔을시
OnPhotonPlayerConnected

방장이 나갔을시
OnMasterClientSwitched
OnPhotonPlayerDisconnected




int PhotonNetwork.ServerTimestamp : 현재 서버의 1/1000 초 타임스탬프, 타임스탬프는 서버의 Environment.TickCount 기준 입니다.

double PhotonNetwork.time : Photon 네트워크 시간, 서버와 동기화 됨

static void PhotonNetwork.FetchServerTimestamp	: 서버 타임 스탬프를 갱신 합니다





# RaiseEvent
            //public static bool RaiseEvent(byte eventCode, object eventContent, bool sendReliable, RaiseEventOptions options)

        // ref: http://doc-api.photonengine.com/en/pun/current/class_photon_network.html
        // RaiseEvent - OpRaiseEvent - OpCustom((byte) OperationCode.RaiseEvent
        //    this.opParameters.Clear(); // re-used private variable to avoid many new Dictionary() calls (garbage collection)
        //    this.opParameters[(byte)ParameterCode.Code] = (byte) eventCode;
        //    this.opParameters[(byte)ParameterCode.Data] = customEventContent;
        // opcustom

        // ref: https://doc.photonengine.com/en-us/pun/current/reference/photon-lag-simulation-gui
        // ref: https://doc.photonengine.com/en-us/pun/current/reference/photon-stats-gui

        // ref: http://forum.photonengine.com/discussion/6881/ipuncallbacks-doesnt-work-every-time
        // ref: http://forum.photonengine.com/discussion/956/which-one-i-should-use-opcustom-or-opraise

        // ref: PhotonWire - Photon Server + Unityによる型付き非同期RPCフレームワーク - http://neue.cc/2016/05/31_531.html
        // ref: https://doc.photonengine.com/en-us/onpremise/current/reference/calling-operations

