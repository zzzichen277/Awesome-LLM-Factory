#### 微调经验



#### 微调数据

1.self-instruct：https://github.com/yizhongw/self-instruct

Self-Instruct是一个框架，帮助语言模型提高其遵循自然语言指令的能力。它通过利用模型自身生成的内容来创建大量的指令数据。借助Self-Instruct，可以在不依赖大量人工标注的情况下，提高语言模型的指令遵循能力。



#### 微调理论
1.大模型微调（finetune）方法总结-LoRA,Adapter,Prefix-tuning，P-tuning，Prompt-tuning

https://zhuanlan.zhihu.com/p/636481171

2.一篇关于LLM指令微调的综述
https://mp.weixin.qq.com/s/mpajhoPQ7WQh_2Saw_hOPg

这一小节主要介绍使用指令调优的pipeline。

指令数据集的构造：
指令数据集中的每个实例由三个元素组成:一个指令，它是指定任务的自然语言文本序列(例如，为XX写一封感谢信给XX，写一篇关于XX主题的博客，等等)；为上下文提供补充信息的可选输入；以及基于指令和输入的预期输出。

通常构造指令数据集有两种方法：
1.来自带注释的自然语言数据集的数据集成。在这种方法中，通过使用模板将文本标签对转换为(INSTRUCTION, PUT)对，从现有的带注释的自然语言数据集中收集INSTRUCTION, TPUT)对。Flan和P3数据集是基于数据集成策略构建的。
2.使用LLM生成输出:使用诸如GPT-3.5-Turbo或GPT4之类的LLM收集输出。指令可以来源于人工收集或基于使用LLM的少量手写指令进行扩展。接下来，将收集到的指令馈送到LLM以获得输出。使用这种方法生成了instructwind和self - directive等数据集。
对于多回合会话IT数据集，可以让LLM扮演不同的角色(用户和AI助手)来生成会话格式的消息。

指令微调：
基于收集到的IT数据集，可以以完全监督的方式直接对预训练模型进行调优，在给定指令和输入的情况下，通过顺序预测输出中的每个标记来训练模型。
