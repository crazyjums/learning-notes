### Cas单点登录

### 一、cas中的概念

#### 1.1 TGC：Ticket Granting Cookie

Cas 将会生成的 TGT 放在 session 中，而 TGC 就是这个 session 的唯一标识（sessionId），可以认为是 TGT 的key，为TGT就是TGC的value，TGC 以 cookie 的形式保存在浏览器中每个请求都会尝试携带 TGC 。（每个服务都会在session和cookei中保存对应的TGT 和 TGC）

#### 1.2 TGT：Ticket Granting Ticket

TGT 是CAS 为用户签发的登录 ticket，也是用于验证用户登录成功的唯一方式。 TGT 封装了 Cookie 值以及 Cookie 值对应的用户信息，CAS 通过 Cookie 值（TGC）为 key 查询缓存中有无 TGT（TGC:TGT（key:value）），如果有的话就说明用户已经登录成。

#### 1.3 ST：Service Ticket

ST 是当用户访问某一服务时提供的 ticket。用户在访问其他服务时，发现没有 cookie 或 ST ，那么就会302到 CAS 服务器获取 ST。然后会携带着 ST 302 回来。