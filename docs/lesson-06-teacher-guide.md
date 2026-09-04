# 第 06 次课教师指南｜P1 v2.0 Vue 门户

## 本课完成结果

学生在不丢失原有功能的前提下，将原生项目重构为 Vue 3 + Vite。页面保持原固定 URL，并继续支持响应式、打印、筛选排序、异步状态、失败降级和主题记忆。

## 课前教师演练

```powershell
git switch p1-v1.2.2
npm ci
npm test
npm run build
git switch main
npm ci
npm run dev
```

教师必须先写出新旧功能回归表，再进行重构。不要把“换成 Vue”误讲成视觉改版。

## 25 分钟演示脚本

1. 对比原生入口和 Vite 的 `index.html` 挂载点。
2. 从静态 header 抽出 `ProfileHeader`，演示 prop 与 emit。
3. 把项目卡抽成 `ProjectCard`，用 `v-for` 和稳定 `:key` 渲染。
4. 用 computed 组合筛选与排序，不手工同步第二份数组。
5. 用 `onMounted` 读取主题和项目数据。
6. 运行组件测试，修改 emit 名称使测试失败，再恢复。
7. 解释 `vite.config.js` 中 GitHub Pages `base` 的作用。

## 新旧功能回归

| 功能 | v1.2.2 | v2.0 验收 |
| --- | --- | --- |
| 手机/桌面/打印 | 已有 | 不倒退 |
| 筛选/排序 | 已有 | computed 驱动 |
| JSON 读取与降级 | 已有 | onMounted + ref |
| 主题记忆 | 已有 | 组件事件驱动 |
| 项目选择反馈 | 无 | 子组件 emit，父组件处理 |

## 收尾证据

- 组件树与各组件单一职责；
- props/emit 解释；
- Node 单元测试、Vitest 组件测试和生产构建；
- CI/CD、固定 URL 和 `p1-v2.0` Release；
- v1.2.2 与 v2.0 回归表；
- 从上一 Tag 恢复并重新构建的记录。
