# 凤不栖戏份盘点网站 · 固定规则

请用中文回复。

## 一、项目
- 网站:GitHub 仓库 jwjw-888/fbq(分支 main),GitHub Pages:https://jwjw-888.github.io/fbq/ ,手机当 app 用。
- 模板来自刀笔娘子网站(jwjw-888/wjy_dramas),但**没有大计划、没有 PDF、没有拍摄日期**,只统计 Excel 里的戏份。
- 文件:index.html(界面与逻辑)、data.json(场次:roles、scenes)、sw.js(缓存版本号,改网页就加 1)、manifest.webmanifest、icons/。
- 导入 Excel 只改 data.json;改界面才改 index.html 和 sw.js。
- 测试:本机 http.server + Playwright。

## 二、安全规则
- 用户的 email 不能出现在网站或 commit 里。commit 作者用 jwjw-888@users.noreply.github.com。
- commit 署名行(Co-Authored-By、Claude-Session)照该聊天系统给的内容写,模型名以实际使用的为准。
- 先 git pull --rebase 再 push。
- 目前没有管理员在线编辑(没有设定 fbq 的 GitHub token),登录按钮已隐藏。

## 三、Excel 格式与导入
- 只看 Sheet1(总表)。
- 栏位:集数、场号、景光(日/夜)、景别(内/外)、主场景、次场景、内容提示、页数,之后每个角色两栏:「页数」+「标记」(如 霜15D、玦①、少歌)。
- 角色该栏页数有填 = 该场有戏。角色页数 = 该角色出现场次的「页数」栏加总(和刀笔一样)。
- 网站「日夜」= 景光,「内外」= 景别。
- 页数是文字时(如 0.3S、005、部分0.45)取其中的数字,并提醒用户。
- 每次导入要核对 Excel 合计行(每个角色、总页数)、场次数,有误要明确指出(哪一项、差多少)。

## 四、已确认(用户 11/20)
- 角色名:萧玦(Excel 写萧缺)、萧琛(Excel 写萧探)、江照薇(分集表写江照潋)。导入时自动改,并提醒 Excel 写法不同。
- 4集12ins、9集3ins 各有两场不同内容,都算。
- 只看 Sheet1 总表,分集工作表不用。

- 戏份占比页有三种秦长歌/明霜算法:照 Excel 标记 / 只有明霜·秦长歌(扣掉秦栏标记含「弦」的场次,data.json 的 xq=1)/ 含阿弦(再加上其他角色栏标「/弦」或概要写到弦的场次,xian=1)。导入新 Excel 要重算这两个标记。

## 五、要先问用户
- 同一集出现重复场号、新出现的奇怪场号、角色名写法不一致。
