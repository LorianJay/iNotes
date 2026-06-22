# 目录 
1.编程工具  



## 1.编程工具  
**目录:**  
1.1 AI模型选择指南  
1.2 AI代码编辑器  
1.3 命令行编辑工具  
1.4 AI IDE插件  
1.5 OpenClaw  


### 1.1 AI模型选择指南
1.分清AI编程工具和AI模型  
AI编程工具:Cursor、Claude Code可以理解为传统的IDE,用来生产代码  
AI模型:Claude、ChatGPT可以理解为传统的程序员,负责思考  
<font color="#00FF00">所以同样是用‍Cursor,选择不同的模型Claude或Chat⁡GPT,最终呈现的效果自然会不一样</font>  

2.主流AI模型  
* 国际顶尖模型:Claude、ChatGPT、Gemini这三大巨头
* 国产优秀模型:DeepSeek、智谱GLM、通义千问、Kimi等性价比之选
* 还有开源模型:Llama、Qwen等,需要一定技术能力自己部署

![模型能力对比](resources/VibeCoding/1.png)  
![模型能力对比](resources/VibeCoding/2.png)  

2.1 Claude最强编码能力  
发布路线:Claude 4.5(2025)->Claude Opus 4.6(2026.2)->Claude Opus 4.8(2026.5)->claude fable 5(2026.6)  

Claude4‍系列主要有两个版本线:Opus是顶配版本,编程能力最强,但速⁡度相对较慢,价格也更高;Sonn​et是平衡版本,在性能和速度之间取得了很好的平衡,性价比最高.  

Claud‍e主要有3种使用方式:  
* 官方订阅:Claude Pro每月20美元,Max 5x每月100美元,Max 20x每月200美元
* Cursor:订阅Cursor Pro每月20美元,包含了Claude的使用额度
  Curso⁡r的优势是每个月不同的模型有不同的额度,不过超出额度之外是需要额外付费的
* API调用(按量付费):按Token计费,用多少付多少,比较灵活

2.2 ChatGPT  
发布路线:GPT-5.3-Codex(2026.2)->GPT-5.5(2026.4)

ChatGPT主要有3种使用方式: 
* ChatGPT Plus:每月20美元
* ChatGPT Pro:每月100美元(5 倍用量)或每月200美元(20 倍用量)
* API 调用:按Token计费(GPT-5.5为$5/M输入、$30/M输出)

2.3 Gemini  
Gemini最厉害的地方是它的<font color="#00FF00">超长上下文窗口</font>,Gemini 3 Pro支持1M Token(约100万字)的输入上下文,所以如果你需‍要处理大型项目、需要分析大量代码、做UI⁡/前端开发、或者预算​有限但需要强大能力,Gemini会是很好的选择  

Gemini主要有3种使用方式: 
* Gemini 3 Pro:每月19.99美元
* API调用:价格比Claude和GPT便宜很多
* 免费版本:Gemini 3 Flash有一定的免费额度,每天也有几次思考模型的试用

2.4 DeepSeek  
DeepSeek-V4是开源模型,完全免费使用(API按量计费价格极低),编程能力在国产模型中数一数二;V4系列支持100万token超长上下文,包括更强的DeepSeek-V4-Pro(1.6T参数,49B 激活)和更快更便宜的DeepSeek-V4-Flash(284B参数,13B激活),特别适合Agent编程和大型代码库分析  

2.5 Qwen3(千问)
阿里通义千问Qwen3.7-Max是2026年5月发布的旗舰模型,专为智能体时代设计,在编程、推理、长程自主执行等能力上表现出色,支持Claude Code、OpenClaw等主流框架;通过阿里云百炼平台可以API调用(输入12元/百万Tokens,输出36元/百万Tokens)或Token Plan订阅使用  

2.6 <font color="#FFC800">GLM(智谱)</font>
智谱GLM-5(及最新的GLM-5.2)是清华团队出品的旗舰模型,2026年2月发布,全球开源模型综合排名第一;GLM-5在Coding和Agent能力方面表现非常突出,支持200K Token的长上下文,具备强大的工具调用和长程任务规划能力;实测下来,体感已经接近Claude Opus级别,但作为开源模型,成本要低得多,我自己也在持续用GLM开发,在生成完整项目方面的速度和效果都很不错  

