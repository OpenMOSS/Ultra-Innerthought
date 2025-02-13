<div align="right">
    <a href="README.md">English</a> | <a href="README_zh.md">中文</a>
</div>

# Ultra-Innerthought🤔

[![Hugging Face](https://img.shields.io/badge/🤗%20Hugging%20Face-Ultra--Innerthought-blue)](https://huggingface.co/datasets/fnlp/Ultra-Innerthought)

## Introduction
Ultra-Innerthought is a bilingual (Chinese and English) open-domain SFT dataset in Innerthought format, containing 2,085,326 dialogues. Unlike current reasoning datasets that mainly focus on mathematics and coding domains, Ultra-Innerthought covers a broader range of fields and includes both Chinese and English languages. We used Deepseek V3 as the model for data synthesis.

## Dataset Format
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

## Data Synthesis
Ultra-Innerthought uses the following SFT datasets as raw input and employs Deepseek V3 for data synthesis. We preserved the user input from each round of the original datasets, using Deepseek V3 to first generate a model's Inner thought, and then generate the final response based on that Inner thought. When generating the model's Inner thought, we prompted the model to perform intent clarification, problem decomposition, self-reflection, exploration, and other behaviors. The dataset has approximately a 1:1 ratio of Chinese to English content.

### User Input Sources
User inputs are sampled from [OpenHerms2.5](https://huggingface.co/datasets/teknium/OpenHermes-2.5) and its Chinese version translated by Deepseek V3, [QwQ-LONGCOT-500K](https://huggingface.co/datasets/PowerInfer/QWQ-LONGCOT-500K) and its Chinese version translated by Deepseek V3, [tulu-3-sft-mixture](https://huggingface.co/datasets/allenai/tulu-3-sft-mixture), [sharegpt-zh](https://huggingface.co/datasets/kimnt93/zh-sharegpt), [COIG-CQIA](https://huggingface.co/datasets/m-a-p/COIG-CQIA), [Wildchat](https://huggingface.co/datasets/allenai/WildChat-1M), [WizardLM](https://huggingface.co/datasets/WizardLMTeam/WizardLM_evol_instruct_70k), Moss-inhouse-data, [lmsys](https://huggingface.co/datasets/lmsys/lmsys-chat-1m).