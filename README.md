# jwt

jet 설치

```solidity
$ npm install jsonwebtoken
```

가져오기

```solidity
const jwt = require('jsonwebtoken');
```

### 토큰

![images_neity16_post_cfdcc3e9-29ba-4e90-9916-2e9949cbba9e_스크린샷 2020-12-11 오전 12 11 45](https://github.com/likeprograming1/login_jwtStudy/assets/89185550/c4cf13f7-b348-4aca-aad7-4e3e332ac6a7)


- **HEADER(헤더)**
  - **typ : 토큰의 타입을 지정(JWT)**
  - **alg : 해싱 알고리즘을 지정(보통 HMAC SHA256 / RSA 사용)**
- **PAYLOAD(내용)** - **사용되는 정보의 한 조각을 클레임(claim)**이라고 함
- **VERIFY SIGNATURE(서명)**: **header + payload 정보를 비밀키로 해쉬를 하여 생성!** (즉, **payload가 바뀌어도 이 값에 영향을 주기 때문에 보안성이 높아짐!**)

### 토큰생성

공식 : jwt.sign(payload, secretKey, option)

```jsx
const accessToken = jwt.sign({
        id : userInfo.id,
        username : userInfo.username,
        email: userInfo.email,
      }, process.env.ACCESS_SECRET, {
        expiresIn : '1m',
        issuer : "About Tech",
      });

payload = {
        id : userInfo.id,
        username : userInfo.username,
        email: userInfo.email,
      }

secretKey = process.env.ACCESS_SECRET //env파일에 있는 ACCESS_SECRET의 값

option = {
        expiresIn : '1m',
        issuer : "About Tech",
      }

/* 모든 등록된 클레임은 선택적으로 사용! 필수가 아님! */
iss : 토큰 발급자 (issuer)
sub : 토큰 제목 (subject)
aud : 토큰 대상자 (audience)
exp : 토큰의 만료시간 (expiration) / 형식은 NumericDate
nbf : Not Before 을 의미 / 토큰의 활성 날짜
```

- **jwt에서 사용 할 함수**는 **jwt.sign --> 토큰 발급, jwt.verify --> 토큰 인증(확인)**
