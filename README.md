# Получение ленты
**URL** : `/api/feed`
**Method** : `GET`


### Успешный ответ

**Code** : `200 OK`


```json
{
  "posts": [
    {
      "author_id": "ObjectID()",
      "post_id": "12345",
      "text": "Post 1",
      "file_urls": [
        "https://post.com/image1.jpg",
        "https://post.com/image2.jpg"
      ],
      "likes": [
        "ObjectID()",
        "ObjectID()",
        "ObjectID()"
      ],
      "date": "2024-01-01",
      "comments": [
        {
          "author_id": "ObjectID()",
          "text": "Comment 1",
          "likes": [
            "ObjectID()",
            "ObjectID()"
          ],
          "re_comments": []
        }
      ]
    },
    {
      "author_id": "ObjectID()",
      "post_id": "6789",
      "text": "Post 2",
      "file_urls": [
        "https://post.com/image.jpg"
      ],
      "likes": [
        "ObjectID()",
        "ObjectID()"
      ],
      "date": "2024-02-02",
      "comments": [
        {
          "author_id": "ObjectID()",
          "text": "Comment 1",
          "likes": [
            "ObjectID()",
            "ObjectID()"
          ],
          "re_comments": []
        },
        {
          "author_id": "ObjectID()",
          "text": "Comment 2",
          "likes": [
            "ObjectID()",
            "ObjectID()"
          ],
          "re_comments": [
            {
              "author_id": "ObjectID()",
              "text": "Recomment",
              "likes": []
            }
          ]
        }
      ]
    }
  ]
}
```


# Публикация постов

**URL** : `/posts`
**Method** : `POST`

### Запрос

```json
{
    "author_id": "ObjectID()",
    "text": "Текст поста",
    "image_url": "https://post.com/image.jpg" 
}
```
### Успешный ответ

**Code** : `200 OK`
```json
{
    "success": true,
    "posts": {
        "post_id": "12345",
        "author_id": "ObjectID()",
        "text": "Текст поста",
        "image_url": "https://post.com/image.jpg" 
        "date": "2024-10-10"
    }
}
```

# Удаление поста

**URL** : `/posts/:post_id`

**URL PARAMETRES** :`post_id=[integer]` - ID поста, который нужно удалить

**Method** : `DELETE`

### Успешный ответ

**Условие** : Указан верный ID поста

**Code** : `204 NO CONTENT`

```json
{
    "success": true,
    "message": "Пост успешно удалён"
}
```
### Ошибка

**Условие** : Пост с указанным ID не существует

**Code** : `404 NOT FOUND`

```json
{
    "success": false,
    "message": "Ошибка: пост не найден"
}
```



# Получение списка комментариев
# Оставить комментарий
**URL** : `/posts/:post_id/comments`

**URL PARAMETRES** :`post_id=[integer]` - ID поста, на который нужно оставить комментарий

**Method** : `POST`
### Запрос

```json
{
    "author_id": "ObjectID()",
    "text": "Текст комментария"
}
```
### Успешный ответ

**Code** : `200 OK`
```json
{
    "success": true,
    "comments": {
        "author_id": "ObjectID()",
        "comment_id": "98765",
        "date": "2024-10-10"
        "text": "Текст комментария",
        "date": "2024-10-13"
    }
}
```

# Удалить комментарий

**URL** : `/posts/:post_id/comments`

**URL PARAMETRES** :`post_id=[integer]` - ID поста, на который нужно оставить комментарий

**Method** : `DELETE`
### Успешный ответ

**Code** : `204 NO CONTENT`
```json
{
    "success": true,
    "message": "Комментарий успешно удалён"
}
```

# Ответить на комментарий
**URL** : `/posts/:post_id/comments/:comment_id`

**URL PARAMETRES** :`post_id=[integer]` - ID поста, `:comment_id=[integer]` - ID коментария, на который нужно ответить

**Method** : `POST`
### Запрос

```json
{
    "author_id": "ObjectID()",
    "text": "Текст комментария"
}
```
### Успешный ответ

**Code** : `200 OK`
```json
{
    "success": true,
    "comments": {
        "author_id": "ObjectID()",
        "comment_id": "54321",
        "date": "2024-10-10"
        "text": "Текст ответа на комментарий",
        "date": "2024-11-13"
    }
}
```


# Получение списка лайков

# Поставить лайк
**URL** : `/posts/:post_id`

**URL PARAMETRES** :`post_id=[integer]` - ID поста, на который нужно поставить лайк

**Method** : `POST`

### Успешный ответ

**Условие** : Указан верный ID поста

**Code** : `200 OK`

```json
{
    "success": true,
    "message": "Лайк успешно добавлен"
}
```
### Ошибка

**Условие** : Пост с указанным ID не существует

**Code** : `404 NOT FOUND`

```json
{
    "success": false,
    "message": "Ошибка: пост не найден"
}
```

# Убрать лайк

**URL** : `/posts/:post_id`

**URL PARAMETRES** :`post_id=[integer]` - ID поста, с которого нужно убрать лайк

**Method** : `DELETE`

### Успешный ответ

**Условие** : Указан верный ID поста

**Code** : `200 OK`

```json
{
    "success": true,
    "message": "Лайк успешно удалён"
}
```
### Ошибка

**Условие** : Пост с указанным ID не существует

**Code** : `404 NOT FOUND`

```json
{
    "success": false,
    "message": "Ошибка: пост не найден"
}
```

