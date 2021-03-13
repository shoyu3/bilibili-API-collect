# 获取b23.tv短链

- [获取b23.tv短链](#获取b23.tv短链)

---

## 获取b23.tv短链

> http://api.bilibili.com/x/report/click/now 

*请求方式：POST*

**正文参数（ application/x-www-form-urlencoded ）：**

| 参数名   | 类型 | 内容         | 必要性 | 备注                          |
| -------- | ---- | ------------ | ------ | ----------------------------- |
| build | num  | 9331 | 必要 | 大于9300的值均可，如9301, 9320, 9330 |
| bvuid | str  | 32位字母与数字的组合 | 必要 | 具体含义未知，如qp92wvbiiwercf5au381g1bzajou85hg |
| oid | str | B站站内链接 | 必要 | 必须是B站站内链接 |
| platform | str | ios或android | 必要 | 分享平台 |
| share_channel | str | COPY | 必要 |      |
| share_id | str | public.webview.0.0.pv或main.ugc-video-detail.0.0.pv | 必要 | 一般选择public.webview.0.0.pv，可以生成所有站内链接 |
| share_mode | num | 3 | 必要 | 似乎大于0的数字均可 |

**json回复：**

根对象：

| 字段    | 类型 | 内容     | 备注    |
| ------- | ---- | -------- | ------- |
| code    | num  | 返回值   | 0：成功 |
| message | str  | 错误信息 | 默认为0 |
| ttl     | num  | 1        |         |
| data    | obj  | 信息本体 |         |

`data`对象：

| 字段 | 类型 | 内容         | 备注 |
| ---- | ---- | ------------ | ---- |
| content  | str  | https:‬//b23.tv开头的短链 | 传入的长链必须为B站站内链接，否则无此字段 |

**示例：**

生成`https://www.bilibili.com/`的短链

```shell
curl 'https://api.bilibili.com/x/share/click'\
--data-urlencode 'build=9331'\
--data-urlencode 'bvuid=qp92wvbiiwercf5au381g1bzajou85hg'\
--data-urlencode 'oid=https://www.bilibili.com/'\
--data-urlencode 'platform=android'\
--data-urlencode 'share_channel=COPY'\
--data-urlencode 'share_id=public.webview.0.0.pv'\
--data-urlencode 'share_mode=3'
```

<details>

<summary>查看响应示例：</summary>

```json
{
	"code": 0,
	"message": "0",
	"ttl": 1,
	"data": {
		"content": "https://b23.tv/El8pMD"
	}
}
```

</details>
