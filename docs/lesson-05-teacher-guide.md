# 第 05 次课教师指南｜P1 v1.2.2 交互记忆

## 本课完成结果

学生完成主题切换与本地记忆，使用 `fetch` 读取 JSON，并正确呈现 loading、success、empty、error 和 fallback。关闭数据源时页面仍能显示内置数据和重试入口。

## 课前教师演练

```powershell
git switch p1-v1.2.1
npm ci
npm test
git switch main
npm test
npm run build
```

部署后准备三个地址：

- 正常：站点根地址；
- 空状态：`?empty=1`；
- 失败降级：`?fail=1`。

## 25 分钟演示脚本

1. 给主题按钮注册 `click`，修改根元素 `data-theme`。
2. 刷新页面，说明为什么状态丢失。
3. 用 `localStorage` 保存，再演示存储不可用时的 `try/catch`。
4. 用 `fetch('./projects.json')` 替代直接导入数据。
5. 请求前显示 loading，空数组显示 empty，成功显示 success。
6. 打开 `?fail=1`，演示 error、内置数据 fallback 和重试按钮。

## 三类测试

| 类型 | 操作 | 预期结果 |
| --- | --- | --- |
| 正常 | 切换主题并刷新 | 主题保持；项目数据读取成功 |
| 边界 | 访问 `?empty=1` | 显示项目数量 0 和空状态 |
| 失败 | 访问 `?fail=1` | 显示失败原因、内置项目和重试按钮 |

## 收尾证据

- 三种 URL 状态截图；
- 刷新前后主题截图；
- 18 个累计自动测试；
- CI/CD、固定 URL 和 `p1-v1.2.2` Release；
- 一个真实失败记录及恢复说明。
