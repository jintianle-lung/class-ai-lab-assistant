# 阿里云学生权益 + 百炼 Qwen/DeepSeek + OpenCode 傻瓜教程

> 目标读者：非技术同学、初学者、第一次配置 AI 编程工具的学生。  
> 目标效果：学生完成阿里云学生认证后，用领取到的 300 元权益抵扣百炼按量调用费用，并在 OpenCode 里使用 Qwen / DeepSeek 辅助完成课堂实验。

## 0. 先把路线讲清楚

推荐学生优先走这条路线：

```text
阿里云账号
-> 学生认证
-> 领取 300 元学生权益
-> 开通百炼 Model Studio
-> 创建百炼 API Key
-> 配置 OpenCode
-> 在项目里使用 Qwen / DeepSeek
```

注意两句话：

1. 这不是“无限免费”，而是用学生权益/优惠券抵扣阿里云部分公共云产品费用，最终是否抵扣、抵扣多少，以阿里云页面和费用中心显示为准。
2. 普通学生优先使用“百炼按量计费”。不要一上来买 Coding Plan，因为 Coding Plan 是另一套套餐，API Key 和 Base URL 都不一样。

## 1. 你需要准备什么

你需要：

1. 一个阿里云账号。
2. 能完成学生身份认证。
3. 一台能安装 Node.js 的电脑。
4. 一个课程项目文件夹，例如 Windows 程序设计、C/C++、Java、Python 项目。
5. 一点耐心：第一次配置大概 20-40 分钟。

## 2. 领取阿里云学生 300 元权益

1. 打开阿里云高校计划页面：

   <https://university.aliyun.com/>

2. 登录阿里云账号。

3. 找到学生权益、云工开物、高校学生通用权益等入口。

4. 按页面提示完成学生认证。

5. 领取 300 元权益。

6. 领取后检查余额：

```text
阿里云控制台
-> 费用与成本
-> 卡券管理
-> 优惠券管理
```

阿里云官方页面写明：通过学生认证的高校学生可领取 300 元无门槛优惠券，活动时间、名额、适用范围以活动页面展示为准。

## 3. 开通百炼并创建 API Key

1. 打开百炼控制台：

   <https://bailian.console.aliyun.com/>

2. 如果页面提示开通服务，按提示开通。

3. 进入 API Key 页面。

4. 点击创建 API Key。

5. 推荐选择：

```text
地域：华北 2（北京）
业务空间：默认业务空间
用途备注：opencode-student-lab
```

6. 创建后立即复制保存 API Key。

普通百炼 API Key 通常长这样：

```text
sk-xxxxxxxxxxxxxxxx
```

Coding Plan 专属 API Key 通常长这样：

```text
sk-sp-xxxxxxxxxxxxxxxx
```

本教程默认使用普通百炼 API Key，也就是 `sk-` 开头的 Key。

## 4. 安装 Node.js

OpenCode 可以用 npm 安装，所以先安装 Node.js。

1. 打开：

   <https://nodejs.org/>

2. 下载 LTS 版本。

3. 一路下一步安装。

4. 打开 PowerShell，输入：

```powershell
node -v
npm -v
```

能看到版本号就成功。

## 5. 安装 OpenCode

在 PowerShell 输入：

```powershell
npm install -g opencode-ai
```

验证：

```powershell
opencode -v
```

如果有版本号，说明安装成功。

## 6. 把 API Key 放进环境变量

不要把 API Key 直接写进项目文件，也不要发到微信群、QQ群、GitHub、截图里。

在 PowerShell 输入下面命令，把 `YOUR_API_KEY` 替换成自己的 `sk-...`：

```powershell
[Environment]::SetEnvironmentVariable("DASHSCOPE_API_KEY", "YOUR_API_KEY", [EnvironmentVariableTarget]::User)
```

然后关闭 PowerShell，重新打开一个 PowerShell，检查：

