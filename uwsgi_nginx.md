# 服务器部署与维护
> 记录服务器相关操作命令。【解决相关问题时，请及时分享、记录相关操作，以备后用。】

## 首次启动
本项目采用uwsgi+nginx部署。uwsgi做python web后端服务器，nginx做HTTP反向代理。
* uwsgi配置文件： 根目录uwsgi.ini，配置了项目启动入口、进程名(uwsgi.pid)、日志文件、自动重启等。【待补充模板】 
* 首次启动项目，直接使用uwsgi启动：
```
uwsgi -ini uwsgi.ini 
```
会按照uwsgi.ini配置信息，启动程序，生成项目进程，如uwsgi.pid（查看uwsgi.ini获得具体的进程名）。

## 修改项目文件后，重启/重载项目
**修改py等文件后， uwsgi会自动监测modification，然后自动重启。不需要额外操作。**

如需要手动重启项目，可以采用uwsgi重载uwsgi.pid进程（查看uwsgi.ini获得具体的进程名）
```
uwsgi --reload uwsgi.pid
```

重启时，如遇错误 `signal_pidfile()/kill(): No such process`，
可以参考：[重启uwsgi pid提示找不到process](https://blog.csdn.net/Aerkui/article/details/107557727)

## 修改nginx配置文件后，重启/重载nginx
```
nginx -t #检查配置文件
nginx -s reload  # 重载nginx
```


# 其他
> uwsgi与nohup区别（by ChatGPT，**未校对**）
```
Q: uwsgi 与 nohup启动项目的区别？

nohup是一个Linux命令，用于在后台运行命令或脚本，并且即使关闭控制终端，也会持续保持运行。在启动Python项目时，可以使用nohup python <script_name>.py &来使Python脚本在后台运行，这样即使关闭控制终端，Python脚本也会持续运行。

uWSGI是一个Web服务器，可以将Python项目部署在服务器上，使之能够被HTTP请求访问。它可以管理多个Python脚本进程，处理并发请求，支持各种协议和应用程序框架。通过uWSGI启动Python项目，可以实现高效、稳定的Web服务。

总的来说，nohup用于在后台运行命令或脚本，比如让Python脚本长时间运行，而uWSGI用于将Python项目部署在Web服务器上，使之能够高效、稳定的处理并发请求。
```
```
Q： 假如用两者分别启动了项目，接下来在管理进程方面有什么区别？

`nohup`命令是基于Linux终端的，使用Linux命令行来监视和管理该进程，例如`ps`、`kill`等查看和结束进程；另外，使用nohup启动进程不会提供任何服务的监控和日志记录。这种方式对于简单的Python脚本可以很好地工作，但是对于复杂的多进程Python应用可能就不太有效了。

相反，`uWSGI`是一个更全面的Web服务程序，它提供了更强大的进程和资源管理功能，因此更适用于处理长时间运行且对并发请求产生响应的Python Web应用。使用uWSGI，可以使用一些命令来启动、停止、挂起、恢复进程，例如下面的命令：

- `uwsgi --ini <uwsgi.ini>`：启动uWSGI进程
- `uwsgi --reload <uwsgi.pid>`：暂重载uWSGI进程
- `uwsgi --stop <uwsgi.pid>`：关闭uWSGI进程
- `uwsgi --status <uwsgi.pid>`：查看进程信息

在使用uWSGI时，还可以使用uWSGI管理器，一个网页版的程序，可以用于动态监控和管理进程。该管理器提供了许多有用的功能，例如查看请求统计数据、复制进程、动态修改配置等。

综上所述，使用`nohup`需要手动使用一些Linux命令来管理进程，更适合简单的单个脚本的管理; 而使用`uWSGI`可以使用更强大的进程和资源管理功能，更好地进行性能优化和故障排除。
```

```
Q: uwsgi进程管理相关命令？

在使用uWSGI启动Python项目后，可以使用以下命令来管理uWSGI进程：

1. 启动uWSGI：`uwsgi --ini uwsgi.ini`。其中，`uwsgi.ini`是uWSGI配置文件的名称，用于控制进程启动时的各种参数和配置信息。

2. 关闭uWSGI：`uwsgi --stop <uwsgi.pid>`。其中，`uwsgi.pid`是uWSGI进程的PID文件地址，这个文件记录了uWSGI的当前PID，用于控制进程的关闭。

3. 重新加载uWSGI：`uwsgi --reload <uwsgi.pid>`。这个命令会重新加载uWSGI进程，并且会在无需关闭当前进程的情况下更新配置文件和代码变化。

4. 查看uWSGI进程信息：`uwsgi --status <uwsgi.pid>`。这个命令可以查看当前正在运行的uWSGI进程的状态信息，例如进程ID、启动时间、运行时间、请求数等。

5. 查看uWSGI进程日志：通过配置文件，可以配置uWSGI将日志文件输出到特定的位置。对于常见的Linux系统，uWSGI日志文件通常存放在`/var/log/uwsgi`目录中，您可以通过查看日志文件来了解uWSGI进程的详细信息和错误信息。

这些是uWSGI常用的进程管理命令，可以通过这些命令对uWSGI进程进行启动、关闭、重新加载和监视。同时，uWSGI还提供了更多的高级命令和功能，例如内存使用情况监视、进程调试等，可以根据需要进行了解和使用。
```