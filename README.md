## 1 Backend


### （1）提供 `.env` 文件

复制 `backend/.env.example`，并重命名为 `backend/.env`，然后修改里面的邮箱配置

### （2）修改 `config.py` 文件

修改 `back-end/config.py` 中的配置，比如 `SECRET_KEY` 和 `SQLALCHEMY_DATABASE_URI`

> `ADMINS` 这个配置一定要修改！

```
ADMINS = ['xxx@qq.com']  # 管理员的邮箱地址
```

因为在这个列表中的邮箱地址，在注册时，会自动赋予管理员的角色

### （3）启动后端 Flask 应用

Open a new terminal:

```bash
$ cd back-end
$ python -m venv venv
$ source venv/bin/activate  # 如果是Windows环境，则执行 venv\Scripts\activate
(venv)$ pip install -r requirements.txt

# Flask-Migrate create database
(venv)$ flask db upgrade

# Pre deploy, eg. insert roles
(venv)$ flask deploy

# create back-end/.env file, like this
FLASK_APP=microblog.py
FLASK_DEBUG=1

(venv)$ flask run
```

浏览器访问: `http://localhost:5000/api/ping`，比如返回 `"Pong!"` 则说明正常


## 2 Frontend

### （1）安装 Node.js

请前往 [官方网站](https://nodejs.org/zh-cn/) 下载并安装 `LTS` 版本

安装好后，由于 `npm` 命令使用的国外镜像，在国内下载依赖包时很慢，这里换成 [淘宝 NPM 镜像](https://npm.taobao.org/)

打开 `cmd`：

```bash
$ npm install -g cnpm --registry=https://registry.npm.taobao.org
```

之后，用 `cnpm` 来代替 `npm` 命令

### （2）运行前端应用

Open a new terminal:

```bash
$ cd front-end
$ cnpm install
$ npm run dev
```

浏览器访问: `http://localhost:8080`


## 3 注册管理员账号

浏览器访问: `http://localhost:8080/#/register` 注册你的管理员账号 (注册时填写的 Email 在配置文件 `config.py` 的 `ADMINS` 中即可！)

然后登录你的这个邮箱，去激活账号