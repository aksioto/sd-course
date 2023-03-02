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
photo
city_id
interests
```

#### cities
```
id
name
```

#### relationships
```
id
primary_user_id
secondary_user_id
relationship_type_id
```

#### relationship_type
```
id
name
```

#### groups
```
id
name
owneer_id
```

#### group_users
```
id
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
id
chat_id
user_id
```

#### messages
```
id
chat_id
user_id
text
created_at
```

#### messages_meta
```
id
message_id
user_id
read_status
```

#### posts
```
id
user_id
group_id
status
description
created_at
```

#### posts_meta
```
id
post_id
likes
views
```

#### media
```
id
post_id
url
media_type_id
created_at
```

#### media_types
```
id
name
```

#### tags
```
id
name
```

#### post_tags
```
id
tag_id
post_id
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