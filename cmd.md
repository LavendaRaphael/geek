## mklink

<https://liam.page/2018/12/10/mklink-in-Windows/>  
删除虚拟的链接目录，并不会删除远程文件夹真实文件，注意千万不能用del，del会删除远程的真实文件。

```cmd
rmdir d:\recivefiles
rmdir d:\develop
```
