# Taxi-allocation
该项目利用面向对象编程，实现出租车的调配系统
1.输入格式 
没有测试线程 直接输入
A.请求格式样例为：[CR,(50,50),(77,77)];[CR,(1,6),(2,3)]
  每一行中请求之间用分号分割，同一行的请求取一个系统时间
  一行中有一个不符合格式的输入，其他的请求还可以正常相应。
B.寻求某个出租车的状态样例为：[TAXI,1] //数字从1开始编号
C:寻找处于制定状态的出租车对象: [STATE,2] //数字为 0（停止） 1（服务） 2（等待） 3（绿）
D:改变道路状态：[OPEN,(1,1),DOWN] 或者 [CLOSE,(0,0),DOWN] , open close表示要执行的动作，down up right left 表示要关闭的是所输入点的左边的上||下||左||右的道路，如果open操作的路已经开通了则会提示 already open ；close同理/; 同时改变多条线路要求一行输入，分号分隔。
（所谓的接口就是直接在控制台输入B 、 C就可以查询）
可预见输入格式报错形式：
  目的地和出发地相同:CR,50,50,50,50
  坐标不在地图内:CR,50,50,50,80
  输入格式不对:[CRR,(50,50),(30,50)]
注意 本程序不支持直接粘贴多行，只可以一行一行输入，每行中可以有很多请求（时间取相同）回车即开始处理

2.输出格式
当有一条有效请求时，程序会将相关信息输入到相应的工程目录下，文件名字时请求发出时的坐标。
主要包括信息在请求发出时刻，4*4内的出租车状态（没有则不输出）
抢单窗口结束时，抢单的出租车及其信息
系统选择的出租车及其接下来的过程中运行路线。
无出租车响应时直接控制台输出，不会输出到文件中
在出租车到达目的地之后才会一起输出实际运行路径
3.注
   由于GUI的问题，有的时候一行指令过多时会莫名显示“地图不联通”而终止程序，请多试几次。
   Map目前路径是 D:\\map.txt, 如果想改动可以在testTaxi中改
   LIghts目前的路径是D:\\light.txt, 同学发给你的是一个完全相通的图。
   
   对于可追踪出租车的双向迭代器，目前调用方式是在Request线程中。在每有一个可追踪的出租车执行完任务并到达目的地时，程序会更新输出一遍所有拉过乘客的可追踪出租车的情况，包括，从程序启动，该车抢到的乘客请求个数，每一个请求的请求，产生时刻，发出位置，目的地位置，出租车抢到单时的位置，运行路径。
    出租车目前的ID 1-30号为可追踪的31-100号为不可追踪的出租车，测试车可以在init_taxi（testTaxi.java)中自行改动。
论述NewTaxi符合JSP原则：
JSP原则：本程序只要父类能出现的地方，子类就可以出现，并且替换为子类也不会产生任何错误或异常。

