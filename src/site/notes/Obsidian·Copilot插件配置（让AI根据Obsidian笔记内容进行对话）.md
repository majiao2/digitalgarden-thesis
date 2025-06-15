---
{"dg-publish":true,"permalink":"/Obsidian·Copilot插件配置（让AI根据Obsidian笔记内容进行对话）/","dgPassFrontmatter":true,"created":"2025-06-08T22:10:32.753+08:00"}
---


## 安装： 

Obsidian的“第三方插件”搜索Copilot。

首先准备好API keys，使用[硅基流动][Link 1]的API keys（填写邀请码`XDSDxSXR`可彼此赠送2000万Tokens）

## 配置： 

（1）Model选项卡（配置Chat Model）  
![73cd182094884bde575aae48200d003d_MD5.png](/img/user/73cd182094884bde575aae48200d003d_MD5.png)

1.  选择“Add Custom Model”，填写信息（如下图）：
    
     *  Model Name：deepseek-ai/DeepSeek-V3（也可以在“模型广场”中选择不同模型进行尝试使用）
     *  Provider：OpenAI Format
     *  Base URL：https://api.siliconflow.cn/v1
     *  API Key填入刚刚准备好的
2.  点击Verify，右上角显示Successful即可，点击Add Model  
    ![d9aa9b0699e70db1ba5b07c236412172_MD5.png](/img/user/d9aa9b0699e70db1ba5b07c236412172_MD5.png)

（2）Model选项卡（配置Embedding Model）  
![5540ce3df51013884bdee8931593137b_MD5.png](/img/user/5540ce3df51013884bdee8931593137b_MD5.png)

1.  选择“Add Custom Model”，填写信息：
    
     *  Model Name：BAAI/bge-m3（也可以在“模型广场”中选择不同模型进行尝试使用）
     *  Provider：OpenAI Format（和前面一样）
     *  Base URL：https://api.siliconflow.cn/v1（和前面一样）
     *  API Key填入刚刚准备好的（和前面一样）
2.  点击Add Model  
    ![cacdc0c9dd9df5ab04159f41bc56bc08_MD5.png](/img/user/cacdc0c9dd9df5ab04159f41bc56bc08_MD5.png)

（3）Basic选项卡

1.  Default Chat Model和Embedding Model分别选择刚刚添加的模型  
    ![ff3c7264451aedfc3947436564e4d6d6_MD5.png](/img/user/ff3c7264451aedfc3947436564e4d6d6_MD5.png)
2.  此时会进入Copilot is indexing your valut阶段（必须要有）  
    ![fcdd63f24f4a197ab37c05d0a52082b8_MD5.png](/img/user/fcdd63f24f4a197ab37c05d0a52082b8_MD5.png)  
    检索完毕后，在obsidian主页面，快捷键 Ctrl+p：找到“Copilot: Open Copilot Chat Window”。  
    ![93056efbfa1b09c8946a562d4a2f9bcf_MD5.png](/img/user/93056efbfa1b09c8946a562d4a2f9bcf_MD5.png)

选择value QA，即可进行QA对话（AI根据obsidian笔记内容进行对话）  
![caeb204d9e5144878f65a4749ca7f08f_MD5.png](/img/user/caeb204d9e5144878f65a4749ca7f08f_MD5.png)


[Link 1]: https://cloud.siliconflow.cn/