#my little program  

1、原生js实现打地鼠游戏  

http://hunterfront.github.io/little-program/beatmole  

参考原型图：  

![](https://github.com/HunterFront/little-program/blob/master/images/game1.png)  

相关技术：HTML、CSS、JS  

项目需求：实现一个web页面的打地鼠游戏  

功能需求：  

	随机在界面中生成地鼠  

	击中地鼠的同时实现一定的交互效果（地鼠、锤子状态有变化）  

	记录分数、关卡，并计算命中率  

	实现游戏的开始、暂停和重新开始功能  

	游戏结束时，显示成绩  

页面事件：  

1.	点击开始按钮游戏开始，启动定时器  

2.	点击暂停游戏暂停，清除定时器  

3.	点击重新开始，刷新页面  

4.	点击提示框的确定键，隐藏modal框，回到游戏界面  

5.	点击游戏界面的格子，改变锤子的状态，记录点击次数，若击中分数＋1，计算命中率  

数据结构：{x:x,y:y,src:’…’};  

实现流程：  

1、	显示界面：游戏界面由一个table及里面的td构成，生成一个4*4的网格，网格的大小85px；  

2、	点击开始按钮，游戏开始，随机生成地鼠；	  

详细分析：每次产生的地鼠的数量随机[1,2,3]个，根据关卡难度分配个数产生的概率，关卡越难产生数量多的概率越大，产生的每个地鼠为其随机分配停留的时间，关卡越难分配的总时间越短，即每个地鼠分配的单个时间也会变短（每个地鼠分配的时间也按一定比率进行分配，达到参差不齐的效果）  

3、鼠标点击地鼠，点到则立即让地鼠进洞，分数加1，记录总点击次数并计算命中率；没有点到，记录总点击次数，计算命中率。  




2、原生js实现贪吃蛇游戏  

http://hunterfront.github.io/little-program/snake  

参考原型图：  
![](https://github.com/HunterFront/little-program/blob/master/images/game2.png)    

相关技术：HTML、CSS、JS  

项目需求：实现一个web页面纯js的贪吃蛇游戏。  

功能需求：  

	记录关卡（关卡每吃10个果实升一级）  

	记录得分（每一个果实的得分等于关卡值）  

	显示隐藏参考线  

	可以控制蛇的方向  

	可以开始/暂停，重新开始游戏游戏  

	游戏结束时弹出提示框  

页面事件：  

1、点击开始按钮：游戏第一次开始，蛇开始往左移动；游戏暂停后开始，蛇继续往暂停之前的方向移动  

2、点击暂停按钮：游戏暂停  

3、点击重新开始：刷新页面  

4、点击显示和隐藏参考线：显示隐藏单元格的边框  

5、上左下右按键按下，分别控制蛇的移动方向  

数据结构：基础数据结构：{x：x，y：y，bgColor：…};   

实现流程：  

1、	游戏界面的显示：  

	一个table，20*20网格（js动态生成tr、td）  

	关卡/关卡值（b、span）、得分/分值（b/span）  

	四个按钮：开始、暂停、重新开始、显示/隐藏参考线  

2、初始化游戏：  

	生成蛇的初始身体，为三个格子，蛇头{x：9，y：9，bgColor：yellow}，蛇身1{x：10，y：9，bgColor：red}，蛇身2{x：11，y：9，bgColor：red}；  

	随机生成0.8*边长格子数个果实{x：x，y：y，bgColor：blue}，果实位置不能与蛇的位置重叠；  

	初始移动方向左direction：3；（0上，1右，2下，3左）  

3、	点击开始按钮游戏开始，蛇开始移动，计算蛇头的下一个x，y，让其从开头进入蛇身（unshift），弹出（pop）蛇身的最后一个值，通过擦除和重绘模拟蛇的移动，蛇在移动的过程中会有四种状况：  

	蛇头撞墙，游戏结束（根据方向判断蛇头下一步的x或y大于格子边界）  

	蛇头咬到自己，游戏结束（根据方向判断蛇头的下一步达到的格子被蛇尾占据着）  

	吃到果实，蛇长+1（unshift），分数加1*关卡值（根据方向判断蛇头下一步有果实）  

	正常移动（unshif、pop）  

蛇的移动的具体分析：蛇每移动一步都是对前一状态的擦除，和新状态的重绘，蛇在运动的过程中首先判断下一步的状况，判断下一步位置要根据蛇运动的方向来判断。 




