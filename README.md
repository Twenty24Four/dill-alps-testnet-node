# Dill Alps 測試網節點
![image](https://github.com/user-attachments/assets/9233738b-93f7-49be-9410-0041f01e4bee)


# 验证器硬件要求
| 硬件 | 轻型验证器 | 完整验证器
| ------------- | ---------------- | ---------------- |
处理器 | 2 核 | 4 核
操作系统架构 | x86-64 (x64, x86_64, AMD64, and Intel 64) | x86-64 (x64, x86_64, AMD64, and Intel 64)
内存 | 2 GB | 8 GB
操作系统 | Ubuntu 22.04.2 或更高版本 (x86-64) | Ubuntu 22.04.2 或更高版本 (x86-64)
光盘大小 | 20 GB | 256 GB
网络带宽 | 1MB/s | 64Mb/s

# Dill 公共测试网（阿尔卑斯测试网）网络信息
| 网络名称     | Dill Testnet Alps |
| ------------- | ---------------- |
网络名称 | Alps Testnet
Rpc URL | https://rpc-andes.dill.xyz/
链条 ID | 102125
货币符号 | DILL
Explorer URL | https://andes.dill.xyz/




### 安装说明

1- 运行以下命令
```ABNF
curl -sO https://raw.githubusercontent.com/DillLabs/launch-dill-node/main/dill.sh  && chmod +x dill.sh && ./dill.sh
```
2- 开始安装后，您将看到 ```Please choose an option for your purpose [1, Launch a new dill node, 2, Add a validator to existing node]```。在此处写入 1，然后按回车键。

3- 它会开始下载必要的文件。```Step 1 Completed. Press any key to continue...```得到输出后，按任意键继续。

4- 在安装过程中，我们会看到 “记忆法 ”部分。 如果您要创建新的记忆法，请选择 1；如果您要使用 Andres 测试网中的记忆法，请选择 2 并按回车键。不要忘记保存您的单词。您还可以在```dill/validator_keys/mnemonic-xxxxxx.txt```目录下的这个文件中查看您的助记词。

> [!］
> 不要忘记备份 ```dill/validator_keys/mnemonic-xxxxxx.txt``` 文件。如果要将节点转移到另一台服务器上，则需要备份该文件。

5- 创建助记符后，您的 Validator Keystore 密码将随机生成。也请保存。同样，您可以在 ```dill/validator_keys/keystore_password.txt``` 文件中看到随机生成的密码。再次按任意键。

6- 完整验证器和轻型验证器安装的令牌赌注金额不同。为此，您将看到以下选项：```Please choose an option for deposit token amount [1, 3600, 2, 36000]```如果您选择的是轻型验证器，请键入 1；如果您选择的是完整验证器，请键入 2，然后按回车键。

7- 在这一步，```Please enter your withdrawal address:```选项将会出现。请输入您的地址 2 次，即您在 Dill Discord 的龙头中申请代币的地址。

8- ```Step 2 Completed. Press any key to continue...```当你得到输出时，再次按任意键继续安装。

9- 最后，当安装顺利完成后，会输出```node running, congratulations```。它还会在输出中给出你的 validator_pubkey。


## 加密

1- 首先，在 Alps 频道向龙头机器人申请一个代币（$request 是你的钱包地址）。请使用与您在节点中创建的钱包不同的钱包。

2- 访问 https://staking.dill.xyz/。

> 注意
> 建议在节点同步后再执行定投操作。请使用 repo 底部的命令检查节点的同步状态。
> 请注意，您只能向 Faucet 申请一次令牌！

[图片](https://github.com/user-attachments/assets/3c24ea5d-c728-4ee7-87f3-b2a42abd5dd5)

3- 您将把```deposit_data-xxxxx.json```文件上传到该网站。您可以从服务器上的 ```/dill/validator_keys``` 目录中找到并获取该文件（您可以使用 WinSCP、Mobaxterm 等应用程序）。

4- 将```Deposit_data-xxxx.json``文件上传到网站后，点击连接到 MetaMask，确保有足够的测试令牌（>3600 DILL）

![image](https://github.com/user-attachments/assets/f8238c5a-b216-476c-a5a3-18fc919211b6)

5- 连接钱包后，按 Continue（继续）继续。然后按 ```Confirm Deposit``` 键存入代币。

![Ekran görüntüsü 2024-09-14 075934](https://github.com/user-attachments/assets/8f9bcb6a-ddfd-41cf-b202-fc99e5bba489)

6- 完成入金流程后，您可以使用验证器公钥在页面上搜索验证器信息。您的验证器可能需要 30 分钟到 1 小时才能出现。

![Ekran görüntüsü 2024-09-14 080323](https://github.com/user-attachments/assets/1539f0ca-324c-4188-97ea-a279b50d28ab)


## 重要命令

- 如果您不在 Dill 目录中，可以使用此命令切换到 Dill 目录（您需要在 “dill ”目录下运行命令）
```ABNF
cd dill 
```

- 检查节点是否正在运行
```Processing
./health_check.sh -v
```
- 检查节点是否同步。如果输出如下，则说明节点已同步。
  ({“head_slot”: “173420”, “sync_distance”: “0”, “is_syncing”:false, “is_optimistic”:false, “el_offline”:false}}
```ABNF
curl -s localhost:3500/eth/v1/node/syncing
```
