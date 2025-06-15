---
{"dg-publish":true,"dg-home":"false","permalink":"/Obsidian·Copilot插件配置（让AI根据Obsidian笔记内容进行对话）/","tags":["gardenEntry"],"dgPassFrontmatter":true,"created":"2025-06-08T22:10:32.753+08:00"}
---


## 安装： 

Obsidian的“第三方插件”搜索Copilot。

首先准备好API keys，使用[硅基流动][Link 1]的API keys（填写邀请码`XDSDxSXR`可彼此赠送2000万Tokens）

## 配置： 

（1）Model选项卡（配置Chat Model）  
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/81c6184403dd41949c8ee9e6c4acd749.png)

1.  选择“Add Custom Model”，填写信息（如下图）：
    
     *  Model Name：deepseek-ai/DeepSeek-V3（也可以在“模型广场”中选择不同模型进行尝试使用）
     *  Provider：OpenAI Format
     *  Base URL：https://api.siliconflow.cn/v1
     *  API Key填入刚刚准备好的
2.  点击Verify，右上角显示Successful即可，点击Add Model  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/cac7a0305655403a857012c1e1bef391.png)

（2）Model选项卡（配置Embedding Model）  
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/f73598c21b0f4574b45a99a4c08addf3.png)

1.  选择“Add Custom Model”，填写信息：
    
     *  Model Name：BAAI/bge-m3（也可以在“模型广场”中选择不同模型进行尝试使用）
     *  Provider：OpenAI Format（和前面一样）
     *  Base URL：https://api.siliconflow.cn/v1（和前面一样）
     *  API Key填入刚刚准备好的（和前面一样）
2.  点击Add Model  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/7005ebae2fa4422f89fd4d3aa68682ca.png)

（3）Basic选项卡

1.  Default Chat Model和Embedding Model分别选择刚刚添加的模型  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/fefdaf4e0fe245e5bca4204d36adbad0.png)
2.  此时会进入Copilot is indexing your valut阶段（必须要有）  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/b65ee8310995469786cd865703a2f30e.png)  
    检索完毕后，在obsidian主页面，快捷键 Ctrl+p：找到“Copilot: Open Copilot Chat Window”。  
    ![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/87cac429d5d84a84a83629b6bd7708fa.png)

选择value QA，即可进行QA对话（AI根据obsidian笔记内容进行对话）  
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/8e2d207d3fa34280859ae96ffce10689.png)


[Link 1]: https://cloud.siliconflow.cn/