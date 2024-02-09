## 《鳥盾》Expression Handbook
### Basic Format `Action Weight \\ Conditional Expression`
- For example: `skip1000\\blue&fi`  
  Represents, when the condition `is Blue V and in Following` is satisfied  
  `Skip (skip) all subsequent rules`  
  The weight is `1000`, the higher the value, the earlier it executes.
- Supports logical operations: AND `&`, OR `|`, NOT `!`  
  Supports the use of parentheses `()` to adjust the operation priority  
  The default priority is `!` before `&` before `|`  
  For example: `@*=City&(foc<10|cd<1w)`  
  Nickname contains 'City' and (followers < 10 or registration date is less than 1 week)
- Supports actions
  1. `block` Block
  2. `filter` Filter and manually confirm later
  3. `mark` Mark in the text
  4. `skip` Skip subsequent rules

### Expression Elements
<table>
    <tr>
        <th>Category</th>
        <th>Applicable Scene</th>
        <th>Field Name</th>
        <th>Field Abbreviation</th>
        <th>Field Description</th>
        <th>Value Format</th>
        <th>Support Operators</th>
        <th>Example</th>
    </tr>
    <tr>
        <td rowspan="8">Condition Type</td>
        <td rowspan="5">Intercept<br/>and<br/>Search</td>
        <td>blue</td>
        <td></td>
        <td>Is Blue V</td>
        <td rowspan="8"></td>
        <td rowspan="8"><code>!</code>: Negation</td>
        <td rowspan="8"><code>!blue&!fb</code><br/>Not Blue V and not a follower</td>
    </tr>
    <tr>
        <td>blocking</td>
        <td></td>
        <td>Blocked by</td>
    </tr>
    <tr>
        <td>blocked_by</td>
        <td></td>
        <td>Blocked by user</td>
    </tr>
    <tr>
        <td>following</td>
        <td>fi</td>
        <td>Is Following</td>
    </tr>
    <tr>
        <td>followed_by</td>
        <td>fb</td>
        <td>Follower</td>
    </tr>
    <tr>
        <td rowspan="3">Search Only</td>
        <td>private</td>
        <td></td>
        <td>Not Shared</td>
    </tr>
    <tr>
        <td>suspended</td>
        <td>sd</td>
        <td>Suspended</td>
    </tr>
    <tr>
        <td>removed</td>
        <td>rd</td>
        <td>Account Removed</td>
    </tr>
    <tr>
        <td rowspan="4">Numeric Type</td>
        <td rowspan="4">Intercept<br/>and<br/>Search</td>
        <td>followers_count</td>
        <td>foc</td>
        <td>Follower Count</td>
        <td rowspan="4"><code>123</code>: Integer</td>
        <td rowspan="4">
<code>&lt;</code><br/>
<code>&lt;=</code><br/>
<code>&gt;</code><br/>
<code>&gt;=</code><br/>
<code>!=</code><br/>
<code>≠</code><br/>
</td>
        <td rowspan="4"><code>!blue&frc<100</code><br/>Not Blue V and follower count less than 100</td>
    </tr>
    <tr>
        <td>friends_count</td>
        <td>frc</td>
        <td>Following Count</td>
    </tr>
    <tr>
        <td>photos_count</td>
        <td>ptc</td>
        <td>Tweets with Photos Count</td>
    </tr>
    <tr>
        <td>videos_count</td>
        <td>vdc</td>
        <td>Tweets with Videos Count</td>
    </tr>
    <tr>
        <td rowspan="2">Date Type</td>
        <td>Intercept<br/>and<br/>Search</td>
        <td>created_date</td>
        <td>cd</td>
        <td>User Registration Date</td>
        <td rowspan="2">
<code>2</code>: 2 days<br/>
<code>1d</code>: 1 day<br/>
<code>1w</code>: 1 week<br/>
<code>1m</code>: 1 month<br/>
<code>1y</code>: 1 year<br/>
<code>1-5</code>: January 5th<br/>
<code>2023-1-1</code><br/>
</td>
        <td rowspan="2">
<code>&lt;</code>: Before<br/>
<code>&lt;=</code><br/>
<code>&gt;</code>: After<br/>
<code>&gt;=</code><br/>
<code>=</code><br/>
</td>
        <td rowspan="2"><code>cd<1m</code><br/>Registration date less than one month</td>
    </tr>
    <tr>
        <td>Search Only</td>
        <td>added_date</td>
        <td>ad</td>
        <td>Data Addition Date</td>
    </tr>
    <tr>
        <td rowspan="2">Time Type</td>
        <td>Intercept<br/>and<br/>Search</td>
        <td>created_time</td>
        <td>ct</td>
        <td>User Registration Time</td>
        <td rowspan="2">
<code>2</code>: 2 hours<br/>
<code>1d</code>: 1 day<br/>
</td>
        <td rowspan="2">
<code>&lt;</code>: Before<br/>
<code>&gt;</code>: After<br/>
</td>
        <td rowspan="2"><code>ad<8</code><br/>Data added within 8 hours</td>
    </tr>
    <tr>
        <td>Search Only</td>
        <td>added_time</td>
        <td>at</td>
        <td>Data Addition Time</td>
    </tr>
    <tr>
        <td rowspan="9">Text Type</td>
        <td rowspan="8">Intercept<br/>and<br/>Search</td>
        <td>name</td>
        <td>@</td>
        <td>User Name</td>
        <td rowspan="10">
<code>abc</code>: Any text<br/>
<code>公務員</code><br/><br/>
<code>/市/</code>: Regex<br/>(Supports only <code>=</code><code>!=</code><code>≠</code>)<br/>
</td>
        <td rowspan="10">
<code>=</code>: Exactly equal<br/>
<code>≠</code>: Not equal<br/>
<code>!=</code>: Not equal<br/>
<code>^=</code>: Starts with<br/>
<code>$=</code>: Ends with<br/>
<code>*=</code>: Contains<br/>
</td>
        <td rowspan="10">
<code>@*=市</code><br/>User name contains '市'<br/><br/>
<code>lang^=zh</code><br/>Tweets in Chinese<br/><br/>
<code>abc&xyz</code><br/>Any text contains 'abc' and 'xyz'<br/><br/>
</td>
    </tr>
    <tr>
        <td>screen_name</td>
        <td>sn</td>
        <td>English ID</td>
    </tr>
    <tr>
        <td>description</td>
        <td>desc,info</td>
        <td>User Description</td>
    </tr>
    <tr>
        <td>urls,links</td>
        <td>url,link</td>
        <td>All Included Links</td>
    </tr>
    <tr>
        <td>tweet_text</td>
        <td>txt</td>
        <td>Tweet Text</td>
    </tr>
    <tr>
        <td>tweet_lang</td>
        <td>lang</td>
        <td>Tweet Language</td>
    </tr>
    <tr>
        <td>any</td>
        <td></td>
        <td>Any Text (Default Match)</td>
    </tr>
    <tr>
        <td>verified_type</td>
        <td>vtp</td>
        <td>Verification Type</td>
    </tr>
    <tr>
        <td>Search Only</td>
        <td>category</td>
        <td>ctg</td>
        <td>Category</td>
    </tr>
</table>