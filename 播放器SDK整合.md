---


---

<h3 id="存在的问题">存在的问题</h3>
<ol>
<li>线上版本的播放器使用软解码，比较耗cpu资源，在低端机上可能存在性能问题（使用硬解cpu占用量比软解少50%以上）</li>
</ol>

<table>
<thead>
<tr>
<th></th>
<th>阿里SDK</th>
<th>腾讯SDK</th>
<th>Google ExoPlayer</th>
</tr>
</thead>
<tbody>
<tr>
<td>软解</td>
<td>ffmpeg</td>
<td>支持</td>
<td>支持</td>
</tr>
<tr>
<td>硬解</td>
<td>不支持</td>
<td>支持(内部集成EXO)</td>
<td>支持</td>
</tr>
</tbody>
</table><ol start="2">
<li>播放器部分错误事件回调缺失，导致播异常时不能正确的通知用户(黑屏)</li>
<li>阿里和腾讯播放器不开源，定位问题困难，即使有问题也无法解决</li>
<li>腾讯SEI有性能问题</li>
<li>直播和录播封装不统一，后期维护成本加大</li>
</ol>
<h3 id="解决方案">解决方案</h3>
<ol>
<li>封装原有的两套播放器，新加入ExoPlayer作为补充</li>
<li>标准化直播/录播的播放状态和事件</li>
<li>增加播放器内部状态相关日志上报</li>
</ol>
<h3 id="关于exoplayer">关于ExoPlayer</h3>
<p>ExoPlayer是Google官方提供的完整播放器解决方案，用于解决系统自带的MediaPlayer扩展性不好的问题，其硬解功能基于Android 19以上版本系统自带的MediaCodec模块，兼容性已得到开源社区的验证，目前市面上主流的播放器，如<em>ijkplayer</em>，腾讯播放器SDK都集成了Exo作为硬解码的实现方案<br>
该项目完全开源，有强大的的扩展能力，支持市面上所有的主流视频格式，更可根据自身业务需求定制能力，为将来业务发展提供更好的支持</p>

