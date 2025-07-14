# Qwen2.5-VL-3B 奖励模型微调实验复现指南

本项目由MuGuang-L完成，作为腾讯犀牛鸟计划 `UnifiedReward` 项目的一部分。
本目录包含了复现我的《全参与LoRA对比分析实验报告》所需的所有代码、配置文件和详细说明。

## 目录结构

```markdown
├── EXPERIMENT_REPORT.md # 详细的图文实验报告，包含所有结论与分析
├── loss_figure/ # 存放训练Loss和验证Loss的静态图表
├── tensorboard_logs/ # 存放原始 TensorBoard 日志文件，支持本地交互式查看
├── 1_data_preparation/ # 存放所有数据和模型准备相关的脚本
├── 2_training_scripts/ # 存放全参和LoRA的训练配置文件
└── README.md # 您正在阅读的这份总说明文件
```
## 复现流程

**第一步：准备数据与模型**

所有数据和模型准备相关的脚本和详细说明位于 `1_data_preparation/` 目录下。请先进入该目录并按其说明操作，确保所有必要文件（如图片数据集和Qwen基座模型）都已准备就绪。

**第二步：开始训练**

`SFT`和`LoRA`的训练配置文件位于 `2_training_scripts/` 目录下。请在使用前，确保根据您的本地环境修改`.yaml`文件中的模型和数据路径。注意，所有的训练均在 llamafactory 框架下完成：

*   **运行SFT训练 (示例)**:
    ```bash
    llamafactory-cli train 2_training_scripts/qwen_3b_sft.yaml
    ```
*   **运行LoRA训练 (示例)**:
    ```bash
    llamafactory-cli train 2_training_scripts/qwen_3b_lora.yaml
    ```

**第三步：查看详细实验报告与训练日志**

*   **实验报告**: 所有实验的详细结果、图表和深度分析，请查阅根目录下的 `EXPERIMENT_REPORT.md` 文件。
*   **交互式训练日志**: 如果您想交互式地查看训练Loss、验证Loss等详细指标，可以参考 `tensorboard_logs/` 目录下的 `README.md` 文件，在本地启动 TensorBoard。
