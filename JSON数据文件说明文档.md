# 数据文件说明文档

### 一、概述

本文档详细说明了上传的JSON数据文件结构、内容格式和使用方法，专为与AI大语言模型交流而设计。

### 二、数据文件说明

#### 1. K线技术指标组合数据 (CombinedDataPoint)
**文件名示例**: `CombinedDataPoint_BTC-USDT-SWAP_1D_20250619_135140.json`

**数据内容**: K线基础数据 + 全套技术指标

**字段说明**:

- **基础K线**: `Open`, `High`, `Low`, `Close`, `Volume` (开高低收量)
- **移动平均线**: `MA5`, `MA10`, `MA20` (5日、10日、20日简单移动平均)
- **布林带**: `BollUpper`, `BollMiddle`, `BollLower` (上轨、中轨、下轨)
- **MACD**: `DIF`(快线), `DEA`(慢线), `MACD`(柱状图)
- **KDJ**: `K`, `D`, `J` (随机指标)

#### 2. 合约多空持仓人数比 (ContractLongShortAccountRatio)
**文件名示例**: `BTC_ContractLongShortAccountRatio_1D_20250619_135718.json`

**数据含义**: 交割永续净开多持仓用户数与净开空持仓用户数的比值

**字段说明**:

- `Timestamp`: Unix时间戳(毫秒)
- `LongShortAccountRatio`: 多空人数比 (>1表示开多人数多于开空)
- `DateTime`: 北京时间格式(UTC+8)

#### 3. 合约持仓量及交易量 (ContractOpenInterestVolume)
**文件名示例**: `BTC_ContractOpenInterestVolume_1D_20250619_135719.json`

**数据含义**: 交割永续合约的持仓量和交易量数据

**字段说明**:

- `OpenInterest`: 持仓总量(USD)
- `Volume`: 交易总量(USD)

#### 4. 合约主动买入/卖出情况 (ContractTakerVolume)
**文件名示例**: `BTC_ContractTakerVolume_1D_20250619_135720.json`

**数据含义**: taker主动买入和卖出的交易量

**字段说明**:

- `SellVolume`: 主动卖出量
- `BuyVolume`: 主动买入量
- `BuySellRatio`: 买卖比(BuyVolume/SellVolume, >1表示买盘更强)

#### 5. 永续合约历史资金费率 (PerpetualFundingRate)
**文件名示例**: `BTC_PerpetualFundingRateHistory_1D_20250619_135720.json`

**数据含义**: 永续合约资金费率历史数据

**字段说明**:

- `InstrumentId`: 产品ID
- `FundingRate`: 资金费率(正数表示多头支付空头)
- `RealizedRate`: 实际历史资金费率

#### 6. 精英交易员合约多空持仓人数比 (EliteTraderAccountRatio)
**文件名示例**: `BTC_EliteTraderAccountRatio_1D_20250619_135721.json`

**数据含义**: 持仓价值前5%的精英交易员多空持仓人数比

**字段说明**:

`LongShortAccountRatio`: 精英交易员多空持仓人数比

#### 7. 精英交易员合约多空持仓仓位比 (EliteTraderPositionRatio)
**文件名示例**: `BTC_EliteTraderPositionRatio_1D_20250619_135722.json`

**数据含义**: 精英交易员开多、开空仓位占总持仓的比值

**字段说明**:

`LongShortPositionRatio`:  精英交易员开多、开空仓位占总持仓的比值

### 三、时间处理规范

**提醒：**分析时数据文件时，忽略Timestamp，以DateTime（已转换为北京时间）字段为准。

### 四、数据分析重点

- **技术分析**: 使用CombinedDataPoint文件的技术指标
- **市场情绪**: 关注多空比例数据(LongShortAccountRatio)
- **资金流向**: 分析主动买卖量(ContractTakerVolume)
- **持仓变化**: 观察持仓量变化(ContractOpenInterestVolume)
- **精英行为**: 参考精英交易员数据判断大户动向

