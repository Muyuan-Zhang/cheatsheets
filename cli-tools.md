# 🚀 CLI 工具速查表（fzf/fd/rg/bat/eza/zoxide/tldr/jq/starship）

> 安装位置：`~/.local/bin` ｜ 安装日期：2026-08-15 ｜ 忘记用法先翻这里，再不行用 `tldr <命令>`

---

## 1️⃣ fzf —— 模糊查找器

| 操作 | 命令 | 说明 |
|---|---|---|
| 搜历史 | `Ctrl+R` | 输关键字过滤历史命令 |
| 找文件 | `Ctrl+T` | 模糊选文件，路径填入命令行 |
| 跳目录 | `Alt+C` | 模糊选目录并 cd |
| 管道筛选 | `ls \| fzf` | 任何命令输出都能变交互菜单 |
| 预览 | `fzf --preview 'bat {}'` | 右侧实时预览 |

## 2️⃣ fd —— 快速 find

| 操作 | 命令 | 说明 |
|---|---|---|
| 按名找 | `fd dsh` | 当前目录递归（自动忽略 .git） |
| 按扩展名 | `fd -e js` | 只找 .js |
| 只找目录 | `fd -t d` | type: file/d/symlink |
| 含隐藏 | `fd -H` | 默认忽略 . 开头 |
| 排除目录 | `fd -E node_modules` | 可多次使用 |
| 精确路径 | `fd dsh /home/dev` | 指定搜索根 |

## 3️⃣ rg —— 秒搜代码

| 操作 | 命令 | 说明 |
|---|---|---|
| 基础搜索 | `rg "TODO" ~/.dsh` | 文件名+行号+高亮 |
| 忽略大小写 | `rg -i "todo"` | |
| 按语言 | `rg -t js "x"` | -t 后接语言名 |
| 只列文件名 | `rg -l "x"` | |
| 统计行数 | `rg -c "x"` | |
| 上下文 | `rg -C 2 "x"` | 前后各 2 行 |
| 只看匹配 | `rg -o "x"` | 只输出匹配部分 |

## 4️⃣ bat —— 高亮 cat（`cat` 已别名到它）

| 操作 | 命令 | 说明 |
|---|---|---|
| 看文件 | `bat 文件` | 高亮+行号+分页（q 退出） |
| 强制语言 | `bat -l json 文件` | |
| 显示隐藏字符 | `bat -A 文件` | |
| 管道模式 | `命令 \| bat` | 自动去行号纯文本 |

## 5️⃣ eza —— 现代 ls（`ls/ll/la/lt` 已别名）

| 操作 | 命令 | 说明 |
|---|---|---|
| 基本列表 | `ls` | 彩色+目录排前 |
| 详情 | `ll` / `eza -l` | 权限/大小/日期 |
| 树形 | `lt` / `eza --tree -L 2` | -L 限深度 |
| git 状态 | `eza -l --git` | 每行 git 增删改 |
| 总大小 | `eza -l --total-size` | |
| 图标 | `eza --icons` | 需 Nerd Font 终端 |

## 6️⃣ zoxide —— 智能 z

| 操作 | 命令 | 说明 |
|---|---|---|
| 跳转 | `z dsh` | 模糊匹配最常去目录 |
| 多词 | `z pro dsh` | 空格分隔多个关键词 |
| 列记录 | `z -l` | 看权重排序 |
| 精确 | `z /完整/路径` | 直接 cd |

## 7️⃣ tldr —— 精简 man

| 操作 | 命令 | 说明 |
|---|---|---|
| 查用法 | `tldr tar` | 最常用示例直接抄 |
| 更新缓存 | `tldr --update` | 新命令首次用前跑一次 |
| 中文 | `tldr -L zh_CN fd` | 部分命令有中文 |

## 8️⃣ jq —— JSON 利器

| 操作 | 命令 | 说明 |
|---|---|---|
| 格式化 | `cat a.json \| jq .` | 彩色缩进 |
| 取字段 | `... \| jq .a.b` | 点路径取值 |
| 过滤 | `... \| jq '.[] \| select(.x>1)'` | |
| 转换 | `... \| jq 'map(.n)'` | |
| 组合 | `... \| jq '[.[] \| {n: .name}]'` | 重构结构 |

## 9️⃣ starship —— 提示符

| 操作 | 命令 | 说明 |
|---|---|---|
| 开配置 | `starship config` | 打开/创建 TOML |
| 改单项 | `starship config <key> <value>` | 立即生效 |
| 预设 | `starship preset nerd-font-symbols` | 看内置预设 |
| 配置文件 | `~/.config/starship.toml` | 想还原就删它 |

---

## 💡 组合拳速记

```bash
# 找文件 → 模糊选 → 打开
fd -e md | fzf | xargs bat

# 搜代码 → 模糊选 → 看上下文
rg -l "bug" | fzf --preview 'bat {}'

# 跳目录 → 搜内容
z proj && rg "FIXME"

# 看历史命令用法
tldr <命令>
```
