
---

## 📄 README.md 完整内容

```markdown
# 双均线量化交易策略 - 智能体做投资

## 📌 项目简介

本项目为人工智能通识课实践项目，主题为“智能体做投资”。使用**双均线策略**构建了一个自动化的股票交易智能体，在掘金量化平台上进行回测验证。

**策略逻辑**：当5日均线上穿20日均线时买入（金叉），下穿时卖出（死叉）

---

## 🎯 项目目标

- 用数学模型替代主观判断，实现自动化交易决策
- 验证双均线策略在A股市场的有效性
- 通过回测分析策略的收益、风险及适用边界

---

## 🛠️ 技术栈

| 项目 | 说明 |
|------|------|
| 平台 | 掘金量化 (MyQuant) |
| 语言 | Python 3.13 |
| SDK | gm 3.0.183 |
| 回测周期 | 2023-01-01 至 2023-12-31 |
| 初始资金 | 100,000 元 |
| 交易标的 | 平安银行 (SZSE.000001) |

---

## 📁 项目结构

```
/
├── main.py              # 策略主程序
├── backtest_report/     # 回测结果截图
│   ├── equity_curve.png     # 收益曲线图
│   ├── metrics.png          # 关键指标表
│   └── trade_records.png    # 交易记录
├── README.md           # 项目说明
└── requirements.txt    # 依赖环境（如有）
```

---

## 🔑 核心代码

```python
def on_bar(context, bars):
    # 获取历史收盘价
    hist = history(symbol=symbol, frequency='1d', 
                   start_time=start_date, end_time=end_date,
                   fields='close', df=True)
    
    # 计算均线
    short_ma = hist['close'][-5:].mean()
    long_ma = hist['close'][-20:].mean()
    
    # 金叉买入
    if short_ma > long_ma and not has_position:
        order_percent(symbol, percent=1, side=OrderSide_Buy,
                      order_type=OrderType_Market, position_effect=PositionEffect_Open)
    
    # 死叉卖出
    elif short_ma < long_ma and has_position:
        order_percent(symbol, percent=1, side=OrderSide_Sell,
                      order_type=OrderType_Market, position_effect=PositionEffect_Close)
```

---

## 📊 回测结果

| 指标 | 数值 |
|------|------|
| 总收益率 | [填写你的结果] |
| 年化收益率 | [填写你的结果] |
| 最大回撤 | [填写你的结果] |
| 夏普比率 | [填写你的结果] |
| 交易次数 | 12次（6买6卖） |

> 💡 具体数值请查看回测报告截图

---

## 📈 收益曲线

![收益曲线](./backtest_report/equity_curve.png)

---

## 🔍 策略分析

### 优点
- 规则明确，易于理解和实现
- 能捕捉中期趋势，避免频繁交易
- 回测中成功执行了完整的买卖信号

### 不足
- 震荡市中容易产生假信号
- 均线参数对结果敏感
- 未加入止损/止盈条件

---

## 🚀 改进方向

- [ ] 加入移动止损条件
- [ ] 对比不同均线周期（10/30、20/60）
- [ ] 结合成交量过滤假信号
- [ ] 增加多股票组合分散风险

---

## 📝 如何运行

1. 注册掘金量化平台：https://www.myquant.cn/
2. 下载掘金量化终端（Windows）
3. 安装 Python SDK
4. 将本仓库的 `main.py` 复制到策略编辑器
5. 填入你的 `strategy_id` 和 `token`
6. 运行回测

---

## 👤 作者

[刘家泽]  
人工智能通识课 | [智251/2025311860]

---

## 📅 完成时间

2026年6月

```

---

## 📋 使用说明

1. **复制**上面的内容
2. 在 GitHub 仓库中新建一个 `README.md` 文件
3. **粘贴**进去
4. 把 `[填写你的结果]` 替换成你的实际回测数据
5. 把 `[你的姓名]` 和 `[班级/学号]` 改成你自己的信息

```
backtest_report/
├── equity_curve.png   (收益曲线图)
├── metrics.png        (关键指标表)
└── trade_records.png  (交易记录截图)
```
<img width="3200" height="1904" alt="5a540abaf78a875b7cffc704afe7772b" src="https://github.com/user-attachments/assets/1f4d3ac9-d0e0-4675-9bd5-7ffbb138938b" />
<img width="3200" height="1904" alt="a33cb3fa313b3644704dc3df7bb0cc47" src="https://github.com/user-attachments/assets/9abc2d0d-be9f-4cef-9e26-71a017af3aa2" />
<img width="3200" height="1904" alt="1014cfe482dc3c361a1cc0032a69917b" src="https://github.com/user-attachments/assets/06cba50f-583b-4b66-accc-6d108f1122d1" />
