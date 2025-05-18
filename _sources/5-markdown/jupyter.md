
# Jupyter 
## 使用 pyvista[^3] 在网页上实现计算结果的可视化启动jupyter

### 安装 jupyter 和 pyvista

```bash
pip install 'jupyterlab>=3' ipywidgets 'pyvista[all,trame]'
pip install notebook
jupyter notebook password
jupyter notebook --port=9202 --ip=0.0.0.0
```

然后设置外网访问[^1][^2], 需要注意的是打开websocket才能执行代码，否则只能写代码。
![image-20250518173009001](https://githubimages.pengfeima.cn/images/202505181730334.png)

### 运行pyvista

可以选择前端显示或者后端显示。

![image-20250518113614370](https://githubimages.pengfeima.cn/images/202505181136541.png)

## 系统默认启动

> 我通过ssh登陆命令执行脚本，尽可能与命令行执行命令的环境相同

```bash
sudo vi /etc/systemd/system/manyservices.service
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys 
sudo systemctl enable manyservices.service 
# sudo systemctl daemon-reload
sudo systemctl restart manyservices.service 
sudo journalctl -u manyservices.service -n 100
```

```bash
ssh fenics@localhost "export DISPLAY=:99.0 && source ~/pyvenv/bin/activate && jupyter notebook --port=9202 --ip=0.0.0.0 --notebook-dir=/home/fenics/jupyter"
```

```ini
[Unit]
Description=many services
After=network.target syslog.target
Wants=network.target

[Service]
Type=simple
# 指定运行用户和组
User=fenics
Group=fenics
# 启动命令
Restart=on-failure    
RestartSec=5s
ExecStart=/bin/bash /home/fenics/start_services.sh

[Install]
WantedBy=multi-user.target
```













[^1]: http://talk.pengfeima.cn/t/topic/278/4?u=merryjingle
[^3]: https://tutorial.pyvista.org/tutorial/00_jupyter/index.html
[^2]: https://jupyter.pengfeima.cn
