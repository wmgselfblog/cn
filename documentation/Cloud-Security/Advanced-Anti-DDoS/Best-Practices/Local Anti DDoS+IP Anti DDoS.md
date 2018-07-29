# 方案说明

为解决用户本地节点安全防护问题，帮助用户建立本地基础防护系统，同时由于本地节点带宽资源有限，无法应对海量DDoS攻击，为用户提供云端联动防护功能。本地防护系统通过实时流量监测，当攻击流量达到本地防护阈值，自动将流量牵引至IP高防，帮助用户实现应急上云。

# 部署架构
![部署架构](https://github.com/jdcloudcom/cn/blob/edit/image/Advanced%20Anti-DDoS/Best-Practice01.png)<Br/>
同时满足用户本地业务防护和一键上云联动防护的最佳实践：
- 京东云的安全调度中心，通过DNS解析，对全局的流量进行统一调度。
- 当攻击流量在本地防护阈值内，流量在用户源站入口处清洗。
- 当攻击流量超过本地防护阈值，流量牵引至IP高防，清洗后返回用户源站。
- 本地安全组件集成控制台，即能管理配置本地防护资源，又能关联云端高防账号，查看云端联动信息。
- 本地安全组件支持串联或旁路部署方式。

注意：如果关联的高防实例到期或者删除，联动策略将无法生效。高防实例如果欠费，则弹性防护将不会生效。请及时续费或充值，已保证业务正常进行。

# 方案优势
1. 本地组件提供攻击检测和防护能力，当攻击流量超过阈值时迁移至云端IP高防，这种协同防御模式能够满足政府、金融行业的数据自主可控的合规监管要求。
2. CNAME接入，一键自动上云，配置简单，减少运维人员工作。
