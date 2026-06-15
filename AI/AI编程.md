# 目录  
1.介绍  
2.学习路线  


## 1.介绍  
**目录:**  
1.1 相关术语  
1.2 大模型推荐  

### 1.1 相关术语  
1.LLM  

2.Prompt(提示词)  
每次与AI对话时当前发送的信息就称为提示词Prompt  

3.Context(上下文)  
LLM非常傻,只能一次问一次答,为了解决这个问题,则将上一次的Prompt+LLM的Response作为下一次的Context,每次问答由Context+Prompt组成  
简单理解为,AI把所有的历史问答记录放到Context便于理解,而Prompt永远指代每次的新问题  

4.Memory  
将上下文信息进行压缩便形成了Memory,AI通过Memory+Prompt来生成下一次的Response  

5.Agent(智能体)  
智能体的翻译不恰当,翻译为代理更加合适  
由于LLM本身只具备文字推理的功能,假设现在要让LLM总结查询及时的互联网信息,那么LLM就做不到,为了解决这一问题,在用户与LLM沟通的桥梁中添加了一个中间代理(Agent),假设用户让AI去查询实时新闻,由于AI做不到,所以它就把这个请求委派给Agent去执行,让Agent去互联网搜索然后再将结果返回给LLM,LLM整合之后再返回给用户  
![Agent](resources/AIProgram/1.png)  
*提示:看完本节之后,实际上Agent做的工作就是加context到LLM中,最终离不开大模型,有点茴香豆的五种写法,Agent帮助你更好地编写上下文内容,也是所有环节中最不需要智能的地方,即<font color="#00FF00">一个流程中所有能通过固定程序解决而不用大模型解决的地方就是Agent发挥作用的地方</font>*  


6.Function Call  
现在LLM可以委派Agent去执行一些增强服务的功能,但大模型本身就只有文字生成功能,Agent只能通过判断大模型返回的语义来去调用相应的接口,但是每次大模型返回的内容都不相同,Agent不好识别大模型具体需要哪个功能,于是乎  
通过一种称为Function Call的约定在LLM和Agent之间,当LLM需要调用Agent增强功能的时候,必须以指定的格式(例如JSON)写明当前需要调用那个具体的Agent服务  

6.MCP  
目前Agent的增强服务都是写在主程序里的,没有解耦;所以现在将Agent提供的这些增强服务抽离出来,成为单独的服务,并在Agent和增强服务之间通过MCP来约定当前有哪些服务、怎么调用这些服务  
![MCP](resources/AIProgram/2.png)  

7.大模型的交互方式  
目前有CLI、IDE集成、桌面程序  
CLI:Claude Code、CodeX、IFlow、KimiCLI  
IDE:Cursor、Antigravity、Trae、KimiCode  
桌面程序:Clawdbot、Moltbot、OpenClaw  

8.LangChain
现在用户让Agent完成,读取某个PDF并将其翻译为中文并保存为HTML格式的需求,首先Agent会调用MCP进行读取,然后把读取到的内容传给LLM,LLM翻译完成之后再传给Agent让Agent将内容转为HTML  
像这种具有重复性任务且流程相对稳定的任务,如果每次都交由Agent自由发挥会导致Agent发挥不稳定且浪费token,为此把整个流程中固定的这些部分用LangChain(硬编码实现)来实现,直接用编程的方式解决,仅仅在翻译的这一部分由LLM接手  

9.WorkFlow(工作流)  
为了方便LangChain的编写创造出的一套低代码平台,允许通过网页直接操作工作流的方式称为WorkFlow  

10.Skills  
如果转换的文件格式种类十分繁多,就需要编写很多的工作流去处理这些转换  
为此准备一个目录,将所有可能涉及到的转换操作都提前编写成相应的脚本固定,对这些脚本编写一个统一的说明文件<font color="#00FF00">SKILL.MD</font>,该说明文件需要描述整体的流程  
然后在每次与Agent交互的时候,后台添加一条提示词为根据SKILL.MD格式做相应的内容处理,进一步优化就是Agent提前约定好某个文件夹为所有SKILL存放的路径,Agent就会从该路径下自动读取并选择对应的SKILL  
<font color="#00FF00">SKILL.MD的本质就是提示词</font>  
![Skills](resources/AIProgram/3.png)  
Agent-Skills已经成为通用标准Claude Code、Cursor、Vscode都支持  

11.渐进式披露  
LLM执行任务时会通过Agent扫描约定好的SKILLS文件夹下的所有SKILL,但不会把所有SKILL.MD的内容全部加载到context,而是只读取每个SKILL的元数据,如果SKILL的描述和任务相关就使用该SKILL  