```powershell
echo $env:DASHSCOPE_API_KEY
```

能看到 `sk-...` 说明生效。不要把完整 Key 截图发给别人。

## 7. 创建 OpenCode 配置文件

OpenCode 的全局配置文件一般放在：

```text
C:\Users\<你的用户名>\.config\opencode\opencode.json
```

PowerShell 可以这样打开：

```powershell
mkdir "$env:USERPROFILE\.config\opencode" -Force
notepad "$env:USERPROFILE\.config\opencode\opencode.json"
```

如果弹出“是否创建新文件”，选择“是”。

## 8. 复制按量计费配置

把下面内容复制到 `opencode.json`：

```json
{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "bailian-payg": {
      "npm": "@ai-sdk/anthropic",
      "name": "阿里云百炼（学生权益按量）",
      "options": {
        "baseURL": "https://dashscope.aliyuncs.com/apps/anthropic/v1",
        "apiKey": "{env:DASHSCOPE_API_KEY}"
      },
      "models": {
        "qwen3.6-plus": {
          "name": "Qwen3.6 Plus",
          "options": {
            "thinking": {
              "type": "enabled",
              "budgetTokens": 2048
            }
          }
        },
        "deepseek-v3.2": {
          "name": "DeepSeek V3.2"
        }
      }
    }
  },
  "model": "bailian-payg/qwen3.6-plus",
  "small_model": "bailian-payg/deepseek-v3.2",
  "share": "disabled",
  "permission": {
    "edit": "ask",
    "bash": "ask"
  }
}
```

这里有 3 个初学者友好设置：

1. `apiKey` 从环境变量读取，避免泄露。
2. 默认模型用 `qwen3.6-plus`。
3. `edit` 和 `bash` 设置成 `ask`，AI 修改文件或运行命令前会先问你。

本仓库也提供了可复制版本：

```text
opencode/bailian-payg-opencode.example.json
```

## 9. 启动 OpenCode

进入你的课程项目目录，例如：

```powershell
cd "C:\Users\你的用户名\Desktop\我的课程项目"
opencode
```

进入 OpenCode 后，输入：

```text
/models
```

选择：

```text
阿里云百炼（学生权益按量）
```

再选择：

```text
Qwen3.6 Plus
```

或者：

```text
DeepSeek V3.2
```

## 10. 第一次测试怎么问

第一次不要直接说“帮我写完整项目”。

先问一个很小的问题：

```text
请只回复一句话：如果你能正常工作，请回答“OpenCode 已连接成功”。
```

如果能回答，再让它读项目：

```text
请先阅读当前项目结构，不要修改任何文件。
用中文告诉我：
1. 这个项目大概是做什么的；
2. 我应该先看哪 3 个文件；
3. 每个文件可能对应哪些课堂知识点。
```

## 11. 配合 CLASS-AI 使用

如果你要把它用于课堂实验，可以把本仓库的 OpenCode 指令放进项目根目录。

最简单做法：

1. 把这个文件复制到你的项目根目录：

```text
opencode/AGENTS.md
```

2. 然后对 OpenCode 说：

```text
请按 AGENTS.md 和 CLASS-AI 的方式带我完成课堂实验。
每次只问我一个问题。
先确认课程主题和老师要求，再生成最小可运行版本。
不要一上来生成大项目。
```

Windows 程序设计课可以补一句：

```text
本课程优先使用 Win32 / MFC / GDI / 标准 C++。
不要使用 Qt、Web 前端、Direct2D、OpenGL 等超出课程范围太多的技术。
```

## 12. 省钱用法

学生权益有限，建议这样用：

1. 一次只让 AI 读 1-3 个关键文件。
2. 先让 AI 输出计划，确认后再让它改代码。
3. 让 AI 每次只改一个小功能。
4. 报错时只贴关键错误，不要贴整个日志。
5. 不要把 `build/`、`node_modules/`、`.git/`、图片视频大文件放进要分析的范围。
6. 让 AI 多解释“为什么这样改”，少让它反复生成完整代码。
7. 课上演示时优先用短问题，避免多人同时长上下文调用。

