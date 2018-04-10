multiplayer sync

# ref
멀티플레이 게임의 동기화 기법 시리즈 2편: 이벤트 동기화
https://m.blog.naver.com/linegamedev/221061964789
Starcraft 네트웍 동기화 질문입니다.
http://www.gpgstudy.com/forum/viewtopic.php?f=18&t=4900&sid=f3a8056af53f5f425e5eb093232ab564


# 1. Conservative Algorithms
Lockstep Synchronization
http://www.gpgstudy.com/forum/viewtopic.php?f=18&t=4900&sid=f3a8056af53f5f425e5eb093232ab564

# 2.  Optimistic Algorithm
Time Warp Synchronization
모든 이벤트들에 대해 게임의 snapshot을 저장하는

# 3. Trailing State Synchronization
즉, 각각의 이벤트에 대한 snapshot을 저장하는 것이 아니라, 몇 가지 delay로 게임의 복사본을 운영하는 것입니다.


# 4. Dead Reckoning
추측항법
