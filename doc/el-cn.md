## 《鸟盾》表达式手册
### 安装
- [Chrome市场](https://chromewebstore.google.com/detail/%E6%8E%A8%E7%89%B9%E9%B8%9F%E7%9B%BE/igapbfjkbkmjcmgjmgfcegamhkfppdmg?hl=zh-CN)  
- [Edge市场](https://microsoftedge.microsoft.com/addons/detail/%E6%8E%A8%E7%89%B9%E9%B8%9F%E7%9B%BE/copkjadjjcbkgclndhlhdbmhdabhfmed)  
### 基本格式 `处理动作 权重 \\ 条件表达式`  
- 如:`skip1000\\blue&fi`  
  代表,当满足 `是蓝V 且 在关注` 条件时  
  `跳过(skip)后续所有规则`  
  权重值为`1000`,值越大,越先执行
- 支持 与`&`、或`|`、 非`!` 逻辑运算  
  支持使用 括号 `()`调整运算优先级  
  默认优先级为 `!` 先于 `&` 先于 `|`  
  如:`@*=市&(foc<10|cd<1w)`  
  昵称包含'市' 且 (粉丝数<10 或 注册日期小于1周)
- 支持处理动作
  1. `block` 拉黑
  2. `filter` 过虑后手功确认
  3. `mark` 在正文中标记
  4. `skip` 跳过后续规则
### 表达式元素
<table>
    <tr>
        <th>分类</th>
        <th>适用场景</th>
        <th>字段名称</th>
        <th>字段缩写</th>
        <th>字段描述</th>
        <th>值格式</th>
        <th>支持运算符</th>
        <th>范例</th>
    </tr>
    <tr>
        <td rowspan="8">条件类型</td>
        <td rowspan="5">拦截<br/>与<br/>搜索</td>
        <td>blue</td>
        <td></td>
        <td>是否蓝V</td>
        <td rowspan="8"></td>
        <td rowspan="8"><code>!</code>:取反值</td>
        <td rowspan="8"><code>!blue&!fb</code><br/>不是蓝V并且不是粉丝</td>
    </tr>
    <tr>
        <td>blocking</td>
        <td></td>
        <td>已拉黑他</td>
    </tr>
    <tr>
        <td>blocked_by</td>
        <td></td>
        <td>被其拉黑</td>
    </tr>
    <tr>
        <td>following</td>
        <td>fi</td>
        <td>已关注</td>
    </tr>
    <tr>
        <td>followed_by</td>
        <td>fb</td>
        <td>粉丝</td>
    </tr>
    <tr>
        <td rowspan="3">仅搜索</td>
        <td>private</td>
        <td></td>
        <td>未共享</td>
    </tr>
    <tr>
        <td>suspended</td>
        <td>sd</td>
        <td>已冻结</td>
    </tr>
    <tr>
        <td>removed</td>
        <td>rd</td>
        <td>已消号</td>
    </tr>
    <tr>
        <td rowspan="4">数字类型</td>
        <td rowspan="4">拦截<br/>与<br/>搜索</td>
        <td>followers_count</td>
        <td>foc</td>
        <td>粉丝数</td>
        <td rowspan="4"><code>123</code>:整数</td>
        <td rowspan="4">
<code>&lt;</code><br/>
<code>&lt;=</code><br/>
<code>&gt;</code><br/>
<code>&gt;=</code><br/>
<code>!=</code><br/>
<code>≠</code><br/>
</td>
        <td rowspan="4"><code>!blue&frc<100</code><br/>不是蓝V并且关注数小于100</td>
    </tr>
    <tr>
        <td>friends_count</td>
        <td>frc</td>
        <td>关注数</td>
    </tr>
    <tr>
        <td>photos_count</td>
        <td>ptc</td>
        <td>推文含图片数</td>
    </tr>
    <tr>
        <td>videos_count</td>
        <td>vdc</td>
        <td>推文含视频数</td>
    </tr>
    <tr>
        <td rowspan="2">日期类型</td>
        <td>拦截<br/>与<br/>搜索</td>
        <td>created_date</td>
        <td>cd</td>
        <td>用户注册日期</td>
        <td rowspan="2">
<code>2</code>:2天<br/>
<code>1d</code>:1天<br/>
<code>1w</code>:1周<br/>
<code>1m</code>:1月<br/>
<code>1y</code>:1年<br/>
<code>1-5</code>:1月5日<br/>
<code>2023-1-1</code><br/>
</td>
        <td rowspan="2">
<code>&lt;</code>:在之前<br/>
<code>&lt;=</code><br/>
<code>&gt;</code>:在之后<br/>
<code>&gt;=</code><br/>
<code>=</code><br/>
</td>
        <td rowspan="2"><code>cd<1m</code><br/>注册日期小于一月</td>
    </tr>
    <tr>
        <td>仅搜索</td>
        <td>added_date</td>
        <td>ad</td>
        <td>添加数据日期</td>
    </tr>
    <tr>
        <td rowspan="2">时间类型</td>
        <td>拦截<br/>与<br/>搜索</td>
        <td>created_time</td>
        <td>ct</td>
        <td>用户注册时间</td>
        <td rowspan="2">
<code>2</code>:2小时<br/>
<code>1d</code>:1天<br/>
</td>
        <td rowspan="2">
<code>&lt;</code>:在之前<br/>
<code>&gt;</code>:在之后<br/>
</td>
        <td rowspan="2"><code>ad<8</code><br/>8小时内添加的数据</td>
    </tr>
    <tr>
        <td>仅搜索</td>
        <td>added_time</td>
        <td>at</td>
        <td>添加数据日间</td>
    </tr>
    <tr>
        <td rowspan="9">文本类型</td>
        <td rowspan="8">拦截<br/>与<br/>搜索</td>
        <td>name</td>
        <td>@</td>
        <td>用户名称</td>
        <td rowspan="10">
<code>abc</code>:任意文本<br/>
<code>公务员</code><br/><br/>
<code>/市/</code>:正则<br/>(仅支持<code>=</code><code>!=</code><code>≠</code>)<br/>
</td>
        <td rowspan="10">
<code>=</code>:完全等同<br/>
<code>≠</code>:不等同<br/>
<code>!=</code>:不等同<br/>
<code>^=</code>:以什么开始<br/>
<code>$=</code>:以什么结束<br/>
<code>*=</code>:包含什么<br/>
</td>
        <td rowspan="10">
<code>@*=市</code><br/>用户名包含'市'<br/><br/>
<code>lang^=zh</code><br/>推文是中文<br/><br/>
<code>abc&xyz</code><br/>任意文本包含'abc'和'xyz'<br/><br/>
</td>
    </tr>
    <tr>
        <td>screen_name</td>
        <td>sn</td>
        <td>英文ID</td>
    </tr>
    <tr>
        <td>description</td>
        <td>desc,info</td>
        <td>用户描述</td>
    </tr>
    <tr>
        <td>urls,links</td>
        <td>url,link</td>
        <td>所有包含的链接</td>
    </tr>
    <tr>
        <td>tweet_text</td>
        <td>txt</td>
        <td>推文正文</td>
    </tr>
    <tr>
        <td>tweet_lang</td>
        <td>lang</td>
        <td>推文语言</td>
    </tr>
    <tr>
        <td>any</td>
        <td></td>
        <td>任意文本(默认匹配)</td>
    </tr>
    <tr>
        <td>verified_type</td>
        <td>vtp</td>
        <td>认证类型</td>
    </tr>
    <tr>
        <td>仅搜索</td>
        <td>category</td>
        <td>ctg</td>
        <td>分类类别</td>
    </tr>
</table>