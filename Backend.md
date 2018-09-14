# Backend

## Django

### field 추가할때 에러가 발생했다!

모델에 user 정보를 넣어야 해서, 어디선가 보고 처음에 아래 코드와 같이 `OneToOneField`를 써서 작성했었는데:

```python
user = models.OneToOneField(User, on_delete=models.CASCADE)
```

아래와 같은 오류가 발생했다.

1.  새 `todo` `item` 을 추가하기 위해 `post` 요청을 보내면 IntegrityError at `/*/` UNIQUE constraint failed: `*_*.*` 에러가 발생
2.  `model` 에 `field` 를 추가하고 (물론 `makemigrations`와 `migrate`를 하고 난 후) `get` 요청을 보내면 OperationalError at `/*/` no such column: `*_*.*` 에러가 발생

찾아보니 아래와 같이 `ForeignKey`를 써야 하는 것이었다.

```python
user = models.ForeignKey(User, on_delete=models.CASCADE)
```

눈물..

## Auth

#### JWT

#### `xxxx.yyyy.zzzz` 처럼 생겼다

token 요청을 하면 JSON 형태로 오지만,

```json
{
  "token": "xxxx.yyyy.zzzz"
}
```

JSON 형태로 쓰는 건 아니라는.

## 짜잘짜잘

> `patch` 요청할 때 `500` 이 뜨는 경우 &rarr; 요청 주소 끝에 `/` 를 빼먹었나 확인해보자.

> 데이터베이스가 꼬였을 때 &rarr; `./manage.py flush` 를 해보자.

> `TemplateDoesNotExist` 에러가 뜰 경우 &rarr; `settings.py` 의 `INSTALLED_APPS` 에 빼먹은게 있나 살펴보자.

> `localhost`를 다른 컴퓨터에서 액세스하기:  
> `runserver <ip address>:8000` 하면 된다.
