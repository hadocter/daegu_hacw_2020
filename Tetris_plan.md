# <strong>머신러닝</strong> - 게임플레이 봇 만들기
<!--Animeloverhachangwoo-->

## 1. 게임 선정
<ul>
<li>게임의 목표와 끝나는 시점(gameover)이 명확할것</li>
<li>만들어진 모델을 평가할 구체적인 기준이 있을것<dd><small>*게임 내의 점수 등</small></dd></li>
<big>선택한 게임</big>

<li>Tetris</li><br><a href="https://youtu.be/dQw4w9WgXcQ"><img src="https://thumbs.gfycat.com/DecisiveSafeHorsemouse-size_restricted.gif"></a>
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
        <dd>
            <li>
            간단한 네트워크는 Keras 등의 소프트웨어를 통해 비교적 간단히 구현이 가능하고, 또한 데이터를 더 많이 주거나 다른방법으로 주고, 알고리즘을 바꾸며 여러 방면의 최적화가 가능하다.
            </li>
        </dd>
  </dd>
  </ul>
</ul>
  
## 6.게임에 표시되는 정보의 입력 방법
<ul>
    <li>
        딥러닝 알고리즘에 정보 하나하나를 입력하는 경우 : <a href=https://github.com/benycze/python-tetris>https://github.com/benycze/python-tetris</a> 등의 오픈 소스 테트리스 프로그램에 정보를 알고리즘으로 넘겨주는 코드를 추가한다.
    </li>
    <li>
        딥러닝 알고리즘에 이미지 전체를 입력하는 경우 : 이럴 경우에는 OpenCV 등의라이브러리를 이용해서 이미지를 코드로 입력한다.
    </li>
</ul>

## 7.코드 공유 및 실행
<ul>
    <li>
        클라우드 pc 서비스를 이용해 ssh로 접속하고 편집기로 서버에 <a href=https://github.com/cdr/code-server>CODE-SERVER</a> 을 올려서 편집하는 방식 또는 준비된 데스크탑 환경에 우분투 서버의 안정된 버전(18버전 추천)을 설치한뒤 똑같이 ssh로 접속하고 편집기로 서버에 <a href=https://github.com/cdr/code-server>CODE-SERVER</a> 을 올려서 편집하는 방식(이 경우에는 보안을 위해 방화벽에서 22번 포트만 활성화 하는 방식을 추천).
    </li>
</ul>

## 8.역할 분담
<ul>
    <li>
        되도록 모두 머신러닝에 대한 많은것을 배워 모두 같이 구현했으면 좋겠으며, 또한 구현부분도 모두 한자리에 앉아 의논하며 만들면 좋겠음.
    </li>
</ul>

## 9.과정
<ul>
  <li>
    아직 모두 머신러닝에 대한 세부한 부분의 지식과 실습경험이 엄청 부족하므로, 일단 간단한(상대적으로) Cart-Pole 문제나 mnist dataset 에서 제공하는 숫자인식 등을 모두 이해하고 실습하고 변경해보는 과정을 통해 비교적 익숙해지고 난 후에 상세한 Tetris plan의 계획을 짜는쪽이 좋을것 같다.
    DQN 등 일부 게임에 크게 효과있는 알고리즘은 논문상으로 제시되어 있으므로 바로 구현하기에는 아직 어려움이 클거 같다.
    <br>따라서 앞으로의 문제 해결 과정에서 필요하다고 생각하는 것을 나열해 보았습니다.
    <ul>
      <li>Cart-Pole, MNIST 데이터셋으로 숫자인식등 머신러닝으로 해결할수 있는 비교적 간단한 문제를 해결하여, 그 과정과 코드, 또한 코드의 특정부분을 수정하면서 변경된 결과들을 발표하고 의논하면 좋겠습니다.</li>
      <li>머신러닝등 큰양의 다차원 데이터를 다루거나, 벡터연산등이 필수적인 분야에서 약방에 감초같은 존재인 NUMPY라는 라이브러리가 있습니다. 하지만 실제 NUMPY를 사용한 코드를 보면 약간 난해하거나 햇갈리는 부분이 꽤 있었습니다. 따라서 큰 목표를 위해 NUMPY와 데이터형, 벡터에 대한 학습은 꽤 유용할 것이라고 생각합니다.</li>
      <li>어느정도 다룰 수 있을 정도의 이해가 된뒤, 이미 입력방법과 목표등은 설정해놓았으므로 그떄는 구체적인 알고리즘의 설정과, 실험을 반복할수 있다고 생각합니다.</li>
    </ul>  
    
    
  </li>
</ul>

## 자료
제가 공부하면서 찾은 유용하다고 생각되는 자료들입니다.
<ul>
  <li><a href="https://tensorflow.blog/%ec%bc%80%eb%9d%bc%ec%8a%a4-%eb%94%a5%eb%9f%ac%eb%8b%9d/">https://tensorflow.blog/%ec%bc%80%eb%9d%bc%ec%8a%a4-%eb%94%a5%eb%9f%ac%eb%8b%9d/</a> 얼마전에 찾은 케라스 라이브러리의 쉬운 가이드입니다.</li>
  <li><a href="https://www.youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi">https://www.youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi</a> 인공신경망의 개념과 작동방식에 관해 쉽게 잘 설명한 영상입니다.</li>
  <li><a href="https://www.youtube.com/watch?v=fNk_zzaMoSs&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab">https://www.youtube.com/watch?v=fNk_zzaMoSs&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab</a>벡터를 개념만이라도 공부하는것이 나을것이라 판단해 시청했던 동영상입니다.</li>
</ul>  
