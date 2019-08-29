1.linux
在 Linux 容器中运行
在 Docker 客户端中，切换到 Linux 容器。
导航到 dotnet-docker/samples/aspnetapp 下的 Dockerfile 文件夹。
运行以下命令以在 Docker 中生成并运行示例：
console

复制
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
build 命令参数：
将映像命名为 aspnetapp。
在当前文件夹（末尾的句点）中查找 Dockerfile。
运行命令参数：
分配伪 TTY，即使未附加也使其保持打开状态。 （与 --interactive --tty 的效果相同。）
容器在退出时自动删除。
将本地计算机上的端口 5000 映射到容器中的端口 80。
将容器命名为 aspnetcore_sample。
指定 aspnetapp 映像。
在浏览器中转到 http://localhost:5000 以测试应用。

2.windows
在 Docker 客户端中，切换到 Windows 容器。
导航到 dotnet-docker/samples/aspnetapp 下的 docker 文件文件夹。
运行以下命令以在 Docker 中生成并运行示例：
console

复制
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
对于 Windows 容器，你需要容器的 IP 地址（浏览到 http://localhost:5000 不起作用）：
打开另一个命令提示符。
运行 docker ps 以查看正在运行的容器。 验证其中是否包含“aspnetcore_sample”容器。
运行 docker exec aspnetcore_sample ipconfig 以显示容器的 IP 地址。 该命令的输出如以下示例所示：
console

复制
Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : contoso.com
   Link-local IPv6 Address . . . . . : fe80::1967:6598:124:cfa3%4
   IPv4 Address. . . . . . . . . . . : 172.29.245.43
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 172.29.240.1
将容器 IPv4 地址（例如，172.29.245.43）复制并粘贴到浏览器地址栏以测试应用。
3.直接发布，然后运行发布的程序
dotnet publish -c Release -o published
