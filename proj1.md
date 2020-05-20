# <strong>머신러닝</strong> - 게임플레이 봇 만들기

## 1. 게임 선정
<ul>
<li>게임의 목표와 끝나는 시점(gameover)이 명확할것</li>
<li>만들어진 모델을 평가할 구체적인 기준이 있을것<dd><small>*게임 내의 점수 등</small></dd></li>
<big>적합하다고 생각하는 게임들-</big>
<ul>
<li>Snake<br><img src="https://thumbs.gfycat.com/WildSharpFlyingfish-size_restricted.gif"><br><ul><li>조작이 간편함 - up, down, left, right</li><li>gameover = 자신의 몸에 닫거나 벽에 닿은경우로 명확함</li><li>score = 먹은 점의 갯수로 정해져 있음</li></ul></li>
<li>Flappy bird<br><img src="https://thumbs.gfycat.com/PlayfulFrigidAnchovy-size_restricted.gif"><br><ul><li>조작이 간편함 - jump</li><li>gameover = 기둥에 닿거나 바닥에 닿은 경우로 명확함</li><li>score = 지난 기둥의 갯수로 정해져있음</li></ul></li>
<li>Tetris</li><br><img src="https://thumbs.gfycat.com/DecisiveSafeHorsemouse-size_restricted.gif">
<ul><li>조작이 간편함-left, right, drop, rotate</li><li>gameover=조각이 천장에 닿을경우로 명확함</li><li>score=<a href="https://www.codewars.com/kata/5da9af1142d7910001815d32">테트리스 스코어 시스템</a></li></ul>
</ul>
</ul>
