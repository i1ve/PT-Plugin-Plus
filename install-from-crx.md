# 从 `crx` 安装与更新

## 写在安装之前
- 仅部分浏览器支持该格式安装；
- `Google Chrome 73` 之后的版本以及 `Edge` 如需安装 `crx` 包，请先添加白名单（仅适用于 `Windows` ），否则会出现 `该扩展程序未列在 Chrome 网上应用店中，并可能是在您不知情的情况下添加的。` 的提示，并且无法正常使用，如下图所示：

  ![](images/chrome_2019-12-23_15-31-23.png)
## Win
- 添加白名单方法如下：
  - 以管理员身份开启一个 `cmd` 或者 `Powershell` 命令行窗口；
  - 执行以下代码：
    # Google
    ```bat
    reg add HKLM\SOFTWARE\Policies\Google\Chrome\ExtensionInstallAllowlist /v 99999 /t reg_sz /d dmmjlmbkigbgpnjfiimhlnbnmppjhpea /f 
    ```
    # Edge
    ```bat
    reg add HKLM\SOFTWARE\Policies\Microsoft\Edge\ExtensionInstallAllowlist /v 99999 /t reg_sz /d dmmjlmbkigbgpnjfiimhlnbnmppjhpea /f 
    ```
  - 或将以下内容保存为 `addWhitelist.reg` 文件，然后双击导入注册表：
    ```
    Windows Registry Editor Version 5.00
    
    [HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Google\Chrome\ExtensionInstallAllowlist]
    "99999"="dmmjlmbkigbgpnjfiimhlnbnmppjhpea"
    [HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Edge\ExtensionInstallAllowlist]
    "99999"="dmmjlmbkigbgpnjfiimhlnbnmppjhpea"
    ```

  - 其中 
    - `99999` 可改成任意 `数字` ；
      - 如之前添加过其他白名单，请确认该内容不要重复！
    - `dmmjlmbkigbgpnjfiimhlnbnmppjhpea` 为固定值，是助手打包 `crx` 所生成的值，不能更改；
  - 执行完成后，重新启动 `Chrome` 浏览器；
  - 此时浏览器菜单会多出一个菜单 `由贵单位管理`，如下图所示：

    ![](images/2019-12-23_15-22-12.png)

  - 同时在 `chrome://extensions/` 页面会多出以下文本：

    ![](images/chrome_2019-12-23_15-25-45.png)
  
  - 此时即可按以下步骤正常安装和使用 `crx` 包，并且不再出现 `该扩展程序未列在 Chrome 网上应用店中` 之类的提示；
## Mac
见这里
https://github.com/ronggang/PT-Plugin-Plus/discussions/1066
## 如何安装
1. 下载 `crx` 包

   - 打开 https://github.com/ronggang/PT-Plugin-Plus/actions 
   - 下载对应的版本的 `crx` 包文件，如 `PT-Plugin-Plus.v1.4.4.crx` ；

2. 安装 `crx` 包
   - 在浏览器里打开 `扩展程序` 或在地址栏中输入：`chrome://extensions/` 回车，进入扩展程序；
   - 将 `crx` 包拖放到浏览器；
     - 如果无法正常拖放，请 `chrome://extensions/` 页面打开 `开发者模式`；
   - 如果浏览器支持 `crx` 包，则会自动安装；如果不支持则会报错；
   - 安装完成后，即可使用。

## 如何更新
- 该方式一般情况为自动更新，只要网络环境可以正常访问 `https://raw.githubusercontent.com/ronggang/PT-Plugin-Plus/master/update/index.xml` 页面，即可在新版本发布后自动更新；
- 如果网络不通畅，也可下载最新的 `crx` 包，重新 `安装` 一遍即可；