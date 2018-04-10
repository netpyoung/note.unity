UNET
=====

# unet
p2p replay


Unite 2016 - Building Multiplayer Games with Unity
https://www.youtube.com/watch?v=-_0TtPY5LCc

Unite Europe 2017 - Photon vs UNet: multiplayer architecture explained
https://www.youtube.com/watch?v=Y1my5bKhKJY

Unite Europe 2017 - How Unity Multiplayer works
https://www.youtube.com/watch?v=V8539HYNuz8



High Level API
Low Level API

# UNET
Transport / Configuration
Connection / Reader / Writer
NetworkClient / NetworkServer
NetowrkIdentity / NetworkBehaviour
NetworkScene / ClientScene
NetworkManager
NetworkLobbyManager
NetworkTransform/NetworkAnimator/NetworkProximityChecker

# HLAPI
Simple Multiplayer Game
https://www.youtube.com/playlist?list=PLwyZdDTyvucw5JhBMJxFwsYc1EbQYxr0G
[Server]

class A : NetworkBehaviour
[Command]
NetworkServer.Spawn(go);

[SyncVar(hook="OnChangeHealth")]
public int currentHealth;

void OnChangeHealth(int health) {
}

[ClientRpc]
void RpcRewpawn() {
}

차이점? Command, ClientRpc
https://docs.unity3d.com/Manual/UNetActions.html

시나리오
클라이언트에서 Command를 사용하여 Server의 SyncVar를 갱신
서버는 SyncVar hook을 이용하여 클라에 hook호출
 hook되어 반환된 값을 이용하여 위치이동

[Command] runs the function on the server using data on the client.
[ClientRpc] runs the function on all clients using data from the server.



# LLAPI
