uframe
======

공식사이트 : http://invertgamestudios.com/
에셋스토어 : https://www.assetstore.unity3d.com/en/#!/content/14381
메뉴얼 : http://invertgamestudios.com/uFrameAPI/Default/webframe.html#uFrame%201.5%20Overview.html


SAVE HOURS! START USING UFRAME TODAY!


마이크로 프레임워크(micro framwork)를 선호하는데, 이건 좀 프레임워크 크기가 좀 큰듯.

음 일단 프레임워크 배우는데 걸리는 시간이 쫌 되는듯..

* [UniRx](https://github.com/neuecc/UniRx)를 가져다 쓴거 보면, reactive programming을 알 정도의 생각있는 넘이 만든 것 같음.. 막상 까보면 어떨까?

오... 보면 볼수록 괜찮다는 생각이..
rx를 어떻게 자연스럽게 녹아들게 했을까 했는데, 오 좀 쩌는듯?


예제 : https://github.com/InvertGames/uFrameExamples



http://cruwelcodes.blogspot.kr/2014/11/mvvm-unity3d.html


다이어그램으로 프로젝트를 시각화 시킬 수 있다는 점에서는 상당히 긍정적으로 바라보지만, 웬지 그 대가로 얻는 제약이 너무나도 클 것 같다.

최악의 경우, 만약 uFramework 문제로, Designer가 꼬이다가 터저버리는 경우에는 어떻게 대처할 것인가?

디자이너에서 파일 생성하고, 합치는 과정에 있어서, 여러사람이 머지하는 경우가 생길것도 같은데 이 부분은?
- 이거 프로젝트 graph 파일이 바이너리여서, 이거 구조 잡을때는 작업 스탑 후, 브랜치 까는 방식으로 가야할듯?




## MVVM
* M(Model) :
* V(View) :
* VM(ViewModel) :
* Control :


# test
Window => uFrame Designer

Create Project

Create SceneManager

scenemanager 우클릭 후, Scene 생성.


Create Systems

Save & Compile


# 프로젝트 구조
TestProject/
  _DesignerFiles/
    - 시각화 도구를 돕기위한 파일들 여기 들어감.(property들이 이쪽에 몰아져 있음.)

  SceneManagers/
    - Project View에서, SceneManager 를 생성하면 이쪽으로 떨어짐.
      - TestProjectSceneManager.cs
      - TestProjectSceneManagerSettings.cs

  Scenes/
    - Project View에서, SceneManager 선택후, `.scene`을 생성하면 이쪽으로 떨어짐.
      - TestProjectSceneManager.scene

  Controllers/
    - Project View에서, System을 생성후, 내부적으로 element를 생성하면 이쪽으로 떨어짐.
      - ElementController.cs

  ViewModels/
    - Project View에서, System을 생성후, 내부적으로 element를 생성하면 이쪽으로 떨어짐.
      - ElementViewModel.cs

  Views/
    - Element에서, Add View를 행하면, 이쪽으로 떨어짐.


uframe
======

fuck 프레임워크가 너무 크다.


ms WPF - MVVM


View model
single source of trueth

게임 로직 - 비주얼 로직을 이어줌

A Controller
엘리멘트에 대한 command 정의를 구룹핑함.

A series of Views
game-object에 붙어있는 Unithy component
ViewModel의 data에 binds되어있으며, commands를 호출함.


# reactive views

Views are standard unity componets
game-object에 붙어있는
single responsibility
자신의 data를 변화시키는 것보다, 데이터 변화에 react한다.
Views can share the same instance of a View-Model removing the requirement to other compoents for data access.



==============


# Subsystem





# Scene Manager
씬 전환하는것만 알면 될듯?
GetToLevelScenes

uframe Loading.scene을 추가시켜주긴 해야함.

ToLevelTransitionComplete


System.Collections.IEnumerator Load(UpdateProgressDelegate progress)






# View Model
MVVM

로직과 데이터를 나눔.

properties : P<String>
collections : ModelCollection<String>
commands : CommandWithSender<MyElementViewModel>






# Controllers
Controllers - Commands

Origin | V - VM - M
uframe | Controller



TurretViewModel turret = null;
this.ExecuteCommand(turret.kill);







# Views
데이터 표현 - VM과 소통.


View - ViewComponent










# Scene properties
 
 Element.propertie => view
 
 
 Bind.Property(Triangle.Target.property, p ==> {
	blabla
 }).DisposeWhenChanged(Triangle.TargetProperty);
 
 
 GetAvataPositionObservable
 








# Bindings
프로퍼티 변화에 대한 binding을 걸기





# Reactive State Machine






# computed properties

property들의 변화를 모아 하나의 프로퍼티를 만듬.




# inheritance - ??????????

ElementBController : ElementBControllerBase

ElementBViewModelBase : ElementAViewModel

===========


# Targeting System


## 결론
시도는 좋았으나, 마이크로 프레임워크가 아니라 유지보수하느데 문제 있을것같음.