# Dify 插件离线安装包打包工具

## 项目背景
针对 Dify 官方插件市场在离线环境下无法安装的问题，本工具提供离线安装包打包能力，支持在无网络环境部署自定义插件。

## 核心依赖
基于 [dify-plugin-repacking](https://github.com/junjiem/dify-plugin-repackaging) 项目二次开发，保留原有功能的同时优化离线打包流程。

## 运行环境要求
- 推荐使用 Linux/macOS 系统
- Windows 系统兼容性未完全测试，可能存在路径或权限问题
- 强烈建议通过 Docker 容器运行以确保环境一致性

## Docker 镜像构建指南
1. 确保 Docker 已正确安装并启动
2. 使用项目提供的 Dockerfile 构建镜像：
   ```bash
   docker build -t dify-plugin-builder:v1.0 .
注意事项：
Dockerfile 中指定的 Python 版本必须与 Dify 官方插件运行环境一致（当前建议使用 Python 3.12.3）
版本不匹配可能导致打包的插件在安装时出现兼容性错误
## 容器化运行步骤
1. 启动打包服务容器：
   ```bash
        docker run -d -p 5000:5000 dify-plugin-builder:v1.0    
   ```

2. 访问管理界面：http://127.0.0.1:5000（默认端口）