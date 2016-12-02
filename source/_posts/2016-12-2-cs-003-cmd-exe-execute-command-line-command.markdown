---
layout: post
title: "C# 003 C#调用cmd.exe执行命令"
date: 2016-12-2 07:57:03 +0800
comments: true
sharing: true
categories: [C#]
tags: [C#, CMD, 命令行, 参数, args]
---


---

* 我使用的电脑：Windows 10 64位
* 使用的Visual Studio 软件： VS2010

---

参考网站：[C#程序调用cmd.exe执行命令](http://www.cnblogs.com/njl041x/p/3881550.html)

创建一个文件，名为：`RunCmd.cs`。将下面的代码拷贝到里面。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Diagnostics;

namespace AoboSir
{
    class RunCmd
    {
        public RunCmd()
        {

        }

        private static string CmdPath = @"C:\Windows\System32\cmd.exe";

        /// <summary>
        /// 执行cmd命令
        /// 多命令请使用批处理命令连接符：
        /// <![CDATA[
        /// &:同时执行两个命令
        /// |:将上一个命令的输出,作为下一个命令的输入
        /// &&：当&&前的命令成功时,才执行&&后的命令
        /// ||：当||前的命令失败时,才执行||后的命令]]>
        /// 其他请百度
        /// </summary>
        /// <param name="cmd"></param>
        /// <param name="output"></param>
        public void run(string cmd, out string output)
        {
            cmd = cmd.Trim().TrimEnd('&') + "&exit";//说明：不管命令是否成功均执行exit命令，否则当调用ReadToEnd()方法时，会处于假死状态
            using (Process p = new Process())
            {
                p.StartInfo.FileName = CmdPath;
                p.StartInfo.UseShellExecute = false;        //是否使用操作系统shell启动
                p.StartInfo.RedirectStandardInput = true;   //接受来自调用程序的输入信息
                p.StartInfo.RedirectStandardOutput = true;  //由调用程序获取输出信息
                p.StartInfo.RedirectStandardError = true;   //重定向标准错误输出
                p.StartInfo.CreateNoWindow = true;          //不显示程序窗口
                p.Start();//启动程序

                //向cmd窗口写入命令
                p.StandardInput.WriteLine(cmd);
                p.StandardInput.AutoFlush = true;
                //p.StandardInput.WriteLine("exit");
                //向标准输入写入要执行的命令。这里使用&是批处理命令的符号，表示前面一个命令不管是否执行成功都执行后面(exit)命令，如果不执行exit命令，后面调用ReadToEnd()方法会假死
                //同类的符号还有&&和||前者表示必须前一个命令执行成功才会执行后面的命令，后者表示必须前一个命令执行失败才会执行后面的命令

                //获取cmd窗口的输出信息
                output = p.StandardOutput.ReadToEnd();
                p.WaitForExit();//等待程序执行完退出进程
                p.Close();
            }
        }
    }
}
```

我们可以这样使用这个`RunCmd` 类：

在GUI界面里面添加一个按钮，然后在对应的`.cs` 文件的程序，就类似于下面这个样子：

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using AoboSir;

namespace learningcs003
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        RunCmd runcmd = new RunCmd();

        private void button1_Click(object sender, EventArgs e)
        {
            string commond, output;
            commond = @"notepad.exe";
            runcmd.run(commond, out output);
            //MessageBox.Show(output);
        }
    }
}
```

运行的功能是：启动 **记事本** 软件。


----------
