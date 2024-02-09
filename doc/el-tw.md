### 《鳥盾》表達式手冊
### 基本格式 `處理動作 權重 \\ 條件表達式`
- 例如：`skip1000\\blue&fi`  
  代表，在滿足 `是藍V 且 在關注` 條件時  
  `跳過(skip)後續所有規則`  
  權重值為 `1000`，值越大，越先執行

### 表達式元素
<table>
    <tr>
        <th>分類</th>
        <th>適用場景</th>
        <th>字段名稱</th>
        <th>字段縮寫</th>
        <th>字段描述</th>
        <th>值格式</th>
        <th>支持運算符</th>
        <th>範例</th>
    </tr>
    <tr>
        <td rowspan="8">條件類型</td>
        <td rowspan="5">攔截<br/>與<br/>搜索</td>
        <td>blue</td>
        <td></td>
        <td>是否藍V</td>
        <td rowspan="8"></td>
        <td rowspan="8"><code>!</code>:取反值</td>
        <td rowspan="8"><code>!blue&!fb</code><br/>不是藍V並且不是粉絲</td>
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
        <td>已關注</td>
    </tr>
    <tr>
        <td>followed_by</td>
        <td>fb</td>
        <td>粉絲</td>
    </tr>
    <tr>
        <td rowspan="3">僅搜索</td>
        <td>private</td>
        <td></td>
        <td>未共享</td>
    </tr>
    <tr>
        <td>suspended</td>
        <td>sd</td>
        <td>已凍結</td>
    </tr>
    <tr>
        <td>removed</td>
        <td>rd</td>
        <td>已消號</td>
    </tr>
    <tr>
        <td rowspan="4">數字類型</td>
        <td rowspan="4">攔截<br/>與<br/>搜索</td>
        <td>followers_count</td>
        <td>foc</td>
        <td>粉絲數</td>
        <td rowspan="4"><code>123</code>:整數</td>
        <td rowspan="4">
<code>&lt;</code><br/>
<code>&lt;=</code><br/>
<code>&gt;</code><br/>
<code>&gt;=</code><br/>
<code>!=</code><br/>
<code>≠</code><br/>
</td>
        <td rowspan="4"><code>!blue&frc<100</code><br/>不是藍V並且關注數小於100</td>
    </tr>
    <tr>
        <td>friends_count</td>
        <td>frc</td>
        <td>關注數</td>
    </tr>
    <tr>
        <td>photos_count</td>
        <td>ptc</td>
        <td>推文含圖片數</td>
    </tr>
    <tr>
        <td>videos_count</td>
        <td>vdc</td>
        <td>推文含視頻數</td>
    </tr>
    <tr>
        <td rowspan="2">日期類型</td>
        <td>攔截<br/>與<br/>搜索</td>
        <td>created_date</td>
        <td>cd</td>
        <td>用戶註冊日期</td>
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
<code>&gt;</code>:在之後<br/>
<code>&gt;=</code><br/>
<code>=</code><br/>
</td>
        <td rowspan="2"><code>cd<1m</code><br/>註冊日期小於一月</td>
    </tr>
    <tr>
        <td>僅搜索</td>
        <td>added_date</td>
        <td>ad</td>
        <td>添加數據日期</td>
    </tr>
    <tr>
        <td rowspan="2">時間類型</td>
        <td>攔截<br/>與<br/>搜索</td>
        <td>created_time</td>
        <td>ct</td>
        <td>用戶註冊時間</td>
        <td rowspan="2">
<code>2</code>:2小時<br/>
<code>1d</code>:1天<br/>
</td>
        <td rowspan="2">
<code>&lt;</code>:在之前<br/>
<code>&gt;</code>:在之後<br/>
</td>
        <td rowspan="2"><code>ad<8</code><br/>8小時內添加的數據</td>
    </tr>
    <tr>
        <td>僅搜索</td>
        <td>added_time</td>
        <td>at</td>
        <td>添加數據日間</td>
    </tr>
    <tr>
        <td rowspan="9">文本類型</td>
        <td rowspan

="8">攔截<br/>與<br/>搜索</td>
<td>name</td>
<td>@</td>
<td>用戶名稱</td>
<td rowspan="10">
<code>abc</code>:任意文本<br/>
<code>公務員</code><br/><br/>
<code>/市/</code>:正則<br/>(僅支持<code>=</code><code>!=</code><code>≠</code>)<br/>
</td>
        <td rowspan="10">
<code>=</code>:完全等同<br/>
<code>≠</code>:不等同<br/>
<code>!=</code>:不等同<br/>
<code>^=</code>:以什麼開始<br/>
<code>$=</code>:以什麼結束<br/>
<code>*=</code>:包含什麼<br/>
</td>
        <td rowspan="10">
<code>@*=市</code><br/>用戶名稱包含'市'<br/><br/>
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
        <td>用戶描述</td>
    </tr>
    <tr>
        <td>urls,links</td>
        <td>url,link</td>
        <td>所有包含的連結</td>
    </tr>
    <tr>
        <td>tweet_text</td>
        <td>txt</td>
        <td>推文正文</td>
    </tr>
    <tr>
        <td>tweet_lang</td>
        <td>lang</td>
        <td>推文語言</td>
    </tr>
    <tr>
        <td>any</td>
        <td></td>
        <td>任意文本(默認匹配)</td>
    </tr>
    <tr>
        <td>verified_type</td>
        <td>vtp</td>
        <td>認證類型</td>
    </tr>
    <tr>
        <td>僅搜索</td>
        <td>category</td>
        <td>ctg</td>
        <td>分類類別</td>
    </tr>
</table>
