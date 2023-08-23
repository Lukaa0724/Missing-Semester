# fatal: unable to access ‘XXX‘: Recv failure: Connection was reset
```shell
git config --global --unset http.proxy
git config --global --unset https.proxy
```
然后以管理员身份打开cmd，输入ipconfig /flushdns来清除DNS缓存即可

[CSND teaching](https://blog.csdn.net/m0_69087087/article/details/128838186)

# Failed to connect to github.com port 443:connection timed out
![Alt text](image.png)
这个问题只需要取消园全局代理即可，就像上面的两行代码，甚至不需要清除DNS缓存。