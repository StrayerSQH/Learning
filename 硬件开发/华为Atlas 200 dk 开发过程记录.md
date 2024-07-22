# 华为Atlas 200 dk开发过程记录
## 一键制卡

## 环境搭建
### 安装Python3.7.5
安装Python软件。在终端中输入（注意大小写）：
```
wget https://www.python.org/ftp/python/3.7.5/Python-3.7.5.tgz
```
随后输入指令：
```
sudo apt-get install -y gcc g++ make cmake zlib1g zlib1g-dev libbz2-dev libsqlite3-dev libssl-dev libxslt1-dev libffi-dev unzip pciutils net-tools libncursesw5-dev
```
随后解压缩Python3.7.5的安装包
```
tar zxvf Python-3.7.5.tgz
```
紧接着进入Python-3.7.5目录内
```
cd Python-3.7.5
```
输入命令：
```
./configure --prefix=/usr/local/python3.7.5 --enable-loadable-sqlite-extensions --enable-shared
```
随后，输入命令充分调用CPU编译：
```
make -j8
```
接下来，输入指令：
```
sudo make install
```
到这里，PYthon的安装还没有结束（但是快了，剩下就是配一个环境）。<br>
随后在终端中输入以下命令，安装相应的Python文件：
```
sudo ln -s /usr/local/python3.7.5/bin/python3 /usr/local/python3.7.5/bin/python3.7.5
sudo ln -s /usr/local/python3.7.5/bin/pip3 /usr/local/python3.7.5/bin/pip3.7.5
```
完整后，再在终端中输入命令：
```
vi ~/.bashrc
```
随后滑动到最下面，将以下文本复制粘贴
```
#用于设置python3.7.5库文件路径
export LD_LIBRARY_PATH=/usr/local/python3.7.5/lib:$LD_LIBRARY_PATH
#如果用户环境存在多个python3版本,则指定使用python3.7.5版本
export PATH=/usr/local/python3.7.5/bin:$PATH
```
完成后，按`Esc + ： + w + q`键退出程序，随后输入命令：
```
source ~/.bashrc
```
完成后，查看当前环境中的Python版本：
```
python3.7.5 --version
```
应该能看到以下结果：<br>
![Python版本查看](https://github.com/StrayerSQH/stochastic-search/blob/main/%E5%85%B6%E4%BB%96%E6%94%AF%E6%8C%81%E6%9D%90%E6%96%99/%E5%8D%8E%E4%B8%BAAtlas%20200%20dk/Python%E7%89%88%E6%9C%AC%E6%9F%A5%E7%9C%8B.jpg)
随后运行`pip`指令查看：
```
pip3.7.5 --version
```
应该能看到以下结果：
![pip查看python版本](https://github.com/StrayerSQH/stochastic-search/blob/main/%E5%85%B6%E4%BB%96%E6%94%AF%E6%8C%81%E6%9D%90%E6%96%99/%E5%8D%8E%E4%B8%BAAtlas%20200%20dk/Pip%E6%9F%A5%E7%9C%8BPython%E7%89%88%E6%9C%AC.jpg)
到这里，Python包就安装好啦！！！
