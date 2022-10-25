## 一些创建Docker镜像的工具

**hadolint**：一款 Dockerfile 纠错检查工具。可以检查 Dockerfile 文件里有风险的写法，并提示可能缺失的步骤。在线版本：[https://hadolint.github.io/hadolint/ ， [GitHub page](https://github.com/hadolint/hadolint) 版。

**dockle** - 地址： [https://github.com/goodwithtech/dockle](https://github.com/goodwithtech/dockle) 。主要用于检查镜像本身各个组件的安装性，协助创建最符合安全要求的镜像。

```bash
$ dockle nginx-php-stack_php-fpm
WARN    - CIS-DI-0001: Create a user for the container
        * Last user should not be root
WARN    - DKL-DI-0006: Avoid latest tag
        * Avoid 'latest' tag
INFO    - CIS-DI-0005: Enable Content trust for Docker
        * export DOCKER_CONTENT_TRUST=1 before docker pull/build
INFO    - CIS-DI-0006: Add HEALTHCHECK instruction to the container image
        * not found HEALTHCHECK statement
```
**trivy** -  地址 [https://github.com/aquasecurity/trivy](https://github.com/aquasecurity/trivy) 和 Docker 自身反而不太相关，它是针对容器和其他构件的漏洞扫描分析工具。

```bash
 trivy image nginx-php-stack_php-fpm --security-checks vuln
2022-10-24T15:25:29.799+0800    INFO    Vulnerability scanning is enabled
2022-10-24T15:25:32.635+0800    INFO    Detected OS: alpine
2022-10-24T15:25:32.635+0800    INFO    Detecting Alpine vulnerabilities...
2022-10-24T15:25:32.642+0800    INFO    Number of language-specific files: 0

nginx-php-stack_php-fpm (alpine 3.16.2)

Total: 2 (UNKNOWN: 0, LOW: 0, MEDIUM: 0, HIGH: 2, CRITICAL: 0)

│ Library │ Vulnerability  │ Severity │ Installed Version │ Fixed Version │ Title│
│ libxml2 │ CVE-2022-40303 │ HIGH     │ 2.9.14-r1         │ 2.9.14-r2     │ libxml2: integer overflows with XML_PARSE_HUGE         │https://avd.aquasec.com/nvd/cve-2022-40303                 
│         │ CVE-2022-40304 │ HIGH     │ 2.9.14-r1         │ 2.9.14-r2     │ libxml2: dict corruption caused by entity reference cycles │https://avd.aquasec.com/nvd/cve-2022-40304  │

```