# 学习看板 · 发布仓库

这个目录是**发布产物目录**，内容由脚本自动生成，**不要手动改这里的东西**。

## 里面有什么

| 文件 | 说明 |
|---|---|
| `index.html` | 合并版学习看板（3 个专题 + 标签切换）。**这就是线上访问的入口** |
| `README.md` | 本文件 |

## 它是怎么生成的

由 `../publish.sh` 生成：

```
../build-board.sh  →  把 3 个专题的看板打包成一个 index.html
                   →  在这里 git commit
                   →  推送到所有 remote（Gitee / GitHub）
```

## 为什么单独一个 git 仓库

因为 `~/数据/Code/` 下面还有 Angular、LeetCode、LibreChat、Spring、python 等一堆
**互不相关的项目**。如果把那一整个目录变成 git 仓库，很容易误提交一堆无关代码。

单独一个 `publish/` 目录，**这里只有看板**，从根上避免这个问题。

## 源文件在哪（改了要重新发布）

真身在各自的专题仓库里，**这里只是打包产物**：

```
../../Database-Learn/roadmap/data/*.js
../../Redis-Learn/roadmap/data/*.js
../../Java-Basic-Learn/roadmap/data/*.js
```

改了这里的 `index.html` 没有意义 —— 下次 `publish.sh` 会把它覆盖掉。

## 手动重新发布

```bash
bash ~/数据/Code/Learn/_tools/publish.sh
```

平时不用手动跑 —— `watch.sh` 会监听源数据的变化自动发布。
