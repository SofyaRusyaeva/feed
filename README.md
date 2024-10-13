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
    "content": "Текст поста",
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
        "content": "Текст поста",
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

**Condition** : Указан верный ID поста

**Code** : `204 NO CONTENT`

```json
{
    "success": true,
    "message": "Пост успешно удалён"
}
```
### Ошибка

**Condition** : Пост с указанным ID не существует

**Code** : `404 NOT FOUND`

```json
{
    "success": false,
    "message": "Ошибка: пост не найден"
}
```



# Получение списка комментариев
# Оставить комментарий
# Удалить комментарий
# Ответить на комментарий
# Получение списка лайков
# Поставить лайк
# Убрать лайк
