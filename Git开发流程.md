---


---

<h1 id="分支类型">分支类型</h1>
<ul>
<li><strong>master</strong>：版本发布分支（保护）</li>
<li><strong>trunk</strong>：开发主分支（保护）</li>
<li><strong>develop</strong>：迭代分支</li>
<li><strong>sit</strong>：sit分支</li>
<li><strong>release</strong>：预发布分支</li>
<li><strong>bugfix</strong>：紧急修复分支</li>
</ul>
<blockquote>
<p>受保护的分支，只有git管理人员有提交权限，其他分支所有人都有提交权限</p>
</blockquote>
<blockquote>
<p>除master和trunk外，其他分支命名格式为{type}_{date}_{summary}，其中date格式为yyyyMMdd</p>
</blockquote>
<h1 id="角色">角色</h1>
<ul>
<li><strong>项目管理员</strong>：负责一个项目迭代中的功能点改动跟踪（包括当次迭代涉及的所有develop分支），合并develop分支至trunk，拉取sit分支，合并sit分支至trunk，拉取release分支，并在关键时间点通知其他开发中的develop分支同步trunk</li>
<li><strong>开发人员</strong>：负责在develop，sit等分支上进行开发，并在项目进入下一阶段前通知管理员进行代码合并</li>
</ul>
<h1 id="流程">流程</h1>
<p><img src="https://github.com/Ryan-Hu/aaa/blob/master/git.jpg?raw=true" alt="enter image description here"><br>
1.<strong>开发</strong>：通常情况下，一个迭代或独立功能对应一个develop分支，develop分支可同时有多个人进行开发，develop分支从master分支上拉取</p>
<blockquote>
<p>为了减少冲突风险，开发过程中尽量每天提交一次代码</p>
</blockquote>
<blockquote>
<p>如果有独立功能并不确定会在该迭代中上线，也可单独拉develop分支进行开发</p>
</blockquote>
<blockquote>
<p>从develop分支上同步代码应该使用rebase，而不是merge</p>
</blockquote>
<p>2.<strong>STABLE测试</strong>：提交测试前，如果涉及到多个develop分支的功能，则先把所有相关develop分支合并至一个新的develop分支，保证功能完整性，然后提交测试测试，测试中的所有问题修改仍在develop上进行</p>
<p>3.<strong>SIT阶段</strong>：进入SIT测试之前，开发人员先将develop与trunk同步，然后发起megre request给项目对应的管理员，由管理员确认无误后，将代码合并至trunk，合并后立即拉取sit分支，原develop分支立即关闭提交，进入sit测试后，所有的修改只能在sit分支上进行，如果之后有其他develop分支需要合并，则直接合到sit分支</p>
<blockquote>
<p>管理员合并前需确认当前develop已经与trunk同步，确保合并为fast forword，否则通知开发人员修改后重新提交merge request</p>
</blockquote>
<blockquote>
<p>管理员合并前需安排人员再次对代码进行审核，如发现问题，则通知开发人员修改后重新提交merge request</p>
</blockquote>
<p>4.<strong>预发阶段</strong>：进入预发阶段，开发人员再次发送merge request给管理员，管理员审核代码无误后，将sit分支合并至trunk，合并后立即拉取relese分支，原sit分支立即关闭，后续代码修改只能在release分支上进行</p>
<blockquote>
<p>在整个<strong>sit和预发阶段</strong>，管理员需确保不会有其他代码提交至trunk，合并时如果不是fast forward，则需重新检查trunk上的代码提交记录</p>
</blockquote>
<p>4.<strong>发布完毕</strong>：管理人员将release分支合并至master和trunk，并打上对应的版本标签</p>
<blockquote>
<p>管理员要保证在trunk上所有的迭代是串行的，即不能有多个迭代在trunk上同时进入sit或预发布<br>
<img src="https://github.com/Ryan-Hu/aaa/blob/master/git3.jpg?raw=true" alt="enter image description here"></p>
</blockquote>
<p>5.<strong>线上问题</strong>：如线上版本出现问题需要紧急修复，由开发人员从master分支上拉取bugfix分支，问题修复测试通过之后，向管理员发送merge request，由管理员同步至master和trunk，并打上相应标签，如果此时有正在测试中的分支，通知相关开发人员合并至对应的sit或release分支</p>
<blockquote>
<p>trunk上有更新时，合并至sit或release应使用rebase<br>
<img src="https://github.com/Ryan-Hu/aaa/blob/master/git2.jpg?raw=true" alt="enter image description here"></p>
</blockquote>

