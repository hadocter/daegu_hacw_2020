# <strong>머신러닝</strong> - 게임플레이 봇 만들기

## 1. 게임 선정
<ul>
<li>게임의 목표와 끝나는 시점(gameover)이 명확할것</li>
<li>만들어진 모델을 평가할 구체적인 기준이 있을것<dd><small>*게임 내의 점수 등</small></dd></li>
<big>선택한 게임</big>

<li>Tetris</li><br><img src="https://thumbs.gfycat.com/DecisiveSafeHorsemouse-size_restricted.gif">
<ul><li>조작이 간편함-left, right, drop, rotate</li><li>gameover=조각이 천장에 닿을경우</li><li>score=<a href="https://tetris.wiki/Scoring">테트리스 스코어 시스템</a></li></ul>
</ul>
</ul>

## 2.탐구 목표
<ul>
<li>테트리스의 점수부여:<br>
<table border = "1">
<tbody>
<tr><td>동시에 없애는 줄</td><td>1 개</td><td>2 개</td><td>3 개</td><td>4 개</td></tr>
<tr><td align="center">점수</td><td>40*(레벨+1)</td><td>100*(레벨+1)</td><td>300*(레벨+1)</td><td>1200*(레벨+1)</td></tr>
</tbody>
</table>

위에서 보듯이 1개의 줄을 4번 없애는것 보다, 4개의 줄을 한번에 없애는것이 훨씬 점수효율이 좋은것을 알수있다.<br>
따라서 학습시킨 모델이 과연 4개의 줄을 한번에 없애는 전략을 사용할지, 아니면 순간의 이익을 보고 한줄씩을 없앨지, 또한 4개의 줄을 한번에 없애는 전략을 사용하게 하려면 어떻게 해야할지(discount factor 값 등) 를 탐구한다.<br>
또한 이 방법으로 기존 테트리스 인간 신기록을 깰수 있을지, 또한 시간, 점수는 얼마나 차이나는지를 탐구한다.
</li>
<li>기존 인간이 사용하던 전략과 어떤점이 다르고 같은지 탐구한다</li>
</ul>

## 3.방법
<ul>
<li>게임 플레이 화면의 화면을 직접 받아 들이거나(grey-scale로 변환, 다운샘플링) 또는 직접 게임을 구현하거나 만들어진것의 코드를 수정해 좌표 정보를 배열로 받아들임</li>

</ul>

## 4.머신러닝 방법 선정
<ul>
<li><i><strong>Case1</strong></i>: 머신러닝 알고리즘(DQN, NEAT 등)에 대한 엄청난 조사를 해보고 적합할거 같은것을 실행함</li>
<li><i><strong>Case2</strong></i>: 여러 머신러닝 알고리즘을 테트리스 한 게임에 적용해보고 어떤 알고리즘이 테트리스에 가장 잘맞을지, 이유는 뭔지 탐구한다. 또한 다른 고전 게임에 알고리즘을 적용시켰을때 비슷한 결과가 나오는지 보고 어떤형태의 게임과 알고리즘이 잘맞을지 탐구해보고 유추해낸 이유와 함께 정리. <ul><li><small>→ 후에 보고서 작성시 적을 내용이 풍부하지만, <strong>시간과 난이도</strong>가 상당할것. 따라서 이부분은 <i><strong>Case1</strong></i> 을 먼저 실행해보고 시간적 여유가 있을시 진행하는것이 좋다고 생각함.</small></li><li><small>→<i><strong>Case2</strong></i> 진행시엔 팀을 두개로 나누어서 하는것이 좋다고 생각함.</small></li></ul></li>
</ul>

## 5.머신러닝 알고리즘 선정
<ul>
  <li>머신 러닝 알고리즘의 종류가 방대하고, 알고리즘 선정 과정에서 많은 것을 배울 수 있으므로 알고리즘의 선정은 같이 의논하는 방향이 좋다고 생각한다.</li>
  <li>알고리즘 선정의 예)</li>
  <ul>
  <dd>
    <li>Deep neural network</li>
      <li>
      → 간단한 네트워크는 Keras 등의 소프트웨어를 통해 비교적 간단히 구현이 가능하고, 또한 데이터를 더 많이 주거나 다른방법으로 주고, 알고리즘을 바꾸며 여러 방면의 최적화가 가능하다.
      </li>
  </dd>
  </ul>
</ul>
   
## 6.게임에 표시되는 정보의 입력 방법
<ul>
    <li>
        딥러닝 알고리즘에 정보 하나하나를 입력하는 경우 : <a href=https://github.com/benycze/python-tetris>https://github.com/benycze/python-tetris</a> 등의 오픈 소스 테트리스 프로그램에 정보를 알고리즘으로 넘겨주는 코드를 추가한다.
    </li>
    <li>
        딥러닝 알고리즘에 이미지 전체를 입력하는 경우 : 머신 러닝 알고리즘 중 Deep Q Network 등의 알고리즘은 화면 그대로를 입력받는다. 이럴 경우에는 OpenCV 등 라이브러리를 이용해서 이미지를 코드로 입력한다.
    </li>
</ul>