12.Skill-Creator  
技能创建者,该技能专门用于生成其它的技能  

13.SubAgent  
随着任务的扩展,Agent的上下文可能会变得非常大,为此可以对不同的独立的子任务产生一个单独的SubAgent,其本质就是上下文隔离,SubAgent的上下文不会保留在主Agent中,分治思想  

14.Token  
token是模型用来表示自然语言文本的基本单位(大模型以token为单位进行输出),也是我们的计费单元,可以直观的理解为"字"或"词",通常1个中文词语、1个英文单词、1个数字或1个符号计为1个token,一般情况下token的换算  
1 个英文字符 ≈ 0.3个token  
1 个中文字符 ≈ 0.6个token  

15.参数  
单位为B,代表十亿;3B拥有30亿个参数、0.9B拥有9亿个参数  
* 参数越多:模型通常越聪明,能理解更复杂的逻辑,知识储备更丰富,但也更占空间,运行更慢
* 参数越少:模型更轻巧,运行速度极快,可以跑在手机或普通笔记本电脑上,但在处理复杂问题时容易"胡言乱语"

16.Training/Inference  
运行在个人设备上的模型,例如3B-9B的模型;会分为两个步骤,首先是各大厂商先训练Training模型,这个过程需要上千张显卡花几个月时间进行训练;厂商训练好之后会发布一个几GB大小的权重文件,把该文件下载到手机或电脑上运行(称为Inference)  
* 计算量差异:不同参数量的计算差异,每生成一个Token,电脑需要把所有的参数全部算一遍,例如0.9B每一轮只需要9亿次计算,而7B每一轮需要70亿次计算  
* 内存带宽瓶颈:模型运行需要把参数从内存(RAM)搬运到处理器GPU里;3B模型可能只有 2GB大小,搬运很快;70B模型有40GB以上,搬运速度慢,出字自然就卡

17.端侧AI
像这种运行在个人手机/电脑上的模型称为<font color="#00FF00">端侧AI</font>,它有两种部署方式  
* 云端模型(ChatGPT,Claude)
* 端侧模型:模型文件直接存在你的手机闪存里,调用手机自带的NPU
  响应快,隐私安全,断网可用


18.私有化部署  
买云服务部署跑模型,这种叫私有化部署;如果自建机房跑内网模型,这种也叫私有化部署,不叫端侧AI  
区别在于算力在哪里,如果算力就在发送请求的那台设备上(比如手机、电脑)那它就是端侧AI,如果算力在远处/在公司内网机房,只要你把指令传给服务器,服务器再把结果返回给你就叫私有化部署  




### 1.2 大模型推荐  
1.总览  
* Anthropic-Claude 4.6/4.5:目前最强
* OpenAI-GPT-5.2/o3:非常不错
* Google-Gemini 3 Pro/Flash:多模态、超长上下文  
* Grok
* deepseek-V3.2/R1:性价比之光
* Kimi-K2 Thinking:擅长超长文本分析和深度思考模式

2.Claude Code  
Claude Code就是一个编程Agent,并不是大模型,它是CLI交互形式的类似Cursor的IDE,它的功能是直接操作文件、理解上下文、使用工具  
Claude Code原生仅支持<font color="#00FF00">Anthropic</font>自家的Claude系列模型(如Claude 4.5或4.6系列)  
但可以通过代理(Proxy)或路由(Router)技术实现了对其他模型的支持,可以通过第三方中间件如<font color="#00FF00">Claude Code Router</font>让Claude Code这个Agent去调用GPT或Gemini
只要目标模型支持Anthropic协议就可以接入到Claude Code中  
官方支持:Claude 4.5/4.6 Opus(擅长复杂架构)、Claude 3.5 Sonnet(默认)、Claude 3.5 Haiku(极速且廉价)  
如果确定要用Claude的模型,那就用Claude Code这个Agent  

<font color="#FF00FF">Vscode+AI插件与Cursor的区别:</font>  
| 维度           | VS Code + AI 插件             | Cursor(AI原生IDE)                       |
|:---------------|:------------------------------|:----------------------------------------|
| **底层架构**   | AI是个"旁听生"(插件API限制多) | AI 是"主理人"(深度修改了内核)           |
| **上下文范围** | 仅限当前打开的文件            | **整个项目/代码库** (Local Indexing)    |
| **多文件协作** | 基本靠手动复制粘贴            | **Composer模式**(一句话改全身)          |
| **终端理解**   | 你复制报错信息给它            | 它能**自动读报错**并写出修复方案        |
| **上手难度**   | 需要折腾各种插件配置          | 一键导入 VS Code 所有插件/配置,无痛迁移 |

