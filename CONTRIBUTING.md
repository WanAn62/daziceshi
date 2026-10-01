# 参与贡献

感谢你有兴趣一起改这个项目。下面是最短的上手路径。

## 本地开发

```bash
pnpm install
pnpm dev
```

需要 Node 20.19 以上、pnpm 11。

## 常用命令

| 命令 | 作用 |
| --- | --- |
| `pnpm dev` | 启动开发服务器（Vite，默认 5173 端口） |
| `pnpm build` | 类型检查 + 生产构建，产出 `dist/` |
| `pnpm test` | 跑一遍单元测试 |
| `pnpm test:watch` | 监听模式跑测试 |
| `pnpm lint` | ESLint 检查 |

提交之前，这三个都应该是绿的：

```bash
pnpm lint && pnpm test && pnpm build
```

## 代码约定

- **样式只用设计 token**：颜色一律用 `bg-background` / `text-foreground` / `border-border` / `bg-primary` / `text-destructive` 这类语义类名，不要在组件里写十六进制色值、`rgb()` 或 Tailwind 的默认调色板（`zinc-500` 之类）。整套 token 定义在 `src/index.css` 的 `:root` 里。
- **组件用命名导出**：`export function Foo()`，不要 `export default`。
- **一个文件只做一件事**：整页拆到 `src/components/<页面>/` 下，视图里不塞大段逻辑。
- **状态名避开浏览器全局只读属性**：用 `typed`、`runState`、`jobStatus` 这类名字，别用 `status`、`name`、`history`、`location`、`top` 直接当变量名。
- **纯逻辑写进 `src/lib/`**，并尽量补上单元测试——计分口径改动必须同时更新 `src/lib/stats.test.ts`。

## 目录速览

```
src/
  components/   视图组件（home / test / stats / ui / layout）
  hooks/        打字引擎、本地存储、hash 路由
  lib/          词库、计分、本地存储读写
  pages/        三个页面的视图
  test/         测试的公共初始化
```

## 提交与 PR

- 提交信息用一句话说清「改了什么、为什么」，动词开头；一次提交只做一件事。
- PR 描述里写清：改了什么、怎么验证的、有没有界面改动（有的话贴一张截图）。
- 涉及计分口径的变化，请说明理由并同步更新测试。

## 加一种练习内容

1. 在 `src/lib/texts.ts` 里加词库并在 `buildTargetText` 里接上分支。
2. 在 `src/lib/types.ts` 的 `ContentPackId` / `PACK_LABELS` / `PACK_HINTS` 里补齐。
3. 在 `src/components/home/ConfigPanel.tsx` 的 `PACKS` 数组里加一项。
4. 给新内容补一个 `src/lib/texts.test.ts` 的用例。
