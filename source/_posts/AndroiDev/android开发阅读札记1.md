---
title: android开发阅读札记1
categories:
  - AndroiDev
date: 2026-09-16 18:55:54
tags:
---
# 概述
书是Android Programming for Beginners, Fourth Edition  
由于一部分教材的草台，对于此类编成书籍的类似教材印象一直不好。但找来找去没有找到比较现代的android开发的文字教程，只能选择这本书来学  
可能是书比较啰嗦，也可能是洋文读起来膈应，推进速度提不起来  
这本书融合了一部分vibe coding，在当前大环境下似乎比较明智  
# 第一讲
配置android studio环境，没什么好说的。这里本人选择一个较老的软件版本，因为电脑太拉了  
跑自动生成的默认程序，不知道为什么我一直没跑起来，后面没办法换了一个比较新的软件版本，能跑了  
没有独显跑不动AVD，只能拿真机测试，还好无线调试比较方便  
创建项目的时候会下载并构建基本的gradle工具，挂着cf warp才勉强能进行  
# 第二讲
kotlin语法什么的也不会，跟着先学  
{% codeblock lang:kotlin %}
val x = 42
Log.d("Data output: ", "The value of x is $x")
{% endcodeblock %}
kotlin有点弱类型，但又不是完全弱。这里会根据右值自动推算类型，但有的时候又得写明白。同时val定义的像是常量  
Log.d有两个参数，第一个表明消息发出方，第二个是消息内容  
使用logcat需要android.util.Log。对于没有import的类和函数，在android studio用*alt+enter*自动导入  

{% codeblock 骨架 lang:kotlin %}
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
    }
}
{% endcodeblock %}
MainActivity.kt的主要部分，其中MainActivity类是入口，onCreate是LifeCycle中的一环，此外依次是onStart，onResume，onPause，onStop，onDestroy。应用启动会经历create,start和resume，退回桌面会触发pause和stop，回到应用界面会触发start和resume，销毁时即是pause,stop+destroy  
冒号表示继承，亦表示指定类型，两者也是一回事  
这时书给出了一个比较复杂的例子（至少看到这里的时候是这么认为的）来活跃气氛，并阐述现代android开发模式    
{% codeblock MainActivity.kt lang:kotlin %}
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            MaterialTheme {
                Scaffold(modifier = Modifier.fillMaxSize()) { innerPadding ->
                    EnterText(modifier = Modifier.padding(innerPadding))
                }
            }
        }
    }
}
@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
    Text(
        text = "Hello $name!",
        modifier = modifier
    )
}
@Preview(showBackground = true)
@Composable
fun GreetingPreview() {
    EnterNameDemoTheme {
        Greeting("Android")
    }
}
@Composable
fun EnterText(modifier: Modifier = Modifier) {
    var name by remember { mutableStateOf("") }
    Column(modifier = modifier.padding(16.dp)) {
        TextField(
            value = name,
            onValueChange = { name = it },
            label = { Text("Enter your name") },
            modifier = Modifier.fillMaxWidth()
        )
        Spacer(modifier = Modifier.height(16.dp))
        Greeting(name = name)
    }
}
{% endcodeblock %}
\@Composable用于告知编译器，下面的函数是jetpack compose的ui构建块，而非普通kotlin函数  
compose的又一个特性是state，用于持久化存储数据。本例中作用于name变量  
从本例来看，ui构建块指这样一个函数，里面调用了控件构造函数（和其他ui构建块）
涉及到xxxTheme，setContent字样的代码，语法看上去都很猎奇。这里是使用了lambda+神秘语法糖的结果。以下面的代码为例
{% codeblock 骨架 lang:kotlin %}
EnterNameDemoTheme {
    Greeting("Android")
}
{% endcodeblock %}
这里EnterNameDemoTheme表示一个函数，只接受一个参数，并且这个参数是个函数。kotlin中复杂变量作为右值要用花括号包住，同时若传入的参数只有一个并且是函数，可以去掉圆括号  

# 第三讲
var可读写变量 val只读变量 const（编译期）常量  
kotlin有类型推断，要推断long int要加L，推断float要加F  

# 第四讲
if else  
三元运算符：if(exp) v1 else v2  

> 26.9.25
这书讲的也太啰嗦，直接看android官网教程了  