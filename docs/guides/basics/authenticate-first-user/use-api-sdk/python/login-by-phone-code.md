使用 `login_by_phone_code` 方法进行手机号验证码登录：

```python
phone = '188xxxx8888'
# 手机号验证码登录，如果用户不存在会自动创建账号
user = authentication_client.login_by_phone_code(
    phone=phone,
    code='1234',
)
```