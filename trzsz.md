# trzsz

> Ref: <https://github.com/trzsz/trzsz-go/releases>

1. 在本地连接堡垒机的时候：

   ```bash
   # 第一次使用时，本地先安装：
   # brew install trzsz-go

   trzsz -d ssh xxxx.xxxx
   ```

1. 中间无论经过多少次中转，都不需要trzsz

1. 到达最终目标机器的时候，用目标机器上的trz或者tsz传输文件（通过最上面的Ref链接下载rpm包，在目标机器上安装trzsz）
