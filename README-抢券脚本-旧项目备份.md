# 自动抢券脚本

基于 `uiautomator2` 实现的安卓手机自动抢券工具。

## 功能特点

- 无需手机安装APP，仅需电脑和USB线连接
- 支持定时任务
- 自动打开淘宝并查找抢券按钮
- 支持多种点击策略
- 完整日志记录

## 环境要求

- Python 3.7+
- 安卓手机（需开启 USB 调试）
- USB 数据线（或无线连接）

## 安装步骤

### 1. 准备手机端

1. 打开手机 **设置 → 关于手机**
2. 连续点击 **版本号** 7次，开启开发者模式
3. 返回设置，进入 **开发者选项**
4. 打开 **USB调试**（部分手机需要开启 USB调试（安全设置））

### 2. 安装依赖

```bash
# 激活虚拟环境（如使用）
source .venv/bin/activate

# 安装依赖
pip install -r requirements.txt

# 首次需要安装 atx-agent
python -m uiautomator2 init
```

## 使用方法

### 1. 检查设备连接

使用设备检测脚本确保手机正常连接：

```bash
python check_device.py
```

脚本会自动检测：
- ADB 是否已安装
- 手机是否已连接
- USB 调试是否已授权

### 2. 配置参数

编辑 [config.py](file:///Users/dison/Test/config.py) 文件，修改相关参数：

```python
# 定时任务时间（24小时制）
TARGET_TIME = "10:00"

# 抢券按钮文本
COUPON_BUTTON_TEXT = ["立即抢", "抢券", "立即领取"]
```

### 运行模式

#### 1. 立即运行模式（测试）

```bash
python auto_coupon.py now
```

#### 2. 定时任务模式

```bash
python auto_coupon.py
```

## 首次使用建议

1. 先用 **立即运行模式** 测试连接是否正常
2. 确保淘宝已打开在正确的页面
3. 再使用定时任务模式

## 注意事项

- 确保手机屏幕解锁
- 确保手机电量充足
- 保持电脑和手机连接稳定
- 抢券前先手动打开到百亿补贴页面效果更好
- 本脚本仅供学习交流使用，请勿用于非法用途

## 常见问题

### 设备连接失败

- 检查 USB 调试是否已开启
- 尝试更换 USB 接口或数据线
- 在手机上确认 USB 调试授权

### 找不到抢券按钮

- 检查 [config.py](file:///Users/dison/Test/config.py) 中的按钮文本配置
- 可以使用 `uiautomator2` 的截图功能分析界面元素
- 脚本会自动尝试屏幕中心点击作为备用方案

## 项目结构

```
.
├── auto_coupon.py    # 主脚本
├── check_device.py   # 设备检测脚本
├── config.py         # 配置文件
├── requirements.txt  # 依赖列表
└── README.md         # 使用说明
```
