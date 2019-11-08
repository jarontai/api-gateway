简体中文 | [English](./README_EN.md)

# express-vue-admin

## 使用 Node.js（Express.js）, Vue2 开发的管理后台脚手架项目

## 特点
  * 全栈 Javascript 应用
  * 使用 Express.js 构建，清晰且可测试的 rest api
  * 最小化的用户/角色/权限管理功能
  * 使用 iview 框架构建的简洁后台界面

## 组件

express-vue-admin 使用了很多组件（库）来构建后端接口和前端UI：

### 后端
* [express](https://expressjs.com/) - 后端web框架
* [sequelize](http://docs.sequelizejs.com/) - 数据库ORM
* [joi](https://github.com/hapijs/joi) - 参数校验
* [dotenv](https://github.com/motdotla/dotenv) - 环境配置
* [mocha](https://mochajs.org/)/[chai](http://chaijs.com/)/[chai-http](https://github.com/chaijs/chai-http) - 接口测试相关组件
* mysql - 数据库
* redis - 缓存
* ...

### 前端
* [vue2](https://vuejs.org/) - 前端JS框架
* [iview](https://www.iviewui.com/) - 前端UI框架
* [vue-resource](https://github.com/pagekit/vue-resource)/[vue-router](https://github.com/vuejs/vue-router)/[vuex](https://github.com/vuejs/vuex) - vue 相关的路由、状态管理等组件

## 项目文件及说明：

      .
      ├── .env.example  环境配置示例
      ├── .sequelizerc  sequelize配置
      ├── screenshots/  应用运行截图
      ├── web/          vue web应用
      ├── test/         接口测试文件
      ├── server.js     服务器
      ├── middleware/   中间件
      | ├── base.js     基础中间件
      | ├── auth.js     鉴权中间件
      | └── ...         其他业务中间件
      ├── route/        路由
      | ├── base.js     基础路由
      | ├── admin.js    admin模块路由
      | └── ...         其他路由
      ├── controller/   控制器
      | ├── base.js     基础控制器
      | ├── rest.js     rest基础控制器
      | ├── session.js  session控制器
      | ├── admin/      admin模块控制器
      | └── ...         其他业务模块控制器
      ├── database/     sequelize数据库文件
      | ├── models/     模型
      | └── migrations/ migration文件
      | └── seeders/    seeder文件
      ├── util.js       工具
      └── config/       配置
        └── database.js sequelize-cli数据库配置

## 运行截图:

### login

<p align="center">
<kbd>
  <img src="https://raw.github.com/jarontai/express-vue-admin/master/screenshots/login.png">
</kbd>
</p>

### admin/user

<p align="center">
<kbd>
  <img src="https://raw.github.com/jarontai/express-vue-admin/master/screenshots/admin_user.png">
</kbd>
</p>

### admin/role

<p align="center">
<kbd>
  <img src="https://raw.github.com/jarontai/express-vue-admin/master/screenshots/admin_role.png">
</kbd>
</p>

### admin/role delete

<p align="center">
<kbd>
  <img src="https://raw.github.com/jarontai/express-vue-admin/master/screenshots/admin_role_delete.png">
</kbd>
</p>


## 运行:

 1. 安装redis，用于存储session （可选）

 2. 复制.env.example到.env，并对各个项目进行配置 （不配置redis，session将保存在内存中，生产环境不推荐）
    ```
    #server
    NODE_ENV=development 环境配置
    SERVER_PORT=3000 服务器端口
    API_PATH=/api 接口基路径
    API_VERSION=v1 接口版本

    #db
    DB_HOST=localhost 数据库host
    DB_DATABASE=admin 数据库名称
    DB_USER=root 数据库用户
    DB_PASSWORD=root 数据库密码

    #redis
    REDIS_HOST=localhost redis缓存host
    REDIS_PORT=6379 redis端口

    #misc
    ADMIN_SEED_PASSWORD=adminpwd admin帐号密码
    TEST_SEED_PASSWORD=testpwd 测试帐号密码
    SERVER_PORT_TEST=3001 单元测试服务器端口

    ```

 3. 安装依赖、初始化数据库、填充seed数据:
    ```
    $ npm install // 安装依赖
    $ npx sequelize db:migrate // 数据库结构构建
    $ npx sequelize db:seed:all // 数据库数据填充
    ```

 4. 运行server和web应用
    ```
    $ npm start // 开启后端服务

    $ cd ./web  // 进入web文件夹
    $ npm install // 安装依赖
    $ npm run dev // 运行web应用
    ```

## 测试

基本的接口测试：

```
$ npm run test
```

## TODO

* 国际化（i18n）
* ...

## MIT License
