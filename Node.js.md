# Node.js

---



# 安装Node.js

1. 官方Ubuntu商店版本

   `sudo apt-get install nodejs`

2. 最新版本安装

   ```
   sudo apt install curl 
   curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash
   source ~/.bashrc 
   nvm install 版本
   nvm use 版本
   ```
   
   windows版本：https://blog.csdn.net/qq_39367410/article/details/126892822



# NVM

NVM：Node Version Manage，即Node的版本管理工具。使用NVM，可以很方便地在多个NodeJS版本之间进行切换。

由于项目开发当中，不同的项目可能依赖不同版本的NodeJS，这种情况下，NodeJS版本的切换将会是一件非常麻烦的事情。因此，使用NVM管理NodeJS版本就显得尤为重要。

1. 安装nvm

   ```
   sudo apt install curl 
   curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash
   source ~/.bashrc
   ```

2. 下载NodeJS版本

   ```
   nvm install version
   ```
   
3. 切换版本

   ```
   nvm use version
   ```

   



# npm

1. 安装包

    ```bash
    npm install xxx
    ```

2. 查看已安装包

    ```bash
    npm ls # 查看当前项目已安装
    -g	# 全局已安装
    --depth 0	# 限制深度
    --prod	# 只想显示生产环境依赖的包
    --dev	# 只显示开发环境依赖的包
    ```

    
