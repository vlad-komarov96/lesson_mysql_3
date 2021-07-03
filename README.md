/* Проанализировать структуру БД vk, которую мы создали на занятии, и внести предложения по усовершенствованию (если такие идеи есть). Напишите пожалуйста, всё-ли понятно по структуре. 

По структуре все понятно. Затрудняюсь пока что дать какие-то рекомендации по усовершенствованию. */


/* Добавить необходимую таблицу/таблицы для того, чтобы можно было использовать лайки для медиафайлов, постов и пользователей. */

DROP TABLE IF EXISTS  posts;
CREATE TABLE posts (
	id INT AUTO_INCREMENT NOT NULL PRIMARY KEY,
	user_id INT NOT NULL,
	post TEXT NOT NULL,
    comment TEXT NOT NULL,
	likes_id INT NOT NULL,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);


DROP TABLE IF EXISTS  likes;
CREATE TABLE likes (
	id INT AUTO_INCREMENT NOT NULL PRIMARY KEY,
    user_id INT NOT NULL,
    post_id INT NOT NULL,
    likes_id INT NOT NULL,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

ALTER TABLE posts ADD CONSTRAINT fk_posts_user_id FOREIGN  KEY (user_id) REFERENCES likes(id);
ALTER TABLE posts ADD CONSTRAINT fk_posts_likes_id FOREIGN  KEY (likes_id) REFERENCES users(id);

/* Используя сервис http://filldb.info или другой по вашему желанию, сгенерировать тестовые данные для всех таблиц, учитывая логику связей. Для всех таблиц, где это имеет смысл, создать не менее 100 строк. Создать локально БД vk и загрузить в неё тестовые данные.



Создал текстовые данные для таблицы users. Остальные не могу заполнить данными из-за ошибки.

Table name is required as parameter for column user_id
The parameters for foreighKey function are invalid, table: [] or field: [id] is invalid */
