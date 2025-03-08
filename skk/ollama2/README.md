# 在windows平台上部署DeepSeek本地版

[源码](https://github.com/lcctoor/pip/tree/main/skk/ollama2)

# 作者

许灿标

[主页](https://lcctoor.com/index.html) \| [Github](https://github.com/lcctoor) \| [微信](https://lcctoor.com/cdn/WeChatQRC.jpg) \| [邮箱](mailto:lcctoor@outlook.com) \| [捐赠](https://lcctoor.com/cdn/DonationQRC-0rmb.jpg)

# 安装

## 1、

进入 [https://ollama.com/download](https://ollama.com/download)，下载 ollama 的 windows 版本。

## 2、

安装 ollama ，然后启动 ollama（启动后，它会自动最小化到系统托盘）。

## 3、

在命令执行以下代码中的任意一行，注意：执行其中的任意一行就可以。

```
ollama run deepseek-r1:1.5b  # 无条件可以执行
ollama run deepseek-r1:7b  # 5G以下显存
ollama run deepseek-r1:14b  # 12G显存
ollama run deepseek-r1:32b  # 24G显存
ollama run deepseek-r1:70b  # 48G显存
ollama run deepseek-r1:671b  # 大于48G显存
```

由于笔者的电脑显存为8G，所以笔者执行的是 `ollama run deepseek-r1:7b`，后文教程都以 `deepseek-r1:7b` 为例子。

## 4、

在命令行执行：

```
pip install --upgrade git+https://github.com/lcctoor/pip.git@main
```

# 调用

## 创建对话

```python
from skk.ollama2 import Chat

Denny = Chat(model='deepseek-r1:7b')
```

## 对话

```python
answer = Denny.request('1的后继数是多少')

print(answer)  # >>> '1的后继数是2'
```

## 流式对话

```python
answer = Denny.stream_request('再往后是多少')

for x in answer:
    print(x, end='', flush=True)

再
往
后
是
3
。
```
