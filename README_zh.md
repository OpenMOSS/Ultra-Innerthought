# Ultra-Innerthought🤔

[![Hugging Face](https://img.shields.io/badge/🤗%20Hugging%20Face-Ultra--Innerthought-blue)](https://huggingface.co/datasets/fnlp/Ultra-Innerthought)

<div align="left">
    <a href="README.md">English</a> | <a href="README_zh.md">中文</a>
</div>

## 简介
Ultra-Innerthought是一个中英双语的开放领域的Innerthought格式的SFT数据集，包含2,085,326个对话。不同于当前主要关注数学和代码领域的推理数据集，Ultra-Innerthought覆盖了更多的领域，并包含中文和英文两个语种。我们使用了Deepseek V3作为数据合成的模型。

## 数据集格式
```json
{
    "id": "dialogue_id",
    "conversations": [
        {
            "user": "user_input",
            "inner_thought": "model's inner thought",
            "assistant": "model_output"
        },
        ...
    ],
    "data_source": "data_source"
}
```

## 数据合成
Ultra-Innerthought使用下列的SFT数据集作为原始输入，使用Deepseek V3进行数据合成。我们保留了原始数据集每一轮的用户输入部分，使用Deepseek V3首先生成一个模型的Inner thought，然后再使用Deepseek V3基于Inner thought生成最终的回复。在生成模型的Inner thought时，我们通过prompt的方式要求模型进行意图澄清，问题分解，自我反思，探索等行为。数据集中英文占比约1:1.

### 用户输入来源
用户输入采样自[OpenHerms2.5](https://huggingface.co/datasets/teknium/OpenHermes-2.5)以及我们使用Deepseek V3翻译的OpenHerms2.5中文版本，[QwQ-LONGCOT-500K](https://huggingface.co/datasets/PowerInfer/QWQ-LONGCOT-500K)以及我们使用Deepseek V3翻译的QwQ-LONGCOT-500K中文版本，[tulu-3-sft-mixture](https://huggingface.co/datasets/allenai/tulu-3-sft-mixture)，[sharegpt-zh](https://huggingface.co/datasets/kimnt93/zh-sharegpt)，[COIG-CQIA](https://huggingface.co/datasets/m-a-p/COIG-CQIA)，[Wildchat](https://huggingface.co/datasets/allenai/WildChat-1M)，[WizardLM](https://huggingface.co/datasets/WizardLMTeam/WizardLM_evol_instruct_70k)，Moss-inhouse-data, [lmsys](https://huggingface.co/datasets/lmsys/lmsys-chat-1m).