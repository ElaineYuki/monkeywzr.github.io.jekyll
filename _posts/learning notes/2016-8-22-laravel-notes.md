## gulp的相关问题

在项目根目录下运行gulp可能会出现：`not found: notify-send`的错误提示，这个实际上对测试没有影响，只是一个弹出窗提示没有加载成功而已。在ubuntu上的解决办法很简单：
    
    sudo apt-get install libnotify-bin
    
即可。如果还有错误提示，可尝试`npm install notify-send`
