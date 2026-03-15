# 🧪 EXP-XXX — [实验名称]

**日期**: YYYY-MM-DD   
**关联会议**: [YYYY-MM-DD 周会](../meetings/YYYY-MM-DD.md)  
**状态**: 🟡 进行中 / 🟢 完成 / ❌ 放弃

---

## 假设

> 一句话：这个实验想验证什么？

_[例：使用 mixup 数据增强（α=0.2）可以降低模型在验证集上的过拟合程度]_

---

## 配置

**关键配置变量**
- 变量1:
- 变量2:

**对照实验**: [EXP-004](./EXP-004.md)

其他配置：exp_config_XXX(./EXP-Config-XXX.md)

**运行命令 / 代码版本**:
> 为了方便代码管理和复现，建议加入
```bash
python train.py --config configs/exp003.yaml --seed 42
# git commit: abc1234
```

---

## 结果

1. 尽可能使用表格
2. 如果需要使用图表，则一定加上实验内容+关键observation的caption

<!-- CSV 友好格式，方便复制给 LLM 分析 -->

| 指标 | EXP-003 (本次) | EXP-002 (对照) | 变化 |
|------|---------------|---------------|------|
| Val Acc | 74.4% | 73.1% | +1.3% |
| Val Loss | 0.31 | 0.35 | -11% |
| Train-Val Gap | 4.2% | 6.8% | -38% ✅ |
| 训练时长 | 198 min | 195 min | ≈持平 |

### 图表

![训练曲线](../assets/EXP-003-curves.png)  
*caption: 左:训练loss，右:验证acc。蓝=EXP-003，橙=EXP-002。EXP-003在epoch15后过拟合明显减弱。*

![混淆矩阵](../assets/EXP-003-confusion.png)  
*caption: EXP-003 混淆矩阵。class 3（cat）依然是最弱类，F1=0.41，其余类均>0.70。*

---

## 结论

> 一句话：假设是否成立？结果说明了什么？

_[例：假设成立。mixup 显著减少过拟合（train-val gap 下降 38%），但 class 3 的弱表现揭示了类别不平衡问题，这是下一步需要解决的瓶颈。]_

---

## 后续

- **直接触发**: [EXP-004](./EXP-004.md) — 加入 weighted sampler 处理类别不平衡
- **待确认**: focal loss 是否比 weighted sampler 更有效（见周会讨论）
- **搁置**: cutout 增强（优先级降低）
