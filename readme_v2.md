这是完整舞蹈的视频链接：[机器人协调控制系统舞蹈效果](https://www.bilibili.com/video/av65255435).
# 前言
受到波士顿机器狗跳舞的启发，我在协调控制系统中添加了节奏模式，并以此制作了这个舞蹈视频。

# 系统
1.	这一版，我针对之前大家提出的问题，进行了改进，基本解决了系统卡顿问题。另外，我改进了上一版的4足行走算法，进一步提高了控制精度和稳定性，使4足行走的同时精确控制双手或双翅成为可能，这在后半段视频重点展示。
2.	由于硬件算力限制，当前系统每秒平均完成4组指令的演算。为了应对指令生成速度起伏、个别功能不确定动作、以及快节奏需求，我暂时采用对视频非整数加速的方式，完成最后的节奏衔接，希望大家谅解。

# 关于本文
1.	本次视频展示的舞蹈效果，涉及的部分功能，已经在上一个视频和博客中给出，这一次对重复的功能不再赘述。
2.	这一次的详解，重点说明编排的舞蹈涉及的动作细节，以及4足协调运动实现了哪些效果。以展示当前的系统具有足够的协调和控制精度，来支持各种运动需求。

# 一. 后4足站定舞蹈部分
## 1. 螳螂拳
### 1) 蓄势
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190825132102386.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQxNjU1MA==,size_16,color_FFFFFF,t_70#pic_center)

身体沿着斜向小幅度画圆摇摆，同时抬起的双手以略微更大的半径，延迟45度相位角，晃动，产生蓄势感。
### 2) 出拳
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190825132239405.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQxNjU1MA==,size_16,color_FFFFFF,t_70#pic_center)

头部先看向目标，然后身体从最靠后位置突然前移，外侧手臂在延迟的一拍相位到位后，快速出拳。我希望这样动作，能使出拳有更强的拳意。
## 2. 太极
### 1) 云手
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190825132329301.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQxNjU1MA==,size_16,color_FFFFFF,t_70#pic_center)

上一版已经实现，具体参考上一篇详解。这一次，双手和头部的转动更加自然流畅。
### 2) 收势
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019082513241799.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQxNjU1MA==,size_16,color_FFFFFF,t_70#pic_center)

双手先在下方各自画出1/4个大圆，到达水平位置后，继续画1/2个小圆，直到归位。
# 二. 6足舞蹈部分
## 1. 平移
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190825132600774.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQxNjU1MA==,size_16,color_FFFFFF,t_70#pic_center)

上一版已经实现，具体参考上一篇详解。
## 2. 自动转向
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190825132627467.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQxNjU1MA==,size_16,color_FFFFFF,t_70#pic_center)

上一版已经实现，具体参考上一篇详解。
## 3. 精确踩点
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190825132707850.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQxNjU1MA==,size_16,color_FFFFFF,t_70#pic_center)

通过修改各足的最终期望姿势，协调系统，自动判断，哪些足还没有到位，然后自动跨步过去。
## 4. 拔河舞
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190825132742844.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQxNjU1MA==,size_16,color_FFFFFF,t_70#pic_center)

1)	倾斜身体角度，并且指定一个外力，使身体重心自动倾斜。保持一个拔河的受力平衡姿势。
2)	本实验设计目的，主要是最近机器人拉货功能比较火，我认为其中最大的技术难点，就是用姿势平衡受力。由于这个机器人没有传感器，我暂时采用指定外力的方法，以后可以考虑用传感器信号输入外力。
3)	这个实验的本质是加速度倾斜，这在我上一版的斜面运动中已经实现，具体参考上一篇详解。

# 三. 双手空间定点站定运动
## 1. 扭腰舞
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019082513294362.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQxNjU1MA==,size_16,color_FFFFFF,t_70#pic_center)

上一版已经实现，具体参考上一篇详解。这一次，我将扭动的角度进一步加大，扭动的连贯性也更好。
## 2. 螺旋舞
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190825133013660.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQxNjU1MA==,size_16,color_FFFFFF,t_70#pic_center)

身体中心沿着x-z平面做竖直圆周运动，同时，偏航角和俯仰角，也对应修改，使身体轴线始终与圆周所在柱面斜切，形成螺旋效果。

# 四. 4足行走舞蹈部分
四足行走是这一版改进的重点之一。相比上一版单调的左右重心偏移补偿，这一次，我重新设计算法，实现全向重心偏移补偿。这样一来4足的运动就能和6足一样，可以精确地转弯以及全向运动，而不用担心身体重心不稳，打破精确控制。同时，新算法形成的稳定余量，为运动过程挥动双手，提供了足够的重心和惯性鲁棒空间。
## 1. 前后4足行走
前后4足模式能够最大程度保留这个机器人的对称性，有利于平衡的理论计算，因此在尝试一些比较复杂的运动时，依然能够维持较高的坐标精度。

