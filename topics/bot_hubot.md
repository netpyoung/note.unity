## hubot

* [open source](https://github.com/github/hubot)
* written in [CoffeeScript](http://coffeescript.org/)
* on [Node.js](https://nodejs.org/)


https://github.com/slackhq/hubot-slack

## Chat ops

* [So, What is ChatOps? And How do I Get Started?](https://www.pagerduty.com/blog/what-is-chatops/?utm_content=buffer7f787&utm_medium=social&utm_source=linkedin.com&utm_campaign=buffer)
 - ChatOps란, conversation-driven 개발에 관한것.
 - 개발 tool을, conversation으로 옮기게 됨으로써, 팀이 일을을 자동으로, 협력하여, 싸고 빠르게 할 수 있게 만들어 준다.

* [Youtube - ChatOps at GitHub - Jesse Newland](https://www.youtube.com/watch?v=NST3u-GjjFw)
* https://speakerdeck.com/jnewland/chatops-at-github
* http://githubengineering.com/deploying-branches-to-github-com/



## bot 프로그램들
* hubot: https://hubot.github.com/
 - coffeescript로 작성.
* lita: https://www.lita.io/
 - ruby로 작성. skype adapter가 아직 없음. (만들까 했는데, 이건 나중에)
* errbot: http://errbot.net/
 -  python으로 작성. 업데이트가 더딘감이있음.
* sevabot: https://sevabot-skype-bot.readthedocs.org/en/latest/
 - python으로 작성. skype에 특화.

 

### hubot - Pros
* (그나마) 믿을 수 있는 github의 프로젝트.
* 어쩔 수 없이, node.js위에 돌아간다고 하더라도, javascript를 쓰지않고, coffeescript를 쓴점.
* adapter로 추상화를 해놔서, 챗팅프로그램이 변경되더라도 (비교적) 간단하게 교체가능.
 - ms가 skype desktop api 지원을 안하겠다고해서, 기존 sevabot과 같은 skype종속적인 bot들의 호환성이 걱정됨.
 - http://blogs.skype.com/2013/11/06/feature-evolution-and-support-for-the-skype-desktop-api/



### hubot - Cons
* 아직은 부실한 api 문서.



## 구조

```
bin/
    : 휴봇 실행파일 위치.
node_modules/
    : pacakge.json을 이용하여 설치된 패키지들이 있는 폴더
scripts/
    : 사용자 정의 스크립트 파일 위치(.coffee, .js)
Procfile
    : 
README.md
    : 
package.json
    : npm을 사용하여 설치할 패키지선언 파일.
hubot-scripts.json
    : npm의 `hubot-scripts`에 실려있는, community script들을 선언하는 파일
external-scripts.json 
    : 추가로 로드할 npm 패키지들.
```




## 설치
* 공식 사이트에서 nodejs다운로드(skype4py 호환성을 위해 32bit)
* git설치 윈도우즈 : https://msysgit.github.io/
* 커피스크립트 설치

    npm install -g coffee-script

* hubot 설정

    % npm install -g yo generator-hubot
    % mkdir hubot
    % cd hubot
    % yo hubot

* skype adapter를 위한 기본 셋팅
    python 2 - 32bit 설치
    pip install skype4py

* hubot 실행

    % bin/hubot


## etc
한국어 regexp : [가-힇ㄱ-ㅎㅏ-ㅣ]



## ref

* [coffeescript-cookbook](https://coffeescript-cookbook.github.io/)
* [regexr v2.0](http://regexr.com)