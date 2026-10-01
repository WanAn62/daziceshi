<<<<<<< HEAD
# daziceshi
dazi cesi
=======
# TypeFlow · 打字速度训练

![TypeFlow](assets/banner.svg)

一个纯前端的打字速度训练器。打开就能测，测完给你速度、准确率、稳定度和逐秒曲线。

- **逐键记录**：每一次击键的时间与对错都记下来，成绩不是估出来的
- **三种内容**：英文常用词、中文句子、代码符号
- **两种模式**：计时（15 / 30 / 60 / 120 秒）与整段文本
- **盲打模式**：过程中不显示对错，结束后才揭晓
- **完全离线**：算分全在浏览器里完成，历史记录只存在本机 `localStorage`，不会上传

快捷键：`Tab` 重开一轮，`Esc` 退出。

## 跑起来

需要 Node 20.19 以上、pnpm 11。

```bash
pnpm install
pnpm dev      # 开发服务器
pnpm build    # 产出 dist/，丢到任意静态托管即可
```

| 命令 | 作用 |
| --- | --- |
| `pnpm dev` | 启动开发服务器 |
| `pnpm build` | 类型检查 + 生产构建 |
| `pnpm test` | 跑单元测试 |
| `pnpm test:watch` | 监听模式跑测试 |
| `pnpm lint` | ESLint 检查 |

## 目录结构

```
src/
  components/
    home/     首页：介绍、配置、个人记录、最近趋势
    test/     测试页：实时数据、打字区、结果面板
    stats/    统计页：总览、进步曲线、历史记录
    ui/       按钮 / 面板 / 标签 / 图表等基础件
    layout/   整站外壳（导航 + 页脚）
  hooks/
    useTypingTest.ts   打字引擎：击键记录、计时、结算
    useStore.ts        配置与历史记录（localStorage）
    useHashView.ts     hash 路由
  lib/
    texts.ts   词库与文本生成
    stats.ts   WPM / 准确率 / 稳定度计算
    storage.ts 本地存储读写（带内存兜底）
  pages/       三个页面的视图
```

## 计分口径

| 指标 | 口径 |
| --- | --- |
| 速度（WPM） | 敲对的字符数 ÷ 5 ÷ 用时（分钟） |
| 原始速度 | 所有击键（含敲错）÷ 5 ÷ 用时 |
| 准确率 | 1 − 敲错次数 ÷ 总击键次数 |
| 稳定度 | 100 × (1 − 逐秒速度的变异系数) |

回退删除不会撤销已经敲错的记录——准确率统计的是击键过程，不是最终文本。

## 参与贡献

见 [CONTRIBUTING.md](CONTRIBUTING.md)。改动历史见 [CHANGELOG.md](CHANGELOG.md)。

## License

[MIT](LICENSE)
>>>>>>> 200c78a (first commin)
