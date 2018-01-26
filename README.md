# WechatBundle
This Symfony bundle provides integration support with the latest EasyWeChat library.

这个 Symfony bunble 模块用于把 EasyWeChat 库集成进你的项目。

> #### Why use this bundle / 使用这个 bundle 的好处
> You don't need to construct the EasyWeChat API objects explicitly in your code, just inject the service object where you need it and call it.
> 
> 你不需要写代码 “new” 那些 EasyWeChat 提供的类，而是直接在需要的地方注入，然后直接使用就行了。

### Usage / 用法
Once the bundle been successfully loaded into your Symfony application, the following service instances would be ready to use:

在 Bundle 成功加载到你的 Symfony 应用程序之后，以下的5个服务对象就可以使用了：

  - orinoco_wechat.application.official_account
  - orinoco_wechat.application.payment
  - orinoco_wechat.application.mini_program
  - orinoco_wechat.application.open_platform
  - orinoco_wechat.application.work

For example:

例如：
```php
// in controller class
// 在 controller 类中使用
$this->get('orinoco_wechat.application.payment')
```
```xml
<!-- inject it into other services -->
<!-- 注入到需要使用的服务类中 -->
<service id="..." class="..." public="true">
    <argument>...</argument>
    <argument type="service" id="orinoco_wechat.application.payment" />
    <tag name="..." />
</service>
```
### Config / 配置
```yml
# app/config/config.yml
orinoco_wechat:
    sandbox: true

    log:
        enabled: true
        level: debug
        file: /Users/hailong/dev/zshwag/app/../var/logs/wechat.log

    applications:
        official_account:
            app_id: "%wechat_app_id%"
            secret: "%wechat_secret%"
            response_type: array

        payment:
            app_id: "%wechat_app_id%"
            mch_id: "%wechat_mch_id%"
            key: "%wechat_key%"
            cert_path: "%wechat_cert_path%"
            key_path: "%wechat_key_path%"
            notify_url: "%wechat_notify_url%"

        mini_program:

        open_platform:
            app_id: "%wechat_app_id%"
            secret: "%wechat_secret%"
            token: "%wechat_token%"
            aes_key: "%wechat_aes_key%"

        work:
            corp_id: "%wechat_corp_id%"
            agent_id: "%wechat_agent_id%"
            secret: "%wechat_secret%"
            response_type: array
```
### Reference / 参考
Please refer to the EasyWeChat documentation for more details.

具体的用法请参考 EasyWeChat 的文档
[https://www.easywechat.com/docs/master](https://www.easywechat.com/docs/master)
