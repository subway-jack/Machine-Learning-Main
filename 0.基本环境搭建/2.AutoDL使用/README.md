## audoDL常用命令
### 网络
1. 网络配置(使用gg设置代理)[gg-github网址](https://github.com/mzz2017/gg/blob/main/README_zh.md)
```
sudo sh -c "$(curl -L https://hubmirror.v2raya.org/raw/mzz2017/gg/main/release/go.sh)"
gg config -w subscription='自己的订阅链接'
gg bash # 代理整个命令终端
```
### git lfs使用

**GIT LFS简介:**（Large File Storage，解决git大文件存储问题）把音乐、图片、视频等指定的任意文件存在 Git 仓库之外，而在 Git 仓库中用一个占用空间 1KB 不到的文本指针来代替文件的存在,通过把大文件存储在 Git 仓库之外，可以减小 Git 仓库本身的体积，使克隆 Git 仓库的速度加快，也使得 Git 不会因为仓库中充满大文件而损失性能。

1. 安装Git Lfs
```
curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash
sudo apt-get install git-lfs
git lfs install
```

2. 下载HuggingFace文件

**(小文件、大文件)分开下载**
```
git lfs install #git 初始化
GIT_LFS_SKIP_SMUDGE=1 git clone https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.1.git #安装小文件
cd bloom-7b1                 #需要进入下载的文件夹中
git lfs pull --include="*.bin" # 继续下载 此时匹配 ".bin"文件
```
**(小文件、大文件)一起下载**
```
git lfs install
git lfs clone --progress https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.1.git
```
**下载中断用这个恢复**
```
git lfs fetch
```

**参考**
```
# 1. 安装完成后，首先先初始化；如果有反馈，一般表示初始化成功
git lfs install
​
# 2. 如果刚刚下载的那个项目没啥更改，重新下一遍，不算麻烦事（因为下载大文件，一般会比较慢）
git lfs clone https://github.com/AABBBCC/aaa.git
# 在下载的过程中，你也可以查看一下，你刚刚无法解析的那个pkl大文件，是不是在这个项目中，(进入项目目录)使用如下指令：
cd aaa
git lfs track
​
# 3. 如果不想重新下载整个项目，可以使用如下命令，单独下载需要使用lfs下载的大文件。
git lfs fetch
git lfs checkout
#（备选：git lfs pull），不建议
```
**到所要下载模型或数据集文件后，去掉/tree/main,然后添加.git,知乎使用 git clone + URL就可以下载啦**









