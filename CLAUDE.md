# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

TheNow (当下的力量) - 全栈正念冥想应用
- **前端**：微信小程序 (Taro + React + TaroUI + TypeScript)
- **后端**：NestJS + TypeScript + MongoDB + LangChain API服务

## 开发环境

**前端开发环境**
```
# 安装依赖
pnpm install

# 启动微信小程序开发
pnpm dev:weapp
```

**后端开发环境**
```
# 安装依赖
npm install

# 启动开发服务器
npm run start:dev

# MongoDB 服务运行
docker-compose up -d mongodb
```

## 项目目录结构

```
.   
├── frontend/              # Taro 微信小程序前端  
│   ├── src/              
│   │   ├── pages/        # 小程序页面  
│   │   ├── components/   # 通用组件  
│   │   ├── models/       # 数据模型  
│   │   └── app.tsx       # 小程序入口  
│   └── config/           # Taro配置文件  
│
├── backend/               # NestJS 后端服务  
│   ├── src/  
│   │   ├── auth/         # 认证模块  
│   │   ├── meditation/   # 冥想业务逻辑  
│   │   ├── langchain/    # AI集成模块  
│   │   ├── users/        # 用户管理  
│   │   └── main.ts       # 入口文件  
│   ├── test/             # 单元测试  
│   └── docker-compose.yml # MongoDB容器配置
│
├── .env                   # 环境变量  
├── CLAUDE.md              # 当前文档  
└── README.md              # 项目说明
```

## 核心技术栈

**前端**
- Taro 3.x (React) - 跨端开发框架
- TaroUI - 微信小程序UI组件库
- TypeScript - 类型检查
- Wechat Miniprogram APIs - 微信原生能力

**后端**
- NestJS 10.x - Node.js框架
- MongoDB + Mongoose - 数据库及ODM
- LangChain.js - AI集成库
- JWT - 身份认证
- Swagger - API文档

## 架构特征

1. **前后端分离**：小程序前端通过RESTful API与后端交互
2. **领域驱动设计(DDD)**：后端按业务模块组织代码
3. **微信能力集成**：
   - 微信登录
   - 订阅消息
   - 支付集成
4. **AI集成**：
   - LangChain处理自然语言请求
   - 冥想指导生成
   - 用户反馈分析

## 开发规范

- **命名规范**：
  - 接口：RESTful风格 (GET /meditation/sessions)
  - 文件：kebab-case命名 (user-service.ts)
- **提交信息**：遵循Conventional Commits
- **代码风格**：ESLint + Prettier统一规则
- **环境管理**：
  - .env.development - 开发环境
  - .env.production - 生产环境

## 测试策略

**前端**
- Jest + @testing-library 组件测试
- Taro Mocker 模拟API

**后端**
- Jest 单元测试
- Supertest 接口测试
- MongoDB内存服务器
```
# 运行测试
npm run test
```

## CI/CD配置

- GitHub Actions自动化流程：
  - 代码检查 (ESLint)
  - 单元测试
  - 微信云托管自动部署

## 文档资源

- Swagger API文档：http://localhost:3000/api
- 微信小程序文档：https://developers.weixin.qq.com/miniprogram/dev/framework/
- Taro文档：https://taro-docs.jd.com/docs/
- NestJS文档：https://docs.nestjs.com/

## 调试提示

**微信小程序问题诊断**：
- 使用微信开发者工具真机调试
- Taro日志级别设置：`export TARO_LOG_LEVEL = 'debug'`

**NestJS调试**：
```bash
# 启用调试模式  
npm run start:debug  

# 连接到调试器(9229端口)  
chrome://inspect
```