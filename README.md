
# Лабораторная работа №5  
## Безопасность WordPress


## Цель работы  
Закрепить основные практики безопасности WordPress: управление пользователями и паролями, обновления, базовый hardening, резервное копирование, а также настройка плагина All In One WP Security & Firewall (AIOS).


## Шаг 1. Подготовка среды  

Использовалась локальная установка WordPress (XAMPP).  
В файле `wp-config.php` включен режим отладки:

```php
define('WP_DEBUG', true);
````


## Шаг 2. Управление ролями и паролями

Был создан тестовый пользователь:

* Логин: testuser
* Роль: Автор

Для всех пользователей проверены сложные пароли (буквы, цифры, символы).
<img width="942" height="908" alt="Image" src="https://github.com/user-attachments/assets/9b31f652-65a9-4548-a327-534c8e279b6c" />

<img width="941" height="525" alt="Image" src="https://github.com/user-attachments/assets/8f43ccef-e834-4a35-a4f1-1e60bac4e763" />
## Шаг 3. Обновления

Были выполнены обновления:

* WordPress (ядро)
* Плагины
* Темы

<img width="691" height="407" alt="Image" src="https://github.com/user-attachments/assets/95e576f8-75af-489e-a68e-80476881a2c6" />

## Шаг 4. Базовая защита (Hardening)

### Отключение редактора файлов

В файл `wp-config.php` добавлено:

```php
define('DISALLOW_FILE_EDIT', true);
```
<img width="408" height="72" alt="Image" src="https://github.com/user-attachments/assets/3dad5ae6-9a4b-4c32-9060-4ca8a6c57465" />
### Права доступа

* Папки: 755
* Файлы: 644


### Защита wp-config.php

В файл `.htaccess` добавлено:

```apache
<files wp-config.php>
   order allow,deny
   deny from all
</files>
```
<img width="637" height="399" alt="Image" src="https://github.com/user-attachments/assets/1b85ff2e-f119-4b56-a770-bdd046d8f91d" />

## Шаг 5. Установка плагина безопасности

Установлен и активирован плагин:

**All In One WP Security & Firewall (AIOS)**
<img width="947" height="366" alt="Image" src="https://github.com/user-attachments/assets/fec562f6-314d-4295-b6b8-c800a6291aea" />

## Шаг 6. Настройка безопасности

### Защита входа (Login Lockdown)

Настроено:

* Максимум попыток: 5
* Время повторной попытки: 15 минут
* Блокировка: 30 минут

<img width="229" height="809" alt="Image" src="https://github.com/user-attachments/assets/2fb72249-862c-489d-bf0f-e2036c5003b7" />

### Принудительный выход

Настроено автоматическое завершение сессии через 24 часа.

<img width="926" height="895" alt="Image" src="https://github.com/user-attachments/assets/2f442854-5f30-44aa-92c1-4106cc26a14d" />

### Firewall

Активированы:

* Базовая защита
* Защита от XSS
* Фильтрация вредоносных запросов
<img width="909" height="464" alt="Image" src="https://github.com/user-attachments/assets/bbce1162-e202-4538-825b-94dc17fc824b" />
<img width="914" height="865" alt="Image" src="https://github.com/user-attachments/assets/3285c8c8-6b1c-4a54-b6a0-2c726e7578fc" />
<img width="928" height="548" alt="Image" src="https://github.com/user-attachments/assets/28486a6c-8bec-4887-9e9b-af2933135b42" />
<img width="923" height="672" alt="Image" src="https://github.com/user-attachments/assets/895dafad-7b1a-4efb-90da-0ce58c5172bc" />
### Изменение URL входа

Стандартный URL `/wp-login.php` заменён на:

```
http://localhost/wp_lab2/secure-login
```
<img width="926" height="731" alt="Image" src="https://github.com/user-attachments/assets/3fababbe-3bfc-41c9-b524-23ad6a13b728" />

### Резервное копирование

Создан backup базы данных через AIOS.

## Шаг 7. Тестирование защиты

Проведён тест brute-force:

* Введён неправильный пароль несколько раз
* После 5 попыток доступ был заблокирован


## Шаг 8. Восстановление из backup

Проверена возможность восстановления данных из резервной копии.


## Вывод

В ходе работы были реализованы основные меры безопасности WordPress:

* защита авторизации
* настройка firewall
* изменение URL входа
* резервное копирование
* базовый hardening

Эти меры значительно повышают безопасность сайта и защищают его от атак.


