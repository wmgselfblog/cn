## **同账号同地域专线连接**

``使用专线连接前，应规划好IDC内和VPC内的网段，保证IDC内的网段和VPC内的网段不会重叠！``



### **如果使用物理链路打通客户IDC和京东云上的VPC，那么您需要完成以下步骤：**

第一步：创建物理连接

第二步：创建边界网关

第三步：创建专线通道

第四步：配置VPC内的路由表

第五步：配置边界网关上的路由表

第六步：配置客户IDC内的路由



### **详细步骤如下：**

#### **第一步：创建物理连接**

1.登录京东云控制台。

2.点击左侧导航栏，选择“专线服务 -> 专线连接 -> 物理连接”。

3.创建物理连接，您可以直接联系京东云的专线连接合作伙伴，合作伙伴会为您提供一站式服务，具体的合作伙伴详见京东云市场。您也可以选择自助申请，本文档即为自助申请。

4.配置物理连接，详见控制台页面。

主要配置项如下：

- - 端口类型，支持以下几种线路端口接入：千兆电口、千兆单模光口(10KM)、万兆电口、万兆单模光口(10KM)； 

5.单击“确认”，在物理连接列表页中，该连接的状态为申请中。

京东云审核人员会对您的申请进行审核，一般情况下，两个工作日内就会完成审核。物理连接审核通过时连接状态变为待支付，此时您需要对此物理连接进行支付，相关费用详见购买须知。

6.请根据与京东云签订的专线服务合同中指定的结算方式进行支付。

7.物理连接支付成功后，连接状态变为施工中，此时会自动分配接入设备的端口号，用于物理链路的接入。

8.将端口信息同步给您选择的运营商，请运营商核查资源并进行线路铺设，京东云机房运维人员会配合完成线路入室。如需运营商人员亲自完成线路入室操作，请提前提供相关人员的信息，京东云提前为您的运营商完成入室预约，并把当天机房接待人员的联系方式给您。

9.最终确认物理连接创建完成。



#### **第二步：创建边界网关**

1.登录京东云控制台。

2.点击左侧导航栏，选择“专线服务 -> 边界网关”。

3.创建边界网关，边界网关会自动与同地域下该账号的VPC进行关联。



**第三步：创建专线通道**

1.登录京东云控制台。

2.点击左侧导航栏，选择“专线服务 -> 专线连接 -> 专线通道”。

3.配置专线通道，详见控制台页面。

主要配置项如下：

- - 物理连接：用于VPC和IDC通信的物理链路；
  - 边界网关：京东云侧和客户IDC侧运行BGP的终结点，对内与VPC进行通信；
  - vlanId：用户划分业务通道的标识，同一物理链路中通过vlan进行不同业务的隔离，每个通道拥有该物理链路上的唯一vlanId；
  - BGP ASN、密钥：客户IDC路由器和京东云路由器间运行BGP协议所需的信息；
  - 路由互联地址：客户IDC路由器和京东云路由器间运行BGP协议所需的BGP Peer信息；

4.单击“确认”，在专线通道列表页中，该通道的状态为配置中。

5.专线通道完成配置后，通道状态变为可用，此时即可使用该专线通道。



#### **第四步：配置VPC内的路由表**

1.登录京东云控制台。

2.点击左侧导航栏，选择“私有网络”，进入需要与IDC内网络进行通信的京东云VPC内子网所关联的路由表。

3.配置路由表，目的端为您的IDC内的网段，下一跳类型选择边界网关，下一跳选择用于承载专线连接网络互通的边界网关。



#### **第五步：配置边界网关上的路由表**

1.登录京东云控制台。

2.点击左侧导航栏，选择“专线服务 -> 边界网关”，进入用于承载专线连接网络互通的边界网关的详情页面。

3.配置路由表，需要配置双向的路由，即通往VPC侧的路由、通往您的IDC侧的路由。

通往VPC侧的路由，目的端为您的VPC内的网段，下一跳类型选择VPC，下一跳选择具体要进行通信的VPC。

通往IDC侧的路由，目的端为您的IDC内的网段，下一跳类型选择专线通道，下一跳选择用于承载专线连接网络互通的专线通道。



#### **第六步：配置客户IDC内的路由**

配置客户IDC内的路由，包括与京东云运行BGP协议的相关配置，及具体的路由配置。

通往VPC侧的路由，目的端为您的VPC内的网段，下一跳地址为BGP Peer中京东公有云侧的地址，即专线通道/30地址中的京东云侧地址。