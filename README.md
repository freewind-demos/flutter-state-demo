# Flutter 状态（StatefulWidget + setState）

## 简介

整页放在 **一个 `StatefulWidget`** 里，`_counter` 变化时 `setState` 触发重建，`Column` 展示数字与 `ElevatedButton`。最原始的局部状态写法，适合理解 Flutter 刷新机制。

## 快速开始

### 环境要求

Flutter SDK。

### 运行

```bash
flutter pub get
flutter run
```

## 概念讲解

### 第一部分：`setState` 的作用

告诉框架「我这一类 State 对象上有字段变了，请再调一次 `build`」。**不要在 `build` 里调 `setState`**，避免无限循环。

### 第二部分：何时不用 `setState`

跨页面共享、异步数据流、与业务分层耦合时，才引入 Provider、Riverpod、Bloc 等。本 Demo 刻意保持单文件。

## 完整示例

见 `lib/main.dart`：`_MyAppState` 的 `_increment` 与 `build`。

## 注意事项

- `State` 生命周期方法（`initState`、`dispose`）要成对管理控制器、订阅。
- 大作全局 `setState` 会造成不必要 rebuild，应下放到更小 State 或换成细粒度监听。

## 完整讲解（中文）

`setState` 不是「落后」，而是 **最小教学模型**：让你看见「数据一变，界面跟变」。等同一个数字要三屏共用，你就会自然想把计数挪到上层状态管理。先理解这一条刷新链，再学任何架构都轻松。
