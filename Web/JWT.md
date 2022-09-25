# JWT

> Json Web Token의 줄임말

### JWT란?

JWT는 JSON객체로서 당사자 간의 정보를 안전하게 전송하기위한 방법을 정의하고있는 웹표준(RFC 7519)입니다.

### 구조

#### `Header`.`Payload`.`Verify Signature`

구조는 이렇게 3가지로 나누어져있다.


### 1. Header

```Json
{
  "alg": "HS256",
  "typ": "JWT"
}
```
 
 * alg: 서명 암호화 알고리즘
 * typ: 토큰 유형

Header는 일반적으로 JWT 토큰 유형과 사용중인 서명 알고리즘으로 구성되어있습니다.


### 2. Payload

```Json
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}

```

Payload는 토큰에서 사용할 정보의 조각인 Claim이 담겨있습니다.\
Claim은 key-value의 형식으로 이루어진 한 쌍의 정보입니다.

#### - Payload Type
 * Registered Claims : 미리 정의된 Claim
    
    * iss(issuer) 발행자
    * exp(expireation time): 만료 시간
    * sub(subject): 제목
    * iat(issued At): 발행 시간
    * jti(JWI ID)

 * Public Claims : 사용자가 정의할 수 있는 클레임 공개용 정보 전달을 위해 사용합니다.
 * Private Claims : 당사자들 간에 정보를 공유하기 위해 만들어진 사용자 지정 클래임, 외부에 공개되도 상관없지만 해당 유저를 특정할 수 있는 정보를 담고있습니다.

### 3. Signature

```Json
HMACSHA256(
  base64UrlEncode(Header) + "." +
  base64UrlEncode(Payload),
  your-256-bit-secret
)
```

시그니처는 (헤더 + 페이로드)와 서버에서 가지고 있는 key 값을 합친 것을 헤더에서 정의한 알고리즘으로 암호화 한 값을 가지고 있다.

#### 참고한 자료
[JWT Introjuction](https://jwt.io/introduction)
[[WEB] 📚 JWT 토큰 인증 이란? - 💯 이해하기 쉽게 정리](https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-JWTjson-web-token-%EB%9E%80-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC)
