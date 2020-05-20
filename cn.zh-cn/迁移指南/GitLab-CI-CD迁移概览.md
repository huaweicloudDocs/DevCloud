# **GitLab CI/CD迁移概览**<a name="devcloud_migration_0009"></a>

本文主要介绍使用GitLab进行CI/CD的企业，如何迁移至DevCloud平台进行持续构建与部署。

GitLab CI指不断的将新代码集成到服务器，并尽早进行自动构建、集成测试的过程。GitLab 8.0+提供了GitLab CI功能， 使GitLab中的工程代码不必再依赖其他工具（如Jenkins）就可以进行独立的构建。GitLab Runner则是实际处理GitLab CI构建的应用程序， 它通常单独部署，通过注册到GitLab工程下被调用 。

GitLab CD指将验证过的软件推送到测试环境、类生产环境或者生产环境的过程，GitLab通常依赖编写脚本“.gitlab-ci.yml“指定部署动作。

本文要迁移的目标平台是[软件开发平台DevCloud](https://www.huaweicloud.com/devcloud/)，该平台支持DevOps研发全流程，对多语言CI/CD提供较好的云环境，通过界面化的任务配置，减少脚本编写，降低使用者学习成本。

## **迁移前准备**<a name="section83924404172"></a>

-   **账号申请**：使用华为云软件开发平台DevCloud前，请确保您已拥有已实名认证的华为云账号；若您还没有华为云账号，请先进行注册，并完成实名认证。
-   **DevCloud项目创建与代码托管**：参考[GitLab迁移至DevCloud](GitLab迁移至DevCloud.md)。
-   **购买弹性云服务器**：DevCloud部署将使用带有公网IP的云服务器，如果有可以不必购买。本文使用的是华为云ECS（CentOS 7.2），购买方式请参考[购买并登录Linux弹性云服务器](https://support.huaweicloud.com/qs-ecs/zh-cn_topic_0132727313.html)。

  