2.7 Kimi
月之暗面Kimi在很早之前就支持超长上下文能力(200万字),在国产模型中独树一帜;特别适合处理大型项目的代码,可以一次性处理500个文件  

3.怎么选  
* 学习阶段:如果你还在‍学习,主力用DeepSeek-V4或通义千问(Qwen3.7-Max通过Token ⁡Plan 订阅很划算),辅助用Gemini ​3 Flash的免费额度;这个阶段重点是熟悉AI编程的感觉,这些模型完全够用
* 做前端/U‍I项目:Gemini 3 Pro在前端UI设计方面表现特别出色,⁡实测它能生成质感很好的界面、3D 模​型构建能力也很强;如果你主要做前端,Gemini是很好的选择
* 做全栈项目:优‍先选择编程能力强的Claude Sonnet,能力全面前后端都能⁡应对;配合 Cursor使用,开发体​验很好;如果需要快速生成完整项目,智谱GLM-5的速度和效果也不错
* 大量测试和调用:De‍epSeek-V4的API价格极低,而且通义千问(Qwen3.7-Max)也有 Token⁡ Plan订阅方案,适合需要大量调用的场景,测​试时可以放心使用

### 1.2 AI代码编辑器  
1.Cursor  

2.其它主流AI代码编辑器  
* [Windsurf](https://devin.ai/desktop):最大的优势是完全免费  
* [Antigravity](https://antigravity.google/):是Google推出的智能体开发平台
* [Kiro](https://kiro.dev/):是Amazon推出的AI IDE,强调"规范驱动开发",先写需求规范,再让AI实现
* [Trae](https://www.trae.cn/):字节推出
* [Zed](https://zed.dev/):用Rust编写的高性能代码编辑器

3.在Cursor中使用MCP  
参考帖子:https://ai.codefather.cn/library/2010974694076256258  

### 1.3 命令行编辑工具  
**目录:**  
1.3.1 命令行编辑工具和AI代码编辑器的区别
1.3.2 Claude Code安装教程  
1.3.3 CC Switch  
1.3.4 主流CLI  
1.3.5 CodeX CLI  
1.3.6 React Ink  
1.3.7 飞书CLI  

#### 1.3.1 命令行编辑工具和AI代码编辑器的区别  
这两个工具从来就不是相互竞争,而是相互配合,有些场景下CLI更好用而有些场景下cursor更好用,CLI一般更加灵活  
CLI就是命令行界面,与之对应的是GUI图形化界面,如果让AI直接操纵GUI则效率、准确度等都十分低下,所以CLI就是AI发挥最大威力的工具,比如[OpenCLI](https://github.com/jackwener/opencli)这个项目的理念就很好,他能将市面上的各大应用转为CLI,想象一下如果要让AI将目前热点榜单前10的回答全部记录下来,这件事情在GUI平台上做的话会十分麻烦,但是有CLI的话就很方便直接通过API请求,然后直接对结果进行操作,<font color="#00FF00">所以CLI是专门为AI编写的操作平台</font>,而GUI是专门为人类编写的操作平台  
AI代码编辑‍器是有图形界面的软件,你可以看到文件列表、代码高亮、按钮⁡等等;而命令行工具完全​在终端里运行,只有文字输入和输出,几乎没有任何图形界面  

*提示:本节可以补充看1.3.7 飞书CLI,对现代的业务模式有更好的理解*  

#### 1.3.2 Claude Code安装教程  
1.官网  
[详情可以参考官方文档](https://code.claude.com/docs/zh-CN/quickstart#native-install-recommended)  

2.安装  
一定要先确保电脑上有nvm和相应的node  
Linux环境下执行这条命令`npm install -g @anthropic-ai/claude-code`  
安装完毕之后,执行`claude`运行claude code  

3.替换模型  
要想使用Claude就必须登陆,登陆的话有三种方式,第一种是网页端登陆并购买Claude的会员,第二种是输入Claude家的API的token,第三种就是不使用Claude的模型,而是使用第三方的模型,但是第三方的模型只支持零星的几个(不支持国产模型),为此接下来需要将使用国产模型  
假如这里要使用deepseek模型,可以参考这个[deepseek对接各大agent的文档](https://github.com/deepseek-ai/awesome-deepseek-agent/blob/main/README.zh-CN.md),下面以接入claude为例进行演示  
编辑`~/.claude/settings.json`配置文件  
```json
{
  "theme": "dark",
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.deepseek.com/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "这里填入api的key",
    "ANTHROPIC_MODEL": "deepseek-v4-pro[1m]",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "deepseek-v4-pro[1m]",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "deepseek-v4-pro[1m]",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "deepseek-v4-flash[1m]",
    "CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": "1",
    "CLAUDE_CODE_EFFORT_LEVEL": "max"
  }
}
```

4.运行claude  
![Claude](resources/VibeCoding/3.png)  

5.提示词如下:
> 直接在当前文件夹下创建一个JavaGUI项目要求使用标准maven,当前路径就是根路径,不需要再创建子文件夹,要求是界面小清新现代化,左侧有一个切换卡片栏,当鼠标移动到左边的时候他会自动展开,在这个切换栏可以有page1 page2 page3,点击对应的page按钮即可切换到对应的页面,当鼠标移出这个侧边栏的范围之外时这个侧边栏会自动收回  

确认之后claude会在命令行显示生成的执行计划,内容很长最后会询问你是否同意使用该计划,还是说你有一些修改的地方,这里直接yes  
![demo](resources/VibeCoding/4.png)  

6.消费金额  
本次项目生成花费10分钟,花费如下,有点贵我感觉是他生成的内容太详细了,很多东西都没有必要,而且生成的时间也太长了  
![消费](resources/VibeCoding/5.png)  

7.卸载  
因为是使用npm安装的,所以卸载的时候就按照npm来卸载,执行命令`sudo npm uninstall -g @anthropic-ai/claude-code`  

#### 1.3.3 CC Switch  
1.介绍  
这个项目是一个图像化的[开源项目](https://github.com/farion1231/cc-switch),用于可视化管理Claude Code的模型配置,也可以在这里看到刚才生成的项目所花费的token数量  
![介绍](resources/VibeCoding/6.png)  

2.主页  
下图是主界面的样式,实际上主界面由三个主要的部分组成,首先是上方的各种AI编程工具(注意编程工具需要和AI模型区分),选择了某一个具体的编程工具之后,下面会显示该模型可以使用哪些供应商,也就是说选择不同的AI编程工具下方的可选模型是不同的,比如这里就有常见的几种AI编程工具,当你在下方选择某一个具体的供应商此时会直接切换到该模型进行使用,十分方便  
![主界面](resources/VibeCoding/8.png)  

3.添加新供应商
比如现在要为claude code添加deepseek的供应商,此时在主界面右上角点击黄色的+,选择预设供应商中的deepseek  
![配置模型](resources/VibeCoding/7.png)  
点击绿色的框框可以获取当前供应商支持的模型,然后再点击红色框框可以选择具体的某一个模型  

4.安装不同的CLI  
另外CC Switch非常方便的一点,点击设置->关于,可以在这里一键安装主流的CLI以及各种agent助手  
![安装不同CLI](resources/VibeCoding/9.png)  

#### 1.3.4 主流CLI  
1.Gemini CLI  

2.Warp  

3.GitHub Copilot CLI  

4.OpenCode  

#### 1.3.5 CodeX CLI
1.介绍  
openAI家的AI编程工具其实是分为Codex和CodexCLI两个的,不过目前codex(AI编程工具)只支持Windows和Macos,所以目前可以先使用CodeXCLI  

2.安装  
直接通过CC Switch来安装也是十分方便的  
执行命令`npm install -g @openai/codex`

3.更新  
更新的命令和安装的命令一样`npm install -g @openai/codex`  

4.卸载  
因为是使用npm安装的,所以卸载的时候就按照npm来卸载,执行命令`sudo npm uninstall -g @openai/codex`  

#### 1.3.6 React Ink  
1.介绍
[React Ink](https://github.com/vadimdemedes/ink)是一个开源的项目,该项目将传统的React代码渲染为浏览器页面的逻辑改变为,使用同样的React组件最终渲染成终​端界面CLI,所以这个项目本身和AI没有太大关系,而是用于开发CLI的一款组件  


#### 1.3.7 飞书CLI  
1.基本介绍  
[飞书CLI](https://github.com/larksuite/cli)这个项目实际上是*1.3.1 命令行编辑工具和AI代码编辑器的区别->OpenCLI*的一个商业落地项目,飞书CLI允许你一行命令直接直接操作飞书的消息、日历、文档等功能<font color="#00FF00">也就是说各家应用目前的趋势是产品CLI化,关键是产品CLI化之后可以很方便地被各种AI Agent工具接入</font>,所以有一句话叫以前产品之间的互通​靠API,现在AI时代<font color="#FF00FF">产品和AI之间的互通靠CLI</font>  

2.CLI和MCP的区别  
貌似看起来只要各家开放自已的MCP,AI Agent一样可以接入各家的产品,但为什么还需要CLI化呢?
MCP协议要求把‍所有工具的名称和参数格式全部注入到AI的上下文里,工具一多 Toke⁡n 消耗就很夸张;有机构做过基准测试​同样的任务,MCP的Token消耗可能是CLI的几十倍!  
而且MCP的运行过程对人类来说就像个黑盒,出了问题很难排查;C⁡LI就不一样了,如果出错​了,直接把命令复制到终端里跑一遍,报错信息一目了然  


### 1.4 AI IDE插件  
1.Cline  
[Cline](https://github.com/cline/cline)是一个开源的AI编程插件,优势在于支持各种IDE以及各种大模型,功能上最接近Cursor  
直接去各大IDE里面安装这个插件,然后按步骤使用即可  

2.Claude Code VS Code  
这是Claude Code官方推出的VS Code的插件  

3.GitHub Copilot  
GitHub官方推出的插件,已经十分成熟,该插件需要付费,学生和开源贡献者可以免费使用  

4.JetBrains AI Assistant  
JetBrains AI Assistant是JetBrains官方推出的AI编程助手,专门为JetBrains IDE优化,不过这个插件貌似不是免费的  

5.Continue  
[Continue](https://github.com/continuedev/continue)是开源的AI编程插件,功能和Cline类似但更轻量;支持多种AI模型,有代码补全、对话、代码编辑等功能,界面比较简洁,上手容易;完全免费,支持VS Code和JetBrains  


### 1.5 OpenClaw  
1.基本介绍  
一个AI助手  

2.安装教程  
参考[官网](https://openclaw.ai/),执行命令`curl -fsSL https://openclaw.ai/install.sh | bash`  
安装成功后,控制台显示以下内容  
![OpenClaw](resources/VibeCoding/10.png)  

3.配置OpenClaw  
3.1 设置模式选择QuickStart  

3.2 选择模型,选择合适的模型,国产大模型在更多里面  

3.3 然后基本上就是看提示安装  

4.pinchbench
[pinchbench](https://pinchbench.com/)这个网站用于测试各家大模型在OpenClaw场景下的实际表现  

5.openclaw相关命令  
* `openclaw gateway run`启动openclaw的网关  
* `openclaw gateway stop`关闭openclaw的网关
* `openclaw gateway status`查看网关状态
* `openclaw dashboard` 启动openclaw
* `systemctl --user stop openclaw-gateway.service`正确关闭openclaw的方式
* `openclaw uninstall`卸载openclaw

6.卸载openclaw  
可以使用下面这些命令,最好还是用docker装这玩意吧,太恶心了  
```shell
openclaw gateway stop
openclaw gateway uninstall
rm -rf "${OPENCLAW_STATE_DIR:-$HOME/.openclaw}"
npm rm -g openclaw || pnpm remove -g openclaw
```






