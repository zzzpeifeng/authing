# What is Refresh Token

<LastUpdated/>

Access Token and ID Token are [JSON Web Token](https://tools.ietf.org/html/rfc7519), they have a Short **Lifetime**. Access Token are required when user requesting resources. After Access Token expired, users need to obtain a new Access Token.


**Refresh Token** are used to obtain new Access Token. It can shorten the lifetime of Access Token to improve security and user don't need to login frequently.

During users first authentication, Authing return Refresh Token along with Access Token and ID Token. Due to the Refresh Token keeps user login, **it is as important as user password**. Your Application must securely stored Refresh Token.

Refresh Token Example:

```json
{
  "access_token": "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6InIxTGtiQm8zOTI1UmIyWkZGckt5VTNNVmV4OVQyODE3S3gwdmJpNmlfS2MifQ.eyJqdGkiOiJ4R01uczd5cmNFckxiakNRVW9US1MiLCJzdWIiOiI1YzlmNzVjN2NjZjg3YjA1YTkyMWU5YjAiLCJpc3MiOiJodHRwczovL2F1dGhpbmcuY24iLCJpYXQiOjE1NTQ1Mzc4NjksImV4cCI6MTU1NDU0MTQ2OSwic2NvcGUiOiJvcGVuaWQgcHJvZmlsZSBvZmZsaW5lX2FjY2VzcyBwaG9uZSBlbWFpbCIsImF1ZCI6IjVjYTc2NWUzOTMxOTRkNTg5MWRiMTkyNyJ9.wX05OAgYuXeYM7zCxhrkvTO_taqxrCTG_L2ImDmQjMml6E3GXjYA9EFK0NfWquUI2mdSMAqohX-ndffN0fa5cChdcMJEm3XS9tt6-_zzhoOojK-q9MHF7huZg4O1587xhSofxs-KS7BeYxEHKn_10tAkjEIo9QtYUE7zD7JXwGUsvfMMjOqEVW6KuY3ZOmIq_ncKlB4jvbdrduxy1pbky_kvzHWlE9El_N5qveQXyuvNZVMSIEpw8_y5iSxPxKfrVwGY7hBaF40Oph-d2PO7AzKvxEVMamzLvMGBMaRAP_WttBPAUSqTU5uMXwMafryhGdIcQVsDPcGNgMX6E1jzLA",
  "expires_in": 3600,
  "id_token": "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6InIxTGtiQm8zOTI1UmIyWkZGckt5VTNNVmV4OVQyODE3S3gwdmJpNmlfS2MifQ.eyJzdWIiOiI1YzlmNzVjN2NjZjg3YjA1YTkyMWU5YjAiLCJub25jZSI6IjIyMTIxIiwiYXRfaGFzaCI6Ik5kbW9iZVBZOEFFaWQ2T216MzIyOXciLCJzaWQiOiI1ODM2NzllNC1lYWM5LTRjNDEtOGQxMS1jZWFkMmE5OWQzZWIiLCJhdWQiOiI1Y2E3NjVlMzkzMTk0ZDU4OTFkYjE5MjciLCJleHAiOjE1NTQ1NDE0NjksImlhdCI6MTU1NDUzNzg2OSwiaXNzIjoiaHR0cHM6Ly9hdXRoaW5nLmNuIn0.IQi5FRHO756e_eAmdAs3OnFMU7QuP-XtrbwCZC1gJntevYJTltEg1CLkG7eVhdi_g5MJV1c0pNZ_xHmwS0R-E4lAXcc1QveYKptnMroKpBWs5mXwoOiqbrjKEmLMaPgRzCOdLiSdoZuQNw_z-gVhFiMNxI055TyFJdXTNtExt1O3KmwqanPNUi6XyW43bUl29v_kAvKgiOB28f3I0fB4EsiZjxp1uxHQBaDeBMSPaRVWQJcIjAJ9JLgkaDt1j7HZ2a1daWZ4HPzifDuDfi6_Ob1ZL40tWEC7xdxHlCEWJ4pUIsDjvScdQsez9aV_xMwumw3X4tgUIxFOCNVEvr73Fg",
  "refresh_token": "WPsGJbvpBjqXz6IJIr1UHKyrdVF",
  "scope": "openid profile offline_access phone email",
  "token_type": "Bearer"
}
```

When application request contain a Refresh Token. Authing will return the **SAME** Refresh Token and **NEW** Access Token along with **NEW** ID Token until the Refresh Token expired.

