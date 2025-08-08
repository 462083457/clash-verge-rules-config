# 全局配置扩展

```yaml
my-rules:
 - RULE-SET,google,proxy                        #google
 - RULE-SET,proxy,proxy                         #代理域名列表
 - RULE-SET,tld-not-cn,proxy                    #非中国大陆使用的顶级域名
 - RULE-SET,gfw,proxy                           #GFWList
 - RULE-SET,telegramcidr,proxy                  #Telegram 使用的 IP 地址
 - RULE-SET,icloud,chinese                      #icloud
 - RULE-SET,apple,chinese                       #apple
 - RULE-SET,applications,chinese                #需要直连的常见软件
 - RULE-SET,private,chinese                     #私有网络专用域名列表
 - RULE-SET,direct,chinese                      #直连域名列表
 - RULE-SET,lancidr,chinese                     #局域网 IP 及保留 IP 地址列表
 - RULE-SET,cncidr,chinese                      #中国大陆 IP 地址列表
 - DOMAIN,clash.razord.top,chinese              #
 - DOMAIN,yacd.haishan.me,chinese               #
 - RULE-SET,reject,reject                       #广告域名列表

#自制代理组 🇯🇵 日本  🇯🇵 日本下载专用  🇷🇺 俄罗斯
ikuuu-map:
  proxy: 🔰 选择节点
  chinese:  🇨🇳 国内网站
  reject: 🛑 拦截广告
  download: 🇯🇵 日本下载专用
  Jp: 🇯🇵 日本
  Ru: 🇷🇺 俄罗斯

yi-yuan-map:
  proxy: 一元机场
  chinese: 一元机场
  reject: 一元机场
  download: 🇯🇵 日本
  Jp: 🇯🇵 日本
  Ru: 🇯🇵 日本

# 前置代理组
iKuuu-group: 
 - type: 'select'
   name: '🇷🇺 俄罗斯'
   proxies:
     - '🇷🇺 俄罗斯Y01'
 - type: 'select'
   name: ' 🇯🇵 日本'
   proxies:
     - '🇯🇵 日本Y01'
     - '🇯🇵 日本Y02 | IEPL'
     - '🇯🇵 日本Y03 | IEPL'
     - '🇯🇵 日本Y04 | IEPL'
     - '🇯🇵 日本Y05 | 下载专用 | x0.01'
     - '🇯🇵 日本Y06 | 下载专用 | x0.01'
     - '🇯🇵 日本Y07 | x0.8'
     - '🇯🇵 日本Y08 | x0.8'
     - '🇯🇵 日本Y09 | IEPL'
     - '🇯🇵 日本Y10 | IEPL'
     - '🇯🇵 日本Y11 | IEPL'
     - '🇯🇵 免费-日本1-Ver.7'
     - '🇯🇵 免费-日本2-Ver.8'
     - '🇯🇵 免费-日本3-Ver.7'
     - '🇯🇵 免费-日本4-Ver.8'
     - '🇯🇵 免费-日本5-Ver.9'
     - '🇯🇵 免费-日本6-Ver.8'
     - '🇯🇵 免费-日本7-Ver.2'
 - type: 'select'
   name: ' 🇯🇵 日本下载专用'
   proxies:
     - '🇯🇵 日本Y05 | 下载专用 | x0.01'
     - '🇯🇵 日本Y06 | 下载专用 | x0.01'

yi-yuan-group:
  - type: 'select'
    name: ' 🇯🇵 日本'
    proxies:
      - '🇯🇵日本 01 | 专线'
      - '🇯🇵日本 02 | 专线'
      - '🇯🇵日本 03 | 专线'
      - '🇯🇵日本 04 | 专线'

rule-providers:
  reject:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/reject.txt"
    path: ./ruleset/reject.yaml
    interval: 86400

  icloud:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/icloud.txt"
    path: ./ruleset/icloud.yaml
    interval: 86400

  apple:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/apple.txt"
    path: ./ruleset/apple.yaml
    interval: 86400

  google:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/google.txt"
    path: ./ruleset/google.yaml
    interval: 86400

  proxy:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/proxy.txt"
    path: ./ruleset/proxy.yaml
    interval: 86400

  direct:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/direct.txt"
    path: ./ruleset/direct.yaml
    interval: 86400

  private:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/private.txt"
    path: ./ruleset/private.yaml
    interval: 86400

  gfw:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/gfw.txt"
    path: ./ruleset/gfw.yaml
    interval: 86400

  tld-not-cn:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/tld-not-cn.txt"
    path: ./ruleset/tld-not-cn.yaml
    interval: 86400

  telegramcidr:
    type: http
    behavior: ipcidr
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/telegramcidr.txt"
    path: ./ruleset/telegramcidr.yaml
    interval: 86400

  cncidr:
    type: http
    behavior: ipcidr
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/cncidr.txt"
    path: ./ruleset/cncidr.yaml
    interval: 86400

  lancidr:
    type: http
    behavior: ipcidr
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/lancidr.txt"
    path: ./ruleset/lancidr.yaml
    interval: 86400

  applications:
    type: http
    behavior: classical
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/applications.txt"
    path: ./ruleset/applications.yaml
    interval: 86400

profile:
  store-selected: true

dns:
  use-system-hosts: false

```

# 全局扩展脚本

```javascript
//匹配自定义的代理 规则名称 配置
var matchProxyMapName = function(profileName) {
	var proxyMapName;
	switch(profileName) {
	case "iKuuu_V2.yaml": proxyMapName = "iKuuu-map";          break;
	default:              proxyMapName = profileName + "-map";
	}
	return proxyMapName;
};

//匹配当前订阅的代理集名称
var replaceProxyRulesName = function(config, profileName) {
	var proxyMapName = matchProxyMapName(profileName)
	var proxyMapConfig = config[proxyMapName.toLowerCase()]
	
	var rulesConfig = config["my-rules"];
	var newRules = rulesConfig.map((item) => {
		var newArray = item.split(',');
		var proxyRulesName = "DIRECT";
		var mapName = newArray[2];
		if (proxyMapConfig != null){
			proxyRulesName = proxyMapConfig[mapName]==null?"DIRECT":proxyMapConfig[mapName]
		}
		newArray[2] = proxyRulesName
		var newItem = newArray.join(',');
		return newItem;
	});
	
	let oldRules = config.rules;
	config.rules = newRules.concat(oldRules);
	
	//console.info(profileName);
};

//匹配自定义的代理 规则集 配置
var matchProxyGroupName = function(profileName) {
	var proxyGroupName;
	switch(profileName) {
	case "iKuuu_V2.yaml": proxyGroupName = "iKuuu-group";          break;
	default:              proxyGroupName = profileName + "-group";
	}
	return proxyGroupName;
};

//添加代理集
var addProxyGroup = function(config, profileName) {
	var proxyGroupName = matchProxyGroupName(profileName);
	var newProxyGroup = config[proxyGroupName.toLowerCase()];

	var oldProxyGroup = config["proxy-groups"];
	if (newProxyGroup != null) {
		config["proxy-groups"] = newProxyGroup.concat(oldProxyGroup);
	}
};

var ccccccccccccc = function(config, profileName) {
	var proxyGroupName = matchProxyGroupName(profileName);
	var newProxyGroup = config[proxyGroupName.toLowerCase()];
	console.info(proxyGroupName);
	console.info(newProxyGroup==null?"NO":"YES");
}

function main(config, profileName) {
	ccccccccccccc(config, profileName);
	//addProxyGroup(config, profileName);
	//replaceProxyRulesName(config, profileName);
	return config;
}
```

