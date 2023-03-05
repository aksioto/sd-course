### Задача

Спроектировать базу(ы) данных для социальной сети ВКонтакте:
- анкеты людей (имя, описание, фото, город, интересы, …)
- посты (описание, фото / видео / аудио, хэштеги, лайки, просмотры, комментарии …)
- личные сообщения и чаты (текст, прочитанность сообщений)
- отношения (друзья, подписчики)
- сообщества (люди, посты)
- медиа (фото, аудио, видео

---

### Решение

Для хранения медиа используем s3.

#### users
```
id
name
description
blob_id
city_id
interests
```

#### cities
```
id
name
```

#### relationships
Используем графовую бд
```
User
 user_id

User -- friends_with --> User
User -- is_following --> User
```

#### groups
```
id
name
owneer_id
```

#### group_users
```
group_id
user_id
```

#### chats
```
id
name
description
...
```

#### chat_users
```
chat_id
user_id
lastseen // timestamp
```

#### messages
```
id
chat_id
user_id
text
created_at
```

#### posts
```
id
user_id
group_id
status // опубликовано/отложено
description
created_at
```

#### posts_meta
```
id
post_id
views
```

#### posts_likes
```
post_id
user_id
... сюда ещё можно тип реакции поставить
```

#### media
```
id
post_id
blob_id
media_type // tinyint
```

#### tags
```
id
post_id
name
```

#### comments
```
id
post_id
user_id
reply_to_id
text
created_at
```