# Woods API V2

- Base URL: <https://api.infowoods.com/v2>
- [Postman workspace](https://www.postman.com/infowoods/workspace/infowoods-public-workspace)
- Mixin 机器人 ID：**7000104503**

以下仅列出功能和其对应的接口。接口用法详情参考 Postman workspace。

## 授权

> 仅支持 Mixin Messenger User/Group 登录。

- 登录获得 user access token `POST /oauth/mixin`
    > user access token, 拥有完整的权限，7天有效期。

- 注销 token `POST /oauth/revoke`

## 橡树主题中心

- 列出拥有的主题 `GET /oth/topics`
- 读取主题详情 `GET /oth/topics/:id`
- 修改主题属性 `PUT /oth/topics/:id`
- 向主题发布信息 `POST /oth/topics/:id`
- 获取/重置主题Token `GET /oth/topics/:id/token`
    > topic token, 权限仅包括：读主题详情、向主题发布信息。无失效期可永久使用，直到被重置。
    > 此 token 是方便开发主题机器人。

### 如何创建主题

- Mixin机器人消息交互，发送“create”，根据提示付款以创建主题。

- 通过 API
    1. 创建订单获得付款信息 `POST /oth/orders/create`
    2. 根据付款信息，发起 Mixin Payment 窗口，等待用户付款。
    > 付款成功后，支付结果会自动上报。并创建主题。
    > （暂无查询订单状态的接口，计划中）
