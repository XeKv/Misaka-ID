# 御坂网络计数器

一个用于查找 Bilibili 上御坂妹数量的小程序。do，御坂如是说到。

### 主要特点

- 支持 Lv2 以下、未绑定手机的用户的搜索[^1]
- User-Agent 的伪装 （假装自己是浏览器）
- 对B站服务器友好（可以根据需求修改）
- 完善的异常处理机制
- 自动保存结果
- 运行完成后的微信通知（server酱）
- 支持了命令行参数（详情可以通过 -h 来获取）

[^1]: 通过B站注册页面中，“昵称查重”实现。

命令行参数如下:
```text
    -r [--range]       编号检测范围(闭区间,英文逗号分隔) 
                           例如: --range=1,200    表示从 1 检测到 200
    -p [--prefix]      名称前缀 默认为"御坂"
    -s [--suffix]      名称后缀 默认为"号"
    -z [--zfill]       将编号补齐的位数
                           例如: --zfill=5        会将 1 补齐为 00001
    -k [--key]         用于 "server酱" 推送的sckey (push token)
    -f [--filename]    用于设置保存结果的文件名 默认为 lists.txt
    
    --msg_title        自定义推送消息的标题 默认为 "Misaka-ID"
    --msg_context      自定义推送消息的正文
```
使用示例:

```shell
# 后台执行 & 重定向标准输出到文件 & 结果输出为文件 & 指定范围及消息标题
nohup python3 -u main.py -r 0,999 -z 4 -f lists-zfill4-20220628.txt --msg_title="zfill4" & > zf4.out
```

### 特别说明

该程序采用在 B站注册页面中的“昵称查重” 中判断用户是否存在，仅仅支持精确判断指定格式的id。

> 精确格式如下：
> 前缀 + xxx + 后缀
> 
> 其中 xxx 的范围是 可以自定义
>
> xxx 的位数也可以自定义。例如，可以检测 御坂167号 或者 御坂00167号

***实际上，若不严格考虑格式，哔哩哔哩上的御坂妹会更多哦~***

---

<details>
<summary>悄悄告诉你……（点击可展开）</summary>
<br>
0~20000号标准格式的御坂妹 7207 个.（2020.07.16）
<br>
编号前补"0"的御坂妹结果如下（2020.07.17）:
<ul>
<li>补为5位数的有 691 只（形如"御坂00123号"）</li>
<li>补为4位数的有 124 只（形如"御坂0123号"）</li>
<li>补为3位数的有 20 只（形如"御坂012号"）</li>
<li>补为2位数的有 9 只（形如"御坂01号"）</li>
</ul>
<br>
<b>上述御坂总计 8051 只，实际数量会更多一些</b>
<br><br>
<del>另外据其他小伙伴统计，<u>各种形式的御坂大约共有 10361+.（2020.04.19）</u></del>
<br><br>
do，御坂经过一番仔细搜索后开心地说道
</details> 
