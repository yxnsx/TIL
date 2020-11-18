# :fire: Retrofit2
* 안드로이드와 자바를 위한 type-safe HTTP Client이다.
* 인터페이스 메소드 또는 매개변수에 대한 어노테이션은 HTTP 요청이 처리되는 방법을 나타낸다.
<br>

### :sparkles: Retrofit2 Implementation
* build.gradle(Module: app)에서 retrofit 및 변환기 종속성 선언
```xml
dependencies {
    implementation 'com.squareup.retrofit2:retrofit:2.9.0' // 201118 기준 최신 버전
    implementation 'com.google.code.gson:gson:2.8.6' // 변환기로 gson을 사용할 경우 추가
}
```
<br>

### :sparkles: Retrofit2 Configuration
* 서버통신을 위해 manifest 파일에 인터넷 사용 권한을 추가해주어야 한다.
* retrofit 클래스는 API 인터페이스가 호출 가능한 객체로 변환되도록 한다.
* RequestBody 유형에 따라 직렬화 라이브러리를 변환기로 설정할 수 있다.

```java
Retrofit retrofit = new Retrofit.Builder()
    .baseUrl("https://api.github.com/")
    .addConverterFactory(GsonConverterFactory.create()) // 변환기로 Gson 라이브러리 설정
    .build();

GitHubService service = retrofit.create(GitHubService.class);
```
<br>

### :sparkles: Retrofit2 API 선언
#### :zap: 요청 방법
* 모든 메소드에는 요청 메소드와 상대 URL을 제공하는 HTTP 어노테이션이 있어야 한다.
* HTTP 어노테이션은 총 8개가 있다. `HTTP`, `GET`, `POST`, `PUT`, `PATCH`, `DELETE`, `OPTIONS`, `HEAD`

```java
// 자원의 상대 URL을 어노테이션에 지정
@GET("users/list")

// 자원의 상대 URL에 쿼리 매개변수 지정
@GET("users/list?sort=desc")
```
<br>

#### :zap: URL 조작
* 메소드의 대체 블록 및 매개변수를 사용하여 요청 URL을 동적으로 업데이트 할 수 있다.
* 대체 블록은 `{}`로 둘러싸인 영숫자 문자열이다.
* `@Path` 어노테이션을 사용하여 대체 블록과 동일한 문자열을 선언하는 주석을 달아주어야 한다.

```java
// 대체 블록 및 매개변수를 이용하여 동적으로 URL 업데이트
@GET("group/{id}/users")
Call<List<User>> groupList(@Path("id") int groupId);

// 동적 URL에 쿼리 매개변수 추가
@GET("group/{id}/users")
Call<List<User>> groupList(@Path("id") int groupId, @Query("sort") String sort);

// 동적 URL에 Map 형태의 복잡한 쿼리 매개변수 추가
@GET("group/{id}/users")
Call<List<User>> groupList(@Path("id") int groupId, @QueryMap Map<String, String> options);
```
<br>

#### :zap: Request Body
* `@Body` 어노테이션을 사용하여 요청 응답을 특정 오브젝트로 변환할 수 있다.
* 응답은 `retrofit` 인스턴스에 지정된 변환기를 사용하여 변환된다.
* 변환기가 추가되지 않은 경우에만 `RequestBody`를 사용할 수 있다.

```java
@POST("users/new")
Call<User> createUser(@Body User user);
```
<br>

#### :zap: 폼 인코딩 및 Multipart
* `@FormUrlEncoded`어노테이션을 사용하여 폼 인코딩된 데이터를 전송할 수 있다.
* 각 키-값 쌍의 `@Field` 어노테이션에는 이름과 값을 제공하는 객체를 선언한다.

```java
// @FormUrlEncoded와 @Field를 사용한 폼 데이터 요청
@FormUrlEncoded
@POST("user/edit")
Call<User> updateUser(@Field("first_name") String first, @Field("last_name") String last);

// @Multipart와 @Part를 사용한 멀티파트 요청
@Multipart
@PUT("user/photo")
Call<User> updateUser(@Part("photo") RequestBody photo, @Part("description") RequestBody description);
```
<br>

#### :zap: 헤더 조작
* `@Headers`어노테이션을 사용하여 메서드에 대한 정적 헤더를 설정할 수 있다.
* 헤더는 서로 덮어쓰지 않으며, 동일한 이름의 모든 헤더가 요청에 포함된다.
* 요청 URL 헤더는 `@Header` 주석을 사용하여 동적으로 업데이트 할 수 있다.

```java
// @Headers를 사용한 정적 헤더 설정 (1)
@Headers("Cache-Control: max-age=640000")
@GET("widget/list")
Call<List<Widget>> widgetList();

// @Headers를 사용한 정적 헤더 설정 (2)
@Headers({
    "Accept: application/vnd.github.v3.full+json",
    "User-Agent: Retrofit-Sample-App"
})
@GET("users/{username}")
Call<User> getUser(@Path("username") String username);

// @Header를 사용한 동적 헤더 설정
@GET("user")
Call<User> getUser(@Header("Authorization") String authorization)

// @HeaderMap을 사용한 Map 형태의 복잡한 동적 헤더 설정
@GET("user")
Call<User> getUser(@HeaderMap Map<String, String> headers)
```
<br>

### :memo: Reference
* https://square.github.io/retrofit/
