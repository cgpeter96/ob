#代码生成 #LLM


## 论文要点
link: https://huggingface.co/bigcode
- 数据规模:1000B tokens 
- 模型规模: 15B
	- 针对35B token python数据 对StarCoderBase进行微调 （a.k.a, StarCoder）
	- 更长的输入,多轮对话
	- 自动代码补全，根据指令修改代码，
- 安全问题
	- PPI(Personally Identiiable Information)编辑流水线
	- 归因跟踪工具（attribution tracing tool）
- 评估细节
	- 为了强制模型生成一个实际的解决方案，我们添加了提示词 `<filename>solutions/solution_1.py\n# Here is the correct implementation of the code exercise`。（但对性能影响不大）

## 实验&评估
### baselines
- PaLM
- LaMDA
- LLaMA
- CodeGen-16B-Mono
- code-cushman-001(openai, 12B)
### 训练数据
该模型是在 The Stack 1.2 的一个子集上训练的。该数据集(https://huggingface.co/spaces/bigcode/in-the-stack)仅包含许可代码，它还包含一个退出流程，以便代码贡献者可以从数据集中删除他们的数据

https://github.com/bigcode-project/bigcode-dataset
### 评估数据
- HumanEval :比较流行的 Python 基准测试，它主要测试模型是否可以根据函数的签名和文档来编写函数
- MBPP：  1000个众包python编程问题
- MultiPL-E：  是 HumanEval 的多语言扩展版。
- DS-1000 ：数据科学基准测试（python）

### 实验结果
![[Pasted image 20231109172115.png]]
可以看到 starcoder性能还是不错的 可以称之为SOTA

### 技术经理
设计了一套技术经理prompt：https://huggingface.co/datasets/bigcode/ta-prompt?row=0


## 参考
- [论文](https://drive.google.com/file/d/1cN-b9GnWtHzQRoE7M7gAEyivY0kl4BYs/view): 关于 StarCoder 的技术报告。
- [GitHub](https://github.com/bigcode-project/starcoder/tree/main): 你可以由此获得有关如何使用或微调 StarCoder 的所有信息。
- [StarCoder](https://huggingface.co/bigcode/starcoder): 基于 Python 数据集进一步微调 StarCoderBase 所得的模型。
- [StarCoderBase](https://huggingface.co/bigcode/starcoderbase): 基于来自 The Stack 数据集的 80 多种编程语言训练而得的模型。
- [StarEncoder](https://huggingface.co/bigcode/starencoder): 在 The Stack 上训练的编码器模型。
- [StarPii](https://huggingface.co/bigcode/starpii): 基于 StarEncoder 的 PII 检测器。



