在 Docker 中，attach 和 detach 模式是两种容器的运行方式，用于控制容器与终端的交互方式。

**Attach 模式**：
范例指令: 
```
docker container run -p 80:80 nginx
```

在 Attach 模式下，容器的标准输入（stdin）、标准输出（stdout）和标准错误（stderr）会与当前终端（通常是用户的终端）进行绑定，使得用户可以直接与容器交互。这意味着当容器启动后，它会占用当前终端，并将容器的输出发送到当前终端，用户可以直接输入命令并观察容器的输出。

使用 docker attach 命令可以将终端连接到正在运行的容器，例如：
```
docker attach <容器名称或ID>
```
这样就会将当前终端连接到指定的容器，以便与容器进行交互。请注意，如果从容器中退出（例如按下 Ctrl+C），容器可能会停止运行。

**Detach 模式**：
范例指令:
```
docker container run -d -p 80:80 nginx
```

在 Detach 模式下，容器与终端是分离的，容器的标准输入、输出和错误流不会与终端绑定。这意味着容器会在后台运行，而用户可以继续在终端上执行其他操作。容器的输出通常会重定向到日志文件或者 Docker 日志系统中。

使用 -d 或 --detach 参数可以让容器在后台运行，例如：
```
docker run -d <镜像名称>
```
这样容器会在后台运行，并返回容器的 ID，而不会将终端绑定到容器。可以使用 docker logs 命令来查看容器的输出日志。

总的来说，Attach 模式适用于需要与容器进行交互并查看实时输出的情况，而 Detach 模式适用于需要容器在后台持续运行且不影响当前终端操作的情况。