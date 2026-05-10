# 旋转解谜关卡 / Rotation Puzzle Level

## 介绍
这是一个基于 **Godot 4** 的3D旋转解谜关卡模板。
玩家通过拖拽鼠标旋转模型，当模型对齐到目标角度时触发通关效果（黑屏过渡到下一关）。

## 环境要求
- Godot 4.x（推荐 4.2 或以上）

## 使用方法
1. 下载或 Clone 这个仓库
2. 用 Godot 4 打开 `project.godot`
3. 运行主场景 `main.tscn`

## 如何自定义关卡

### 修改目标角度
在场景树中选中 `PuzzleObject` 节点，在右侧 Inspector 面板里调整：
- `Target Rotation` — 玩家需要旋转到的目标角度（X, Y, Z）
- `Rot Threshold` — 判定成功的误差范围（度），默认 5.0

**推荐做法：** 在游戏运行时手动把模型转到目标位置，然后按 **F1** 记录当前角度，再把这个角度填入 `Target Rotation`。

### 修改下一关场景
打开 `pivot_point.gd`，找到 `_on_win()` 函数：
```gdscript
func _on_win():
    _start_glow_then_fade("res://scenes/下一关.tscn")  # ← 改成你的下一关路径
```

### 可调参数一览
| 参数 | 说明 | 默认值 |
|---|---|---|
| `target_rotation` | 目标角度 | (20, 3.2, 0) |
| `rot_threshold` | 判定误差范围（度） | 5.0 |
| `rotate_speed` | 鼠标拖拽旋转速度 | 0.5 |
| `snap_threshold` | 开始自动吸附的距离（度） | 15.0 |
| `snap_speed` | 自动吸附速度 | 5.0 |

## 调试快捷键
运行时可用以下快捷键（仅 Debug 模式下有效）：

| 按键 | 功能 |
|---|---|
| F1 | 记录当前角度为目标角度 |
| F2 | 跳转到目标角度（测试通关） |
| F3 | 重置旋转到 (0, 0, 0) |

## 文件说明
| 文件 | 说明 |
|---|---|
| `main.tscn` | 主场景 |
| `pivot_point.gd` | 旋转控制 + 通关逻辑脚本 |
| `yinghuo.fbx` | 模型文件 |
| `yinghuo_openPBR_shader1_*.png` | 模型贴图（BaseColor / Emissive / Height / Metallic / Normal / Roughness） |
| `puzzle.png` | 参考图 |