### 1) 后退飞走
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190825133414127.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQxNjU1MA==,size_16,color_FFFFFF,t_70#pic_center)

前后四足稳定行走的同时，快速挥动中间两足，形成振翅效果。振翅效果主要证明两种无关动作指令，可以同时进行，由系统自动融合。
### 2) 定点盘旋
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190825133526219.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQxNjU1MA==,size_16,color_FFFFFF,t_70#pic_center)

1. 将右翅（右中足）指定在空间某点悬空，左翅（左中足）在身体外侧中心对称位置。4足绕圈行走，使左翅沿着圆形轨迹滑动。整个过程保持身体滚转角倾斜不变，最终整体效果，仿佛飞鸟盘旋。
2.	这个动作挑战了波士顿动力的一个完整实验——4足行走过程中机械臂指定空间某一点不动。上一版由于4足平衡效果不好，只能尝试看点绕圈，这一次条件满足了，因此尝试完整实验。
### 3) 长颈龙摆尾
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190825133640482.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQxNjU1MA==,size_16,color_FFFFFF,t_70#pic_center)

1.	将左中足作为尾巴，右中足作为头部。身体沿着滚转角倾斜，以抬高头部，降低尾部。行走过程中，尾巴始终摆向抬腿的另一侧。
2.	这个动作模仿自然界的爬行动物，通过摇摆巨大的尾巴来平衡笨重身体的方法。另外头部运动，我模仿了鸡头在行走时定点突进的效果（我不确定这是不是长颈龙的运动特点，请大家不要介意）。
## 2. 后4足行走
由于后4足模式非常不对称，加上各足各段的重量未知（我不擅长硬件，不敢拆了称，怕装不回去，汗）。在没有电脑模拟条件的情况下，纯理论计算保持平衡能力有限。好在我的4足协调算法，预留了一定的稳定余量，允许双手小范围精确运动。
### 1) 咏春连环拳
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190825133738991.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQxNjU1MA==,size_16,color_FFFFFF,t_70#pic_center)

1.	后4足后退行走，同时双手不断前滚，并且两个前滚平面有一个倾角，以尽量让双拳打击点靠近中轴线（由于双手运动范围限制，我只做了近似效果）。
2.	这个动作模仿咏春拳的连环拳。一方面给出了后四足的前后运动效果，同时证明，在不打乱步伐稳定性的情况下，双手依然有较大的自由运动空间。

### 2) 定点冲拳
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190825133812139.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQxNjU1MA==,size_16,color_FFFFFF,t_70#pic_center)

1.	后4足站立模式下，身体逐步绕圈横移。双手根据音乐节奏变化，朝着空间某一个固定点，连续冲拳。
2.	这个动作，充分利用了我新增的节奏模式，使冲拳的时机与音乐所需节奏一致。
3.	另一方面这个动作，类似“定点盘旋”，这个动作从更难的角度，挑战了波士顿动力试验。只是这个非对称的4足姿势，会放大受力形变效果，变成一个向后运动的累积误差，所以最后的效果，冲拳的点位也有了较显著的后移。
# 五. 收尾拉弓pose
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190825133907312.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQxNjU1MA==,size_16,color_FFFFFF,t_70#pic_center)

先头部看向左前方目标，然后抬起双手到正前方，左右分开，左手伸直，右手收拢，仿佛拉弓效果。
# 六. 补充
1.	这一次，我取消了陀螺仪矫正功能，因此这是一个彻底的开环控制系统。这么做一方面为了节约算力，另一方面也想进一步展示这套协调控制系统的精确程度。整个舞蹈结束时，移动范围基本符合理论，没有撞墙，但角度误差大约45度，主要来自4足行走时形变打滑引入。
2.	除了行走模式转化以外，所有部分我实现了节奏踩点到位，由于动作生成的计算效率尚未彻底解决，估算出每秒平均对20个舵机修改4次已经是极限。也许因为计算依然存在速度起伏，最终的节奏，总会在0.8~1.2倍之间不定，因此虽然1倍的速度理论上应该踩点，我还是不得不进行微调，以达到我想要的效果。4足运动要在保证精确控制的同时，维持平衡，速度无法提高，加上一些快节奏的部分本来就超过每秒2拍（我设定了决策更新最小单位为2次指令执行，即0.5s），因此我主动编排了需要加速的舞蹈。
3.	这套协调控制系统的其他功能，可以参考我的上一个CSDN博客以及前一个B站视频，搜索用户名“生命浩瀚”可以找到。

在此衷心表达对大家的感谢，你们的支持和鼓励，让我有了继续研究下去的动力。

注：目前暂不公开