<font color="#FF00FF">Claude Code与Cursor的区别:</font>  
| 维度         | Cursor (IDE)                                      | Claude Code (CLI)                                                       |
|:-------------|:--------------------------------------------------|:------------------------------------------------------------------------|
| **交互逻辑** | **你写代码,它辅助** 它更像是一个极其智能的输入法  | **你下命令,它写代码** 它更像是一个初级程序员(Agent)                     |
| **自主权**   | 它修改文件后,通常需要你一个个手动确认(Apply/Diff) | 它能**自主**运行命令、读日志、跑测试、修复报错,直到任务成功             |
| **处理广度** | 强于当前打开的文件或相关联的代码上下文            | 强于**整个项目**。例如："帮我把整个项目的数据库从MySQL迁移到PostgreSQL" |
| **工具调用** | 局限于编辑器内的操作(搜索、替换、跳转)            | 能调用 Git、终端命令、浏览器甚至系统工具(如搜索本地文件)                |

VsCode(手动挡)、Cursor(辅助驾驶)、Claude Code(无人驾驶)  

3.OpenCode  
也是一款CLI工具,和Claude Code在功能上很类似,主要特点在于<font color="#00FF00">100%开源、不绑定特定模型</font>  
Claude Code是闭源的,默认只能调用Claude系列模型  
但是现在OpenCode已经无法使用Claude模型了  

4.CodeX  
Claude Code:自主权极高,只能使用Claude的相关模型  
CodeX:多样性支持多种模型,自主权较低,它是OpenAI出的一款对标Claude Code的CLI,它不支持SKILLS、Sub Agent目前还是追赶者,但<font color="#00FF00">它最强的效果在于和自家的GPT整合效果非常强</font>  
CodeX的客户端目前只支持mac  

5.IFlow  

6.KimiCLI

7.Cursor  
<font color="#00FF00">vibe coding</font>的鼻祖,整合了大量的国外/国产模型,例如OpenAI-GPT-5.2、Anthropic-Claude 4.5/4.6Opus、Google-Gemini 3 Pro  
它的卖点就是Composer模式(Agent模式),可以全局改文件、可视化确认、Tab补全,Cursor本身并不提供模型,但就是它能自动帮你修改代码这一功能它要卖你钱,如果你用自已的api-key,依旧可以聊天,但它的这一整套Agent功能你完全无法使用  

8.Trae  
字节推出的IDE,基于vscode,内置模型为豆包,可以切换到其它不同的模型  
它的特点是高级模型的价格非常便宜,是Cursor的竞品,它的卖点也是Agent哪一套,能够自动全局修改文件、TAB补全,但它的模型并不全面,基本只有国产模型  

9.Qoder  
阿里推出的一个IDE,特点是<font color="#00FF00">原生支持JetBrains的IDE、上下文长度很长(有10万+)</font>  


9.Clawdbot、Moltbot、OpenClaw  
开源的桌面客户端,提供了比网页版更强的功能,比如支持本地知识库挂载、长对话管理,或者是绕过某些限制的API调用界面  


10.小总结  
* ⭐️Claude Code+Claude 4.5 Sonnet / 4.6 Opus(这套搭配地表最强)  
* ⭐️CodeX + GPT(也很强,但比Claude更省钱)  
* ⭐️OpenCode + deepseek R1/GLM4.7
  (开源+不绑定特定模型,这个可能不符合我胃口,可以一步到位用Claude,反正最后还得是用具体模型,而且现在OpenCode也不支持Claude了)  
  这个如果使用国内的deepseek模型,它的性价比是极高的,如果非常在意成本,这个很省钱  
  也可以切换为GLM来使用,GLM也非常不错
* ⭐️Cursor(AI-IDE无脑选这个就行了)  
* ⭐️Qoder(如果是jetbrains可以用)  
* Trae(价格比Cursor便宜,但没有Claude模型,需要下载国际版,可能存在token消耗过快的问题,实测会浪费token生成无意义的内容)  

## 2.学习路线  
**目录:**  
2.1 基本介绍  


### 2.1 基本介绍  
1.大模型应用开发  
和传统AI开发不同‍‍‍‍‍,大模型应用开发的核心不是从头训练模型,而是<font color="#00FF00">通过工程化手段释放现成模型的潜力</font>,这就像⁡⁡⁡⁡⁡组装乐高积木——开发者需要巧妙组合Prom​​​​​pt工程、向量数据库、业务逻辑等模块,将通用大模型训练为特定场景的解决方案  
AI应用开发的关键,<font color="#00FF00">不是研究AI本身,而是学会如何围绕AI设计出好用的产品</font>  

2.学习路线  
大模型基础>AI大模型和RAG应用开发工程>大模型Agent应用架构>大模型微调和私有化部署  






