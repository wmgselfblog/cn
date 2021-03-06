# API的访问授权

API的访问授权过程，即API提供者给API调用者授权访问API分组的过程。授权过程分为两部分：

- API调用者创建和提供 **访问密钥** 。访问密钥（APIKey/APISecret）代表请求者的身份。

- API提供者授权API分组给API调用者使用。

当API提供者的客户或者自己需要测试调用 API 时，都需要创建 访问密钥 作为请求者的身份，然后由API提供者在访问授权中，授权API分组给 API调用者使用。

下面将分两部分进行说明：


## 操作步骤
### API调用者创建和提供 **访问密钥** 
#### STEP1: 点击左侧菜单 **访问密钥**  进入访问密钥列表页

![访问密钥列表页](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/API-Gateway/fwmy-list.png)

#### STEP2: 点击 **创建访问密钥**

![创建访问密钥](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/API-Gateway/fwmy-add.png)

- 密钥创建成功后，系统会自动生成访问密钥ID、APIKey、APISecret。
- API调用者需要将 **APIKey** 告知API提供者，由API提供者进行访问授权。


### API提供者授权API分组给API调用者使用

#### STEP1: API提供者获取API调用者的访问密钥ID 或者 京东云账户的Access Key。

API调用者可在访问密钥详情页找到访问密钥ID，并将该ID告诉API提供者。


![访问密钥详情页](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/API-Gateway/fwmy-xqy.png)
 
 
 API调用者还可用京东云的AK（Access Key）方式，请求授权调用。具体可在Access Key管理页中新定义或者选择一个AK，并将该AK告诉API提供者。

![AK List](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/API-Gateway/AK-list.png)
 

 
#### STEP2: API提供者创建1个授权。

首先进入左侧菜单的 **访问授权** 列表页

![访问授权页](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/API-Gateway/fwsq-list.png)

然后点击 **创建授权**，在授权信息中，填入API调用者提供的访问密钥或者AK。

![创建授权](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/API-Gateway/fwsq-add.png)


#### STEP3: API提供者绑定授权和API分组

密钥创建成功后，点击 **绑定**进行授权分组的绑定关系。

![授权绑定](https://github.com/jdcloudcom/cn/blob/edit/image/Internet-Middleware/API-Gateway/fwsq-bd.png)



  
