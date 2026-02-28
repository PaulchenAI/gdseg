# 广东省图学学会 FuAdmin 管理平台

<div align="center">

基于 **Django + Django Ninja + Vue3 + Vben Admin** 的通用后台管理系统

[![img](https://img.shields.io/badge/license-Apache%202.0-dark)](https://gitee.com/fuadmin/fu-admin/blob/master/LICENSE)
[![img](https://img.shields.io/badge/python-%3E=3.10.x-green.svg)](https://python.org/)
[![PyPI - Django Version badge](https://img.shields.io/badge/django%20versions-4.0-blue)](https://docs.djangoproject.com/zh-hans/4.0.4/)
[![img](https://img.shields.io/badge/node-%3E%3D%2018.0.0-brightgreen)](https://nodejs.org/zh-cn/)
[![img](https://gitee.com/fuadmin/fu-admin/badge/star.svg?theme=dark)](https://gitee.com/fuadmin/fu-admin)
[![GitHub stars](https://img.shields.io/github/stars/FuAdmin/FuAdmin.svg?theme=dark&label=Github)](https://github.com/FuAdmin/FuAdmin)

</div>

---

## 🧾 项目简介

**FuAdmin** 是一套基于 Django + Django Ninja + Vue3 + Vben Admin 的通用后台管理平台：

- 后端基于 **Django + Django Ninja**，提供高性能 API 能力  
- 前端基于 **Vue3 + Vite + Vben Admin + Ant Design Vue**，提供现代化中后台界面  
- 内置菜单、角色、部门、岗位、字典、日志、附件、定时任务等通用模块  
- 支持动态权限菜单、多维度权限控制，适合作为中小型项目的基础脚手架  

在线体验地址（如有变化以实际部署为准）：  
`http://124.222.210.96:8080`

- 账号：`superadmin`  
- 密码：`123456`

---

## 🧠 为什么选择 Django Ninja + Vue3

### Django Ninja 相比 DRF 的优势

- 简单直观：基于装饰器声明 API，类型提示友好  
- 高性能：得益于 Pydantic 与异步支持，性能优秀  
- 快速开发：自动文档、Schema 生成，让你专注业务逻辑  
- 标准化：遵循 OpenAPI 与 JSON Schema 标准  
- 深度集成 Django：与 Django ORM、认证等生态紧密结合  

![](screenshots/benchmark.png)

### Vue3 的优势

- 生态成熟，国内最主流的前端框架之一  
- 性能优于 Vue2，运行速度更快、打包体积更小  
- 更好的 TypeScript 支持，利于中大型项目维护  
- 组合式 API 便于逻辑拆分与复用  
- 搭配 Vben Admin、Ant Design Vue 提供完善的中后台 UI 解决方案  

---

## 📦 平台特性与模块

### 技术栈

- 前端：[Vue3](https://cn.vuejs.org/) + [Vite](https://vitejs.dev/) + [Vben Admin](https://vvbin.cn/doc-next) + [Ant Design Vue](https://www.antdv.com/docs/vue/getting-started-cn) + TypeScript  
- 后端：Python 3.10+、Django 4.x、[Django Ninja](https://django-ninja.rest-framework.com/)  
- 数据库：MySQL / SQL Server / SQLite 等  
- 其他：Redis 作为缓存和会话存储（推荐）  

### 内置功能

1. 菜单管理：配置系统菜单、按钮权限标识、后端接口权限等  
2. 部门管理：组织架构（公司、部门、角色）维护  
3. 角色管理：角色菜单权限、数据权限范围分配  
4. 权限管理：按角色 / 部门划分权限范围  
5. 用户管理：系统用户的增删改查与授权  
6. 数据字典：维护系统内常用枚举/常量数据  
7. 分类字典：维护树形结构字典数据  
8. 附件管理：统一管理文件、图片等资源  
9. 操作/登录日志：记录系统操作与异常信息  
10. 定时任务：系统定时任务配置与管理  

特别鸣谢：  
[VbenAdmin](https://github.com/vbenjs/vue-vben-admin) 、[Ant Design Vue](https://github.com/vueComponent/ant-design-vue)、[GoView](https://mtruning.club/)  

Vue2 版本可参考：[Dvadmin](https://gitee.com/liqianglog/django-vue-admin)  

---

## 🏗 系统架构

整体架构可以分为三层：

- 应用层：  
  - `web/` 提供基于 Vben Admin 的后台管理界面  
  - `frontend/` 提供面向业务场景的门户网站（如考试报名、新闻展示等）  
- 服务层：  
  - `backend/` Django + Django Ninja 提供统一 API、认证授权、任务调度等能力  
- 基础设施层：  
  - MySQL/SQL Server/SQLite 作为业务数据库  
  - Redis 作为缓存与会话存储  

前端通过 HTTP/JSON 调用后端 API，统一使用 JWT 等方式进行认证；后台管理和业务门户共用同一套权限与数据模型，便于统一运维和扩展。  

---

## 📂 项目结构（简要）

本仓库的目录结构大致如下（节选）：

```bash
scutfuadmin/
├── backend/        # 后端 Django 项目（FuAdmin 主体）
├── web/            # Vben Admin 后台管理前端
├── frontend/       # 业务门户前端（SCUT 创新实验室 / 考试中心站点）
├── docker/         # Docker 相关文件
├── logs/           # 日志目录
└── README.md       # 当前说明文档
```

- 后端代码位于 `backend/` 目录下  
- 主前端管理界面位于 `web/` 目录下  
- 业务门户网站位于 `frontend/` 目录下  

---

## ⚙️ 环境准备

确保本地已安装：

```bash
Python >= 3.10.0   # 推荐 3.10+
Node.js >= 18.0.0  # 推荐最新 LTS
MySQL >= 8.0       # 可选，默认 sqlite3
Redis              # 推荐，默认需要，可在 backend/cache 配置中修改
```

---

## � 前端说明

项目包含两个独立前端：后台管理端 `web/` 与业务门户端 `frontend/`，二者共享后端 API，但面向的用户场景不同。  

### web 后台管理端

- 角色定位：后台运维与业务管理入口  
- 主要能力：菜单与权限管理、用户与角色配置、字典维护、日志与附件管理、任务调度等  
- 技术栈：Vue3 + Vite + Vben Admin + Ant Design Vue + TypeScript  

### frontend 门户网站

`frontend/` 目录提供了基于 **Vue3 + TypeScript + Vite** 的门户网站，主要面向实际业务场景展示与交互（如学院门户 / 考试服务等）。  

#### 技术栈

- 框架：Vue 3.x `<script setup>`  
- 组件库：Element Plus、Vuetify  
- 路由：Vue Router  
- 状态管理：Pinia  
- HTTP：Axios  
- UI 设计与组件开发：Storybook + Vitest（支持组件开发、单测与可视化预览）  

#### 功能特性（按业务模块）

- 首页与概览  
  - 多个概览页面（OverviewPage 系列），展示学院/实验室整体介绍、风采图片等  
  - 首页导航、页头/页脚组件（Header、Navigation、ScutFooter 等）  
- 考试与证书  
  - 考试报名页：支持考试信息展示与报名流程引导（Exam_registration、Registration 等）  
  - 成绩与证书展示：包括成绩查询、证书展示页面（Certificate、CertificateDisplay、grade 等）  
- 新闻与通知  
  - 新闻列表与详情页：分行业动态、社会新闻等分类（Industry、Society、Detail 等）  
  - 公告与通知：通过 `public/documents/notifications` 等资源目录展示通知文件与图片  
- 成员与关于  
  - Members / Overview / Management 等页面展示团队成员、管理结构与项目背景  
  - Contact 页面提供联系方式与咨询通道  
- 用户中心  
  - 登录/注册页面（Login、Register）  
  - 个人信息与资料管理（Profile）  
  - 修改密码（ChangePassword）  

通过 Storybook（`pnpm run storybook`）可以独立预览和开发 `frontend` 中的各类组件与页面，支持按业务模块拆分、复用布局与样式。  

---

## 🎨 启动前端（web）

> 前端推荐使用 **pnpm**，项目提供了 `pnpm-lock.yaml`，使用其他包管理器可能导致依赖版本不一致。

```bash
# 进入前端目录
cd web

# 如果本机尚未安装 pnpm
npm install -g pnpm

# （可选）设置 npm 源
npm config set registry https://registry.npmjs.org/

# 安装依赖
pnpm install

# 启动开发环境
pnpm serve
# 或者根据实际脚本使用
# pnpm dev

# 默认访问地址（以实际控制台输出为准）
# http://localhost:8080
```

如需构建生产环境，可执行：

```bash
pnpm build
```

---

## 🧩 启动后端（backend）

```bash
# 进入后端目录
cd backend

# 建议创建并激活虚拟环境（略）

# 安装依赖
pip install -r requirements.txt

# 在 backend/conf/env.py 或相关配置中设置数据库信息
# 默认使用 MySQL，如需使用 SQL Server，请在 requirements.txt 中启用：
#   mssql-django==1.1.2
#   pyodbc==4.0.32

# 初始化数据库
python manage.py makemigrations system
python manage.py migrate

# 初始化基础数据（管理员账号、菜单等）
python manage.py init

# 启动开发服务
python manage.py runserver 0.0.0.0:8000
# 或使用 daphne
# daphne -b 0.0.0.0 -p 8000 fuadmin.asgi:application
```

### 访问后端文档

- API 文档地址：`http://localhost:8000/api/docs`  
- 默认账号：`superadmin`  
- 默认密码：`123456`  

---

## 🎥 界面预览

![](screenshots/1.png)
![](screenshots/2.png)
![](screenshots/3.png)
![](screenshots/4.png)
![](screenshots/5.png)
![](screenshots/6.png)
![](screenshots/7.png)
![](screenshots/8.png)
![](screenshots/9.png)

---

## 🔗 源码地址

|        | 项目地址                            |
| ------ | ----------------------------------- |
| GitHub | https://github.com/FuAdmin/fu-admin |
| 码云   | https://gitee.com/fuadmin/fu-admin  |

---

## 🐳 Docker 构建

如需使用 Docker 部署，请参考：  
[Docker 构建说明](docker/README.md)
