https://jacksondunstan.com/articles/3349



https://github.com/SnpM/LockstepFramework




# class GameManager
              void Awake()
              {
                     NetworkHelper networkHelper = gameObject.GetComponent<NetworkHelper>();
                     if (networkHelper == null)
                           networkHelper = gameObject.AddComponent<DefaultNetworkHelper>();
                     //Currently deterministic but not guaranteed by Unity
                     // may be add as serialized Array as property?  [SerializeField] private BehaviourHelper[] helpers; ?
                     BehaviourHelper[] helpers = this.gameObject.GetComponentsInChildren<BehaviourHelper>();
                     LockstepManager.Initialize(helpers, networkHelper);
              }

              void FixedUpdate()
              {
                     LockstepManager.Simulate();
              }
              void Update()
              {
                     LockstepManager.Visualize();
              }
              void LateUpdate()
              {
                     LockstepManager.LateVisualize();
              }

              void OnDisable()
              {
                     LockstepManager.Deactivate();
              }
              void OnApplicationQuit()
              {
                     LockstepManager.Quit();
              }


# class LockstepManager
* Command executor
* LockStepManager.Execute(Command command)
    * distribute command and execute
* Simulate()
* CommandManager.Simulate ();
* AgentController.Execute(Command com)

void Simulate()
{
    InfluenceCount ???????
        FrameManager.Simulate

    FrameCount == 0
        GameStart() => BehaviourHelperManager.GameStart ();

    BehaviourHelperManager.Simulate ();
    AgentController.Simulate ();
    PhysicsManager.Simulate ();
    CoroutineManager.Simulate ();
    InfluenceManager.Simulate ();
    ProjectileManager.Simulate ();

    LateSimulate ();

    FrameCount++;
}

# class Frame
* container of `Command`

# class Command
* ContainedData  - Dictionary<ushort,FastList<ICommandData>>



# class FrameManager
* frame storage - resizable
* Simulate
    * frame.Commands { command =>  LockStepManager.Execute(command) }
* TweakFramerate () - modify Time.timescale - depends on ForeSight


# class CommandManager
* SendCommand - accumulate command
* SendOut - ClientManager.Distribute(bufferdBytes)
* ProcessPacket
    * make frame
    * make commands
    * frame.add(commands)
    * ProcessFrame(frame-count, frame)

# class ClientManager
* SimulateNetworking
* NetworkHelper - send / OnFrameData / OnInitData



# interface ILockstepEventHandler
       public interface ILockstepEventsHandler
       {
              ushort GetListenInput();
              void Initialize();
              void EarlyInitialize();
              void LateInitialize();
              void Simulate();
              void LateSimulate();
              void Visualize();
              void LateVisualize();
              void GlobalExecute(Command com);
              void RawExecute(Command com);
              void GameStart();
              void Deactivate();
       }
