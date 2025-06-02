# SpringBoot-Learning

## 记录学习spring的基础知识和项目遇到的问题及解决办法

传统的javaweb项目最终会把程序（其中包括：所有的 Java 代码（编译好的 class 文件），依赖的 jar 文件（库），配置文件（如 web.xml）以及 Web 资源（html, jsp, css, js 等））整合为一个war包，把这个war包发给服务器，服务器就会解压和运行这个war包，于是我们的javaweb项目就从本地变为网络的了。以下是一个传统的javaweb项目开发流程：

1️⃣ 本地开发
在 Eclipse、IntelliJ IDEA 里写 Java 代码，调试、测试。

2️⃣ 打包成 WAR
通过 maven、gradle 之类的工具，把整个 Web 项目打成一个 xxx.war 文件。

3️⃣ 传给服务器
把 xxx.war 文件上传到服务器（Linux、Windows、云…）。

4️⃣ Web 容器（Tomcat）接手
Tomcat 会自动把 WAR 文件解压到它的 webapps 目录

5️⃣ 运行
Tomcat（或其他容器）自动加载解压后的 WEB-INF/classes（class 文件）和 WEB-INF/lib（依赖的 jar 包），然后就能对外提供 Web 服务（比如 http://localhost:8080/myapp）！


springboot再次简化了上述的流程，内嵌了一个Tomcat，也就是说，我的项目不再需要外部的web容器了。以下是对比的表格： 

| 项目类型 | Spring Boot Jar 包            | Spring Boot War 包                    |
| ---- | ---------------------------- | ------------------------------------ |
| 服务器  | 内嵌 Tomcat / Jetty / Undertow | 外部 Tomcat / Jetty / JBoss…           |
| 打包结果 | `.jar` 文件                    | `.war` 文件                            |
| 运行方式 | 直接 `java -jar xxx.jar`       | 把 `.war` 放到外部 Tomcat 的 `webapps` 目录里 |
| 推荐场景 | 新项目，简化部署，支持容器化（Docker）       | 老旧 Tomcat 平台，或需要集成传统 Web 容器          |
