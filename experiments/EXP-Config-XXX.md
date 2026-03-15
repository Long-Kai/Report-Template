# 实验配置_XXX

| 参数 | 值 | 说明 |
|------|----|------|
| 模型 | ResNet-50 | 骨干网络 |
| batch_size | 64 | 显存限制 |
| 学习率 | 0.001 | Adam 优化器 |
| epochs | 50 | early stopping patience=10 |
| 增强 | mixup α=0.2 | 核心变量 |
| 数据集 | CIFAR-10 | 标准划分 |
| 对照组 | EXP-002 | 仅去掉 mixup |