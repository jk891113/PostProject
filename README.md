# 내일배움캠프 4기 A반 8조 팀프로젝트

## 게시판 백엔드 서버 만들기
___
[![My Skills](https://skillicons.dev/icons?i=java,spring,idea,git,github)](https://skillicons.dev)

### Notion TeamSpace :https://mountainous-march-11f.notion.site/f0acd39deaa94413a8d2e5ecb4372393?v=3f5e74eca5ab4ca6aeba65de146c2e7f
___
개발환경
Java17
Springboot 2.7.6
JDK17
___

### A반 8조 (한눈8지말조)
#### 팀장 : 
- 이영빈
#### 팀원 : 
- 조운
- 진용재
- 한정규

### 요구사항
### 0. `Spring Security` 적용하기
### 1. 회원 가입 API
- username, password 를 Client 에서 전달받기
- username 은 `최소 4자 이상, 10자 이하이며 알파벳 소문자, 숫자`로 구성
- password 는 `최소 8자 이상, 15자 이하이며 알파벳 대소문자, 숫자`, `특수문자`로 구성
- DB에 중복된 username 이 없다면 회원을 저장하고 Client 로 성공 메시지, 상태코드 반환
- 회원 권한 부여하기 (ADMIN, USER) - ADMIN 회원은 모든 게시글, 댓글 수정/삭제 가능
### 2. 로그인 API
- username, password 를 Client 에서 전달받기
- DB 에서 username 을 사용하여 저장된 회원의 유무를 확인하고 있다면 password 비교하기
- 로그인 성공시, 로그인에 성공한 유저의 정보와 JWT 를 활용하여 토큰을 발급하고,<br>
  발급한 토큰을 Header 에 추가하고 성공 메시지, 상태코드 반환
### 3. 전체 게시글 목록 조회 API
- 제목, 작성자명(username), 작성내용, 작성날짜를 조회하기
- 작성날짜 기준 내림차순으로 정렬하기
- 각각의 게시글에 등록된 모든 댓글을 게시글과 같이 Client에 반환
- 댓글은 작성 날짜 기준 내림차순으로 정렬
- `게시글 / 댓글에 '좋아요' 갯수도 함께 반환`
### 4. 게시글 작성 API
- ~~토큰을 검사하여, 유효한 토큰일 경우에만 게시글 작성 가능~~<br>
  -> `Spring Security를 사용하여 토큰 검사 및 인증`
- 제목, 작성자명(username), 작성 내용을 저장하고
- 저장된 게시글을 Client로 반환
### 5. 선택한 게시글 조회 API
- 선택한 게시글의 제목, 작성자명(username), 작성날짜, 작성내용을 조회하기<br>
  (검색 기능 아님. 간단한 게시글 조회만 구현)
- 선택한 게시글에 등록된 모든 댓글을 선택한 게시글과 같이 Client에 반환
- 댓글은 작성 날짜 기준 내림차순으로 정렬
- `게시글 / 댓글에 '좋아요' 갯수도 함께 반환`
### 6. 선택한 게시글 수정 API
- ~~토큰을 검사한 후, 유효한 토큰이면서 해당 사용자가 작성한 게시글만 수정 가능~~<br>
  -> `Spring Security를 사용하여 토큰 검사 및 인증`
- 제목, 작성내용을 수정하고 수정된 게시글을 Client로 반환
- 게시글에 '좋아요' 갯수도 함께 반환
### 7. 선택한 게시글 삭제 API
- ~~토큰을 검사한 후, 유효한 토큰이면서 해당 사용자가 작성한 게시글만 삭제 가능~~<br>
  -> `Spring Security를 사용하여 토큰 검사 및 인증`
- 선택한 게시글을 삭제하고 Client로 성공 메시지, 상태코드 반환
### 8. 댓글 작성 API
- ~~토큰을 검사한 후, 유효한 토큰인 경우에만 댓글 작성 가능~~<br>
  -> `Spring Security를 사용하여 토큰 검사 및 인증`
- 선택한 게시글의 DB 저장 유무 확인
- 선택한 게시글이 있다면 댓글을 등록하고 등록된 댓글 반환
### 9. 댓글 수정 API
- ~~토큰을 검사한 후, 유효한 토큰이면서 해당 사용자가 작성한 댓글만 수정 가능~~<br>
  -> `Spring Security를 사용하여 토큰 검사 및 인증`
- 선택한 댓글의 DB 저장 유무 확인
- 선택한 댓글이 있다면 댓글 수정하고 수정된 댓글 반환
### 10. 댓글 삭제 API
- ~~토큰을 검사한 후, 유효한 토큰이면서 해당 사용자가 작성한 댓글만 삭제 가능~~<br>
  -> `Spring Security를 사용하여 토큰 검사 및 인증`
- 선택한 댓글의 DB 저장 유무 확인
- 선택한 댓글이 있다면 댓글 삭제하고 Client 로 성공했다는 메시지, 상태코드 반환
### 11. 게시글 좋아요 API
- 사용자는 선택한 게시글에 '좋아요'를 할 수 있다.
- 사용자가 이미 '좋아요'한 게시글에 다시 '좋아요' 요청을 하면 '좋아요'를 했던 기록이 취소된다.
- 요청이 성공하면 Client로 성공했다는 메시지, 상태코드 반환
### 12. 댓글 좋아요 API
- 사용자는 선택한 댓글에 '좋아요'를 할 수 있다.
- 사용자가 이미 '좋아요'한 댓글에 다시 '좋아요' 요청을 하면 '좋아요'룰 했던 기록이 취소된다.
- 요청이 성공하면 Client로 성공했다는 메시지, 상태코드 반환
### 13. 예외처리
- 아래의 예외처리를 AOP를 활용하여 구현
- 토큰이 필요한 API 요청에서 토큰을 전달하지 않았거나 정상 토큰이 아닌 경우<br>
  - "토큰이 유효하지 않습니다." 라는 에러메시지와 statusCode : 400을 Client에 반환
- 토큰이 있고, 유효한 토큰이지만 해당 사용자가 작성한 게시글/댓글이 아닌 경우 <br>
  - "작성자만 삭제/수정 할 수 있습니다." 라는 에러메시지와 statusCode : 400을 Client에 반환
- DB에 이미 존재하는 username으로 회원가입을 요청한 경우 <br>
  - "중복된 username 입니다." 라는 에러메시지와 statusCode : 400을 Client에 반환
- 로그인 시, 전달된 username과 password 중 맞지 않는 정보가 있는 경우 <br>
  - "회원을 찾을 수 없습니다."라는 에러메시지와 statusCode : 400을 Client에 반환
- `회원가입 시 username과 password의 구성이 알맞지 않은 경우` <br>
  - `에러메시지와 statusCode : 400을 Client에 반환`

___

### 추가기능
- 회원탈퇴(기능추가), 게시글 삭제, 댓글 삭제 시 연관된 데이터 모두 삭제될 수 있도록 구현
- 대댓글 기능 구현
  - 대댓글 작성하기
  - 댓글 조회시 대댓글도 함께 조회
- 게시글과 댓글 조회시 페이징, 정렬 기능 추가
- 게시글 카테고리 만들어 보기
  - 게시글을 분류하는 카테고리를 만들어서 게시글 작성시 카테고리 정보도 함께 저장
  - 카테고리 별로 게시글을 조회하는 기능 추가
- AccessToken, RefreshToken에 대해 구글링해 보고 RefreshToken을 적용해 보기
- 프로젝트에 Swagger를 구글링해 보고 적용해 보기

___

## ERD
https://www.erdcloud.com/d/4gkGtSs6r3yHCtHF7

___

## API 명세서
 http://localhost:8080/swagger-ui/index.html
### UserController
| 기능       | Method | URL           | request                                                                                    | response                                                    | request header | response header             |     |
|----------|--------|---------------|--------------------------------------------------------------------------------------------|-------------------------------------------------------------|----------------|-----------------------------|-----|
| 회원가입     | Post   | /users/signup | {<br/>"username":"username",<br/>"password":"password"<br/>}                               | {<br/>"statusCode":200,<br/>"statusMessage":회원가입 성공"<br/>}  |                |                             |     |
| 관리자 회원가입 | Post   | /admin/signup | {<br/>"username":"username",<br/>"password":"password"<br/>"adminToken":"adminToken"<br/>} | {<br/>"statusCode":200,<br/>"statusMessage":"회원가입 성공"<br/>} |                |                             |     |
| 로그인      | Post   | /users/login  | {<br/>"username":"username",<br/>"password":"password"<br/>}                               | {<br/>"statusCode":200,<br/>"statusMessage":"로그인 성공"         |                | Authorization: Bearer 무작위생성 |     |
|          |        |               |                                                                                            |                                                             |                |                             |     |
|          |        |               |                                                                                            |                                                             |                |                             |     |
|          |        |               |                                                                                            |                                                             |                |                             |     |
|          |        |               |                                                                                            |                                                             |                |                             |     |
|          |        |               |                                                                                            |                                                             |                |                             |     |
|          |        |               |                                                                                            |                                                             |                |                             |     |