## 13. 常见报错

### 13.1 OpenCode 找不到模型

检查：

1. `opencode.json` 是否放在 `C:\Users\<你的用户名>\.config\opencode\opencode.json`。
2. JSON 有没有少逗号、错引号。
3. `DASHSCOPE_API_KEY` 环境变量是否已经设置。
4. 设置环境变量后有没有重新打开 PowerShell。
5. 是否重启了 OpenCode。

### 13.2 401 / Unauthorized

通常是 API Key 问题：

1. Key 复制错了。
2. Key 没有设置到环境变量。
3. 用了别人的 Key 或已删除的 Key。
4. `opencode.json` 里的环境变量名字写错了。

### 13.3 403 / 权限不足

可能原因：

1. 百炼服务没有开通。
2. API Key 所属业务空间没有模型权限。
3. 当前账号或业务空间不可调用该模型。
4. 学生权益未领取或不可抵扣当前调用。

### 13.4 费用没有抵扣

先到费用中心检查：

```text
费用与成本
-> 卡券管理
-> 优惠券管理
-> 账单详情
```

注意：

1. 学生权益的适用范围以阿里云页面为准。
2. 部分产品、地域、模型、套餐可能不参与抵扣。
3. 如果超过权益额度，可能产生真实费用。
4. 老师组织课堂时，不建议让学生共用同一个 API Key。

### 13.5 Key 和 Base URL 混用

普通百炼按量计费：

```text
Key: sk-...
Base URL: https://dashscope.aliyuncs.com/apps/anthropic/v1
```

Coding Plan：

```text
Key: sk-sp-...
Base URL: https://coding.dashscope.aliyuncs.com/apps/anthropic/v1
```

这两套不要混用。

## 14. 如果你买的是 Coding Plan

普通学生先不要看这一节。只有你明确买了 Coding Plan，才用这个配置。

Coding Plan 的环境变量可以单独设置：

```powershell
[Environment]::SetEnvironmentVariable("BAILIAN_CODING_PLAN_API_KEY", "YOUR_SK_SP_API_KEY", [EnvironmentVariableTarget]::User)
```

配置文件示例在：

```text
opencode/bailian-coding-plan-opencode.example.json
```

Coding Plan 的关键区别：

```text
Key: sk-sp-...
Base URL: https://coding.dashscope.aliyuncs.com/apps/anthropic/v1
```

## 15. 给老师的课堂建议

如果老师想让全班用：

1. 先让学生各自完成阿里云学生认证，不要共用老师 Key。
2. 课前发这个教程和 `opencode/bailian-payg-opencode.example.json`。
3. 课堂上先做“连接成功测试”，不要直接开始大项目。
4. 要求学生保留 AI 交互记录。
5. 验收时让学生讲清楚：课堂知识点、AI 做了什么、自己改了什么、怎么验证。
6. 明确禁止提交完整 API Key 截图。

## 16. 一句话版

```text
学生去 university.aliyun.com 做学生认证并领取 300 元权益，
再去百炼控制台创建 sk- 开头 API Key，
把 Key 放到 DASHSCOPE_API_KEY 环境变量，
把 opencode.json 配成百炼按量计费，
最后在 OpenCode 里选择 Qwen 或 DeepSeek 模型。
```

## 参考官方文档

- 阿里云高校计划/云工开物：<https://university.aliyun.com/>
- 阿里云百炼 API Key：<https://help.aliyun.com/zh/model-studio/get-api-key>
- 阿里云百炼 OpenCode 接入：<https://help.aliyun.com/zh/model-studio/opencode>
- OpenCode 安装文档：<https://opencode.ai/docs/>
- OpenCode 配置文档：<https://dev.opencode.ai/docs/config>
