<div align="center">
  
  ![header](https://capsule-render.vercel.app/api?type=waving&color=0:EEFF00,100:a82da8&height=200&section=header&text=Backend%20Developer&fontSize=50&fontColor=ffffff)

</div>

<h3 align="center">💡 문제를 발견하고, 본질을 파악하고, 구조적으로 해결하는 개발자</h3>

<p align="center">
  <a href="mailto:kimsh142536@gmail.com"><img src="https://img.shields.io/badge/Gmail-d14836?style=flat-square&logo=Gmail&logoColor=white"/></a>
  <a href="https://github.com/kimsh300"><img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white"/></a>
  <img src="https://komarev.com/ghpvc/?username=kimsh300&color=blueviolet&style=flat-square"/>
</p>

<br>

## 👨‍💻 About Me
신한DS 금융 SW 아카데미에서 풀스택 개발을 학습하고, **플러거에서 실무 경험**을 쌓았습니다.  
<br>

## 🎖️ Highlights

### 📈 **성과로 증명하는 개발 능력**

| 문제 | 해결 | 성과 |
|:-----|:-----|:-----|
| 알림 삭제 시 N번 API 호출로 서버 과부하 | UI 선처리 + 일괄 삭제 방식으로 재설계 | **API 호출 감소** |
| 장바구니 종속 배송비 계산의 확장성 문제 | 전역 상태 관리로 분리 설계 | **멀티 선택, 쿠폰 정책 확장 가능** |

### 🚀 **빠른 학습 능력**
- Vue.js를 **3개월 만에 실무 투입** 수준으로 습득
- 프론트엔드 경험 없이 풀스택 개발자로 성장

<br>

## 🛠️ Tech Stack

### **Backend**
![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![Spring](https://img.shields.io/badge/Spring-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![MyBatis](https://img.shields.io/badge/MyBatis-000000?style=for-the-badge&logo=mybatis&logoColor=white)
![JSP](https://img.shields.io/badge/JSP-007396?style=for-the-badge&logo=java&logoColor=white)

### **Frontend**
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Vue.js](https://img.shields.io/badge/Vue.js-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white)
![Nuxt](https://img.shields.io/badge/Nuxt-00DC82?style=for-the-badge&logo=nuxtdotjs&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)

### **Database**
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Oracle](https://img.shields.io/badge/Oracle-F80000?style=for-the-badge&logo=oracle&logoColor=white)

### **Security**
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white)
![OAuth](https://img.shields.io/badge/OAuth_2.0-EB5424?style=for-the-badge&logo=auth0&logoColor=white)

### **Tools & Collaboration**
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black)
![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![Notion](https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white)

<br>

## 💼 Experience

<details open>
<summary><b>주식회사 플러거 (Plugger)</b> | 솔루션 개발팀 사원 | <code>2025.04 ~ 2025.06</code></summary>

<br>

**프로젝트**: 마켓빌리(MarketBilly) 중고거래 플랫폼  
**역할**: 풀스택 개발자 (백엔드 주, 프론트엔드 보조)  
**기술**: `Spring Boot` `Vue.js` `Nuxt` `MySQL` 

### 📊 **주요 성과**

#### 1️⃣ **알림 시스템 최적화 (API 호출 90% 감소)**
**문제 상황**
- 사용자가 알림 삭제 버튼 클릭 시마다 개별 API 호출
- 10개 삭제 시 10번 API 호출 → 서버 부하 및 UX 저하

**해결 과정**
```javascript
// Before: 클릭할 때마다 즉시 API 호출
async deleteNotification(notiId) {
    await api.delete(`/notifications/${notiId}`);  // 클릭마다 호출
}

// After: UI에서 먼저 숨김 처리, 모달 닫힐 때 일괄 삭제
data() {
    return {
        deletedIds: []
    }
},

methods: {
    deleteNotification(notiId) {
        this.deletedIds.push(notiId);  // 삭제 목록에 추가
        // UI에서 즉시 숨김 처리
    },
    
    // 모달 닫힐 때 (X 버튼, 외부 클릭 등)
    async onModalClose() {
        if (this.deletedIds.length > 0) {
            await api.delete('/notifications/batch', { 
                ids: this.deletedIds 
            });
            this.deletedIds = [];
        }
    }
}
```

**결과**
- ✅ API 호출 **90% 감소** (N번 → 1번)
- ✅ UI 즉시 반영으로 사용자 경험 개선
- ✅ 서버 부하 해소

---
<br>

## 🚀 Projects

### **새롬터 - 친환경 리사이클링 쇼핑몰** [![GitHub](https://img.shields.io/badge/Repo-181717?style=flat&logo=github)](https://github.com/Saerom-teo/server)

`2024.05 ~ 2024.07` | 6주 팀 프로젝트 (6인) | [🎥 시연 영상](https://www.youtube.com/watch?v=2aBmCkz1ZEE)

**담당 역할**: 인증/인가 시스템 개발 리드, 프로젝트 환경 구축

<details>
<summary><b>🔐 주요 구현 사항</b></summary>

<br>

#### **1. JWT 기반 인증 시스템**
- Access Token 발급 (만료: 24시간)
- HttpOnly 쿠키 방식으로 XSS 공격 방어
- Admin/User 권한 분리

**핵심 코드:**
```java
// JWTUtil.java - JWT 생성
public String generateToken(PrincipalDetail userDetails, String role) {
    return Jwts.builder()
        .claim("id", userDetails.getUser().getUserId())
        .claim("userEmail", userDetails.getUser().getUserEmail())
        .claim("role", role)
        .setIssuedAt(new Date())
        .setExpiration(new Date(System.currentTimeMillis() + 86400000))
        .signWith(Keys.hmacShaKeyFor(secretKey.getBytes()), SignatureAlgorithm.HS256)
        .compact();
}
```

---

#### **2. OAuth2 소셜 로그인**
- Google OAuth2 연동
- Kakao OAuth2 연동
- Spring Security OAuth2 Client 활용

**핵심 코드:**
```java
// SecurityConfig.java - OAuth2 설정
@Bean
public ClientRegistrationRepository clientRegistrationRepository() {
    return new InMemoryClientRegistrationRepository(
        createClientRegistration("google", googleClientId, googleClientSecret, ...),
        createClientRegistration("kakao", kakaoClientId, kakaoClientSecret, ...)
    );
}
```

---

#### **3. 회원가입 시스템**
- 이메일 인증 코드 발송
- BCrypt 비밀번호 암호화
- 신규 가입 웰컴 포인트 100점 자동 지급

**회원가입 플로우:**
```
약관 동의 → 이메일 입력 → 인증 코드 확인 → 비밀번호 설정 → 가입 완료 + 포인트 지급
```

---

#### **4. 비밀번호 재설정**
- 이메일 인증 기반
- 세션을 통한 임시 상태 관리
- 보안 강화를 위한 2단계 인증

</details>

**협업 프로세스**
- GitHub Issues 기반 작업 분배 및 일정 관리
- Pull Request 코드 리뷰
- 코드 컨벤션 준수 및 문서화

**기술 스택**  
`Spring Framework` `Java` `MySQL` `JWT` `Spring Security` `OAuth 2.0` `BCrypt` `JavaMail` `JSP`

**주요 성과**  
✅ Google + Kakao 2개 소셜 로그인 연동  
✅ JWT + OAuth2 하이브리드 인증 구현  
✅ Admin/User 권한 분리  
✅ 이메일 인증 시스템 구축  
✅ 855 커밋, 6명 협업 완수  

<br>

## 📘 Study & Learning

> 꾸준히 학습하고 기록하는 개발자입니다.

| Repository | 내용 | 링크 |
|:-----------|:-----|:-----|
| **CS** | 운영체제, 네트워크, 데이터베이스, OOP 등 CS 기초 | [![GitHub](https://img.shields.io/badge/Repo-181717?style=flat&logo=github)](https://github.com/kimsh300/CS) |
| **Algorithm** | 백준 중심 알고리즘 문제 풀이 | [![GitHub](https://img.shields.io/badge/Repo-181717?style=flat&logo=github)](https://github.com/kimsh300/Algorithm) |

<br>

<br>
</div>
