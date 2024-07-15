## serv00与ct8自动化批量保号，每3天自动登录一次面板，并且发送消息到Telegram

利用github Action以及python脚本


### 将代码fork到你的仓库并运行的操作步骤

#### 1. Fork 仓库

1. **访问原始仓库页面**：
    - 打开你想要 fork 的 GitHub 仓库页面。

2. **Fork 仓库**：
    - 点击页面右上角的 "Fork" 按钮，将仓库 fork 到你的 GitHub 账户下。

#### 2. 设置 GitHub Secrets

1. **创建 Telegram Bot**
    - 在 Telegram 中找到 `@BotFather`，创建一个新 Bot，并获取 API Token。
    机器人创建步骤如下，发送/newbot,在返回消息后输入你的机器人名字例如test，然后再输入一个机器人ID,例如testbot,注意名字后面必须带有bot字样，然后会返回你的机器人地址和api，请记住这个API，稍后会用到。
    - 获取到你的 Chat ID 方法，在telegram中找到‘@getmyid_bot’机器人，发送‘/start’，返回用户信息中那串数字就是你的id

2. **配置 GitHub Secrets**
    - 转到你 fork 的仓库页面。
    - 点击 `Settings`，然后在左侧菜单中选择 `Secrets`。
    - 添加以变量：
  变量1中内容

          [
            {"username": "serv00的账号01", "password": "serv00的密码01", "panel": "panel6.serv00.com"},
            {"username": "serv00的账号02", "password": "serv00的密码02", "panel": "panel6.serv00.com"},
          ]


添加信息如下：
新增变量1   变量名称   ACCOUNTS_JSON     内容拷贝上方信息，其中username为你的账户名称，password为你的账户密码   panel为你的登录页面地址，这些信息在你注册后的邮件内容里。

请注意，上面示例中，一共两个，如果你只有一个账户，那么请删除一行，注意每行后的逗号。

新增变量2   变量名称   TELEGRAM_BOT_TOKEN     写入你的bot API

新增变量3  变量名称   TELEGRAM_CHAT_ID        写入你的账户ID

#### 3. 启动 GitHub Actions

1. **配置 GitHub Actions**
    - 在你的 fork 仓库中，进入 `Actions` 页面。
    - 如果 Actions 没有自动启用，点击 `Enable GitHub Actions` 按钮以激活它。

2. **运行工作流**
    - GitHub Actions 将会根据你设置的定时任务（例如每三天一次）自动运行脚本。
    - 如果需要手动触发，可以在 Actions 页面手动运行工作流。

### 注意事项

- **保密性**: Secrets 是敏感信息，请确保不要将它们泄露到公共代码库或未授权的人员。
- **更新和删除**: 如果需要更新或删除 Secrets，可以通过仓库的 Secrets 页面进行管理。

通过以上步骤，你就可以成功将代码 fork 到你的仓库下并运行它了。如果需要进一步的帮助或有其他问题，请随时告知！
