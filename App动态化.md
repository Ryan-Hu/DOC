---


---

<h1 id="动态化">动态化</h1>
<h2 id="目标">目标</h2>
<p>实现app内容布局的动态下发</p>
<ul>
<li>轻量级</li>
<li>平台无关</li>
</ul>
<h2 id="方案参考">方案参考</h2>
<ul>
<li>知乎：<a href="https://www.infoq.cn/article/RRvP-Kli8AwEx6TuB1aG?utm_source=rss&amp;utm_medium=article">https://www.infoq.cn/article/RRvP-Kli8AwEx6TuB1aG?utm_source=rss&amp;utm_medium=article</a></li>
</ul>
<h2 id="技术实现">技术实现</h2>
<h3 id="模板">模板</h3>
<ul>
<li>格式
<ul>
<li>json</li>
<li>ymal</li>
</ul>
</li>
<li>下发方式</li>
<li>版本控制</li>
</ul>
<h2 id="布局">布局</h2>
<ul>
<li>控件标准：定义一套通用的控件格式标准，各端实现标准控件到原生的映射
<ul>
<li>标准容器：List，Slider，Grid …</li>
<li>卡片布局：FlexLayout(android) / YogaKit(ios)</li>
<li>基础空间：Text，Image …</li>
</ul>
</li>
</ul>
<h2 id="逻辑表达式">逻辑表达式</h2>
<p>简单的数据和布局绑定，往往无法满足业务需求，需要在模板中包含一定的逻辑描述（布局逻辑，非业务逻辑）</p>
<p>考虑使用表达式解析方案：</p>
<ul>
<li>成熟方案
<ul>
<li>Apache Commons JEXL： 基于jvm的表达式解析库<a href="https://commons.apache.org/proper/commons-jexl/reference/syntax.html">https://commons.apache.org/proper/commons-jexl/reference/syntax.html</a><br>
优点：功能完善，可扩展，满足大部分<br>
缺点：只支持java，js，kotlin，python</li>
<li>Google Common Expression Language：跨平台的表达式规范<a href="https://github.com/google/cel-spec">https://github.com/google/cel-spec</a><br>
优点：跨平台<br>
缺点：只支持bool结果</li>
</ul>
</li>
<li>自研方案<br>
可参考JEXL，前期实现小部分简单语法</li>
</ul>
<h2 id="异常处理">异常处理</h2>
<ul>
<li>解析异常处理</li>
<li>灰度</li>
<li>报警</li>
</ul>

