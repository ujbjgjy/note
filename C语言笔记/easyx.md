1. 创建窗口

   ```c
   initgraph(width,height);
   //init:初始化		graph:图形界面
   //width:宽
   //height:高
   ```

2. 刷新

   ~~~c
   cleardevice();//clear:清除	device:设备
   //当你不想要不当前界面的东西时，可以用这个函数来清除当
   //前
   ~~~

3. 颜色

   ~~~c
   RGB(0,0,0);
   ~~~

4. Music(音频)

   > **头文件**
   >
   > mmsystem.h		mm：多媒体		system:系统
   >
   > **库文件**
   >
   > winmm.lib			win：windows系统		mm：多媒体
   >
   > **stdio.h(标准输入输出)**
   >
   > std：standard-标准
   >
   > i：input-输入
   >
   > o: output-输出

   **包含库文件**

   `#pragma comment(lib,"winmm.lib")`

    **mciSendString**

   mci: media control interface=>媒体控制接口

   sendstring: 发送字符串

   ~~~c
   mciSendsting(L"open 音乐名",0,0,0);
   //打开
   mciSendsting(L"play 音乐名",0,0,0);
   //播放
   mciSendsting(L"pause 音乐名",0,0,0);
   //暂停
   mciSendsting(L"close 音乐名",0,0,0);
   //关闭
   
   //L 表示我使用的是个宽字节
   ~~~

5. 文字

   ~~~c
   settextcolor(WHITE);//白色
   //set：设置	text：文字		color:颜色
   setbkmode(TRANSPARENT);
   //去除文字背景 TRANSPARENT
   settextstyle(100,0,"字体样式");
   //style:风格
   //100:字体高度	0:字体宽度，如是写0自适应宽度 
   outtextxy(x,y,"字符串");
   //out:输出	text:文字		xy:坐标
   ~~~

6. 图片处理

   ~~~c
   IMAGE img;
   //定义一个图片变量
   loadimage(&img,"图名"，800，600);//
   //加载一张图片放到img变量中
   putimage(0,0,&img);
   //输出图片
   ~~~

7. 批量绘图

   ~~~c
   BeginBatchDraw();
   //Begin：开始 Batch:批量	Draw:绘图
   //开始将图片绘制到缓冲区
   EndBatchDraw();
   //End:结束
   //结束缓冲区的绘制，将完整一帧图像输出到窗口中
   ~~~

8. 透明图片

   * 准备两张图片

     黑底白面图，白底彩面图

   ~~~c
   //黑底白面图
   //SRCPAINT |
   putimage(0,0,&img,SRCPAINT);//清除黑色，显示白色
   //黑色二制为0，白色为1
   
   
   //白底彩面图
   //SRCAND   &
   putimage(0,0,&img,SRCAND);
   ~~~

   **原理**

   彩底：	1010 彩面：1010

   按位或		    	|

   黑底：	0000 白面：1111

   得出：	1010 			1111

   > 消出黑底，白面覆盖

   彩底：1010 白面：1111

   按位与			&

   白底：1111 彩面：1010

   得出：1010 			1010

8. kbhit()

   **判断是否存在在按建**



























