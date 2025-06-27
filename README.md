# 餐厅管理系统

一个基于 Vue 3 + Spring Boot 的现代化餐厅管理系统，提供点餐、预订、外卖和营收管理等功能。

## 项目概述

本项目是一个全栈餐厅管理系统，包含前端 Vue 3 应用和后端 Spring Boot API。系统支持餐厅的日常运营管理，包括菜品管理、订单处理、预订管理、外卖配送和营收统计等核心功能。

## 技术栈

### 前端
- **Vue 3** - 渐进式 JavaScript 框架
- **Vite** - 现代化构建工具
- **Element Plus** - Vue 3 UI 组件库
- **Vue Router** - 官方路由管理器
- **Axios** - HTTP 客户端

### 后端
- **Spring Boot 3.5.3** - Java 企业级应用框架
- **Spring Data JPA** - 数据持久化
- **MySQL** - 关系型数据库
- **Maven** - 项目管理工具

## 主要功能

### 1. 用户认证
- 登录/登出功能
- 用户角色管理（管理员/普通用户）

### 2. 点餐管理
- 菜品分类浏览（荤菜/素菜）
- 菜品搜索功能
- 购物车管理
- 餐桌管理
- 订单生成和结算

### 3. 预订管理
- 预订请求提交
- 预订确认/拒绝
- 预订状态跟踪
- 餐桌分配

### 4. 外卖配送
- 外卖订单管理
- 配送状态跟踪
- 骑手分配
- 配送时间管理

### 5. 营收统计
- 账单管理
- 收入统计
- 支付方式记录
- 财务报表

## 项目结构

```
test-main2/
├── demo/                          # Spring Boot 后端
│   ├── src/main/java/com/example/demo/
│   │   ├── controller/            # REST API 控制器
│   │   ├── entity/               # JPA 实体类
│   │   ├── repository/           # 数据访问层
│   │   ├── service/              # 业务逻辑层
│   │   ├── dto/                  # 数据传输对象
│   │   └── config/               # 配置类
│   ├── src/main/resources/
│   │   └── application.properties # 应用配置
│   └── pom.xml                   # Maven 配置
├── src/                          # Vue 3 前端
│   ├── views/                    # 页面组件
│   │   ├── Login.vue            # 登录页面
│   │   ├── MainLayout.vue       # 主布局
│   │   ├── Order.vue            # 点餐页面
│   │   ├── Reservation.vue      # 预订管理
│   │   ├── Delivery.vue         # 外卖管理
│   │   ├── Revenue.vue          # 营收统计
│   │   └── Settings.vue         # 系统设置
│   ├── router/                   # 路由配置
│   ├── components/               # 公共组件
│   └── assets/                   # 静态资源
├── public/                       # 公共资源
│   └── tupian/                   # 菜品图片
├── package.json                  # 前端依赖配置
└── vite.config.js               # Vite 配置
```

## 安装和运行

### 环境要求
- Node.js 16+
- Java 17+
- MySQL 8.0+
- Maven 3.6+

### 数据库配置

1. 创建 MySQL 数据库：
```sql
CREATE DATABASE restaurant_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

2. 修改后端配置文件 `demo/src/main/resources/application.properties`：
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/restaurant_db?useSSL=false&serverTimezone=Asia/Shanghai&characterEncoding=utf8
spring.datasource.username=your_username
spring.datasource.password=your_password
```

### 后端启动

1. 进入后端目录：
```bash
cd demo
```

2. 安装依赖并启动：
```bash
mvn clean install
mvn spring-boot:run
```

后端服务将在 `http://localhost:8080` 启动

### 前端启动

1. 安装依赖：
```bash
npm install
```

2. 启动开发服务器：
```bash
npm run dev
```

前端应用将在 `http://localhost:5173` 启动

### 生产环境部署

1. 构建前端：
```bash
npm run build
```

2. 打包后端：
```bash
cd demo
mvn clean package
```

## API 接口

### 主要 API 端点

- **用户认证**
  - `POST /api/login` - 用户登录

- **菜品管理**
  - `GET /api/dishes` - 获取菜品列表
  - `POST /api/dishes` - 添加菜品
  - `PUT /api/dishes/{id}` - 更新菜品
  - `DELETE /api/dishes/{id}` - 删除菜品

- **预订管理**
  - `GET /api/reservations` - 获取预订列表
  - `POST /api/reservations` - 创建预订
  - `PUT /api/reservations/{id}` - 更新预订状态
  - `DELETE /api/reservations/{id}` - 删除预订

- **外卖管理**
  - `GET /api/delivery-orders` - 获取外卖订单
  - `POST /api/delivery-orders` - 创建外卖订单
  - `PUT /api/delivery-orders/{id}` - 更新订单状态

- **营收管理**
  - `GET /api/revenue` - 获取营收数据
  - `POST /api/revenue` - 记录收入

## 使用说明

### 1. 登录系统
- 访问 `http://localhost:5173/login`
- 输入用户名和密码登录
- 系统支持管理员和普通用户两种角色

### 2. 点餐功能
- 在主界面选择菜品分类
- 浏览菜品并添加到购物车
- 选择餐桌号
- 确认订单并结算

### 3. 预订管理
- 提交预订请求（客户信息、时间、人数）
- 管理员确认或拒绝预订
- 分配餐桌
- 跟踪预订状态

### 4. 外卖管理
- 创建外卖订单
- 分配配送员
- 跟踪配送状态
- 确认送达

### 5. 营收统计
- 查看日常账单
- 统计收入数据
- 分析支付方式
- 生成财务报表

## 开发指南

### 添加新功能

1. **后端开发**：
   - 在 `entity` 包中创建实体类
   - 在 `repository` 包中创建数据访问接口
   - 在 `service` 包中实现业务逻辑
   - 在 `controller` 包中创建 REST API

2. **前端开发**：
   - 在 `views` 目录创建页面组件
   - 在 `router/index.js` 中配置路由
   - 使用 Axios 调用后端 API
   - 使用 Element Plus 组件构建 UI

### 代码规范

- 后端遵循 Spring Boot 最佳实践
- 前端使用 Vue 3 Composition API
- 统一的错误处理和日志记录
- RESTful API 设计原则

## 故障排除

### 常见问题

1. **数据库连接失败**
   - 检查 MySQL 服务是否启动
   - 验证数据库配置信息
   - 确认数据库用户权限

2. **前端无法访问后端 API**
   - 检查后端服务是否启动（端口 8080）
   - 验证 Vite 代理配置
   - 检查跨域设置

3. **页面显示异常**
   - 检查浏览器控制台错误信息
   - 验证 Element Plus 组件导入
   - 确认路由配置正确

## 贡献指南

1. Fork 项目
2. 创建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

## 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 联系方式

如有问题或建议，请通过以下方式联系：
- 提交 Issue
- 发送邮件
- 项目讨论区

---

**注意**：这是一个演示项目，用于学习和开发目的。在生产环境中使用前，请确保进行充分的安全性测试和性能优化。
