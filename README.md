# 全局配置扩展

```yaml
ikuuu-map:
  proxy: 🔰 选择节点
  chinese:  🇨🇳 国内网站
  reject: 🛑 拦截广告

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

append-rules:

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
//替换的代理集名称
let replaceProxyGroupName = function(map, meRulesConfig) {
  return meRulesConfig.map((item) => {
    let newArray = item.split(',');
    let proxyGroupName = "DIRECT"
    if (map !== null){
      proxyGroupName = map[newArray[2]]==null?"DIRECT":map[newArray[2]]
    }
    newArray[2] = proxyGroupName
    let newItem = newArray.join(',');
    return newItem;
  });
};

//匹配当前订阅的代理集名称
let choose = function(config, profileName) {
  let mapName = ""
  if (profileName == "iKuuu_V2.yaml") {
      mapName = "iKuuu-map";
  } else {
    mapName = profileName+"-map";
  }
  let map = config[mapName.toLowerCase()]
  let myRulesConfig = config["my-rules"];
  //myRulesConfig = replaceProxyGroupName(map, myRulesConfig)

  //前置新的规则
  //let oldRules = config.rules;
  //config.rules = myRulesConfig.concat(oldRules);

  //console.info(profileName);
  //console.info(mapName);
  //console.info(map)
  //console.info(oldRules);
  //console.info("my-rules:" + myRulesConfig);
};

function main(config, profileName) {
  choose(config, profileName);
  return config;
}
```

