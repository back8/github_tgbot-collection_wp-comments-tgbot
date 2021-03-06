# wp-comments-tgbot
A Telegram Bot for WordPress comments! Simple and fast reply to your comments!
![](pics/1.png)

![](pics/2.jpg)

# Warning
By using this plugin, you agree to open Basic Auth on your WordPress.

Please setup a complex passphrase for your WordPress

# Requirements
1. WordPress native comment system.

2. Network connection to Telegram.

# General guide
## 1. Install plugin
ssh to your blog
```shell script
cd /path/to/root/wp-content/plugins
git clone https://github.com/BennyThink/wp-comments-tgbot
``` 

Then navigate to your Plugin and enable WordPress Comments Telegram Bot.
## 2. Create bot and find your user id
Talk to [@BotFather](https://t.me/BotFather), create your own bot and copy bot token.

Talk to [@get_id_bot](https://t.me/get_id_bot), get your own user id.

## 3. Edit configuration on WordPress
Fill in your token, user id and proxy if needed.
![Alt text](pics/plugin.png)

## 3. Download binary on GitHub Release
[GitHub Release](https://github.com/BennyThink/wp-comments-tgbot/releases)

## 4. Create config
Create your own `config.json`
```json
{
  "username": "admin",
  "password": "admin",
  "url": "http://localhost/",
  "token": "907J6Tw",
  "uid": "23231321",
  "admin": 1,
  "tail": "本评论由Telegram Bot回复～❤️"
}
```
Explanations:
* username & password: username and password for WordPress
* url: site url, must include `/` as suffix.
* token: Telegram bot token
* uid: your Telegram user id
* admin: your user id in WordPress, typically it should be 1
* tail: suffix message to your reply.

## 5. Run
Supply `config.json` as `-c /path/tp/config.json`. By default it will search on working directory.
```shell script
chmod u+x /path/to/bot
/path/to/bot -c /path/to/config.json
```
### cli arguments
```text
  -c file  set configuration file (default "config.json")
  -f      force to run even on http sites.
  -h      this help
  -v      show version and exit
```
# Q&A
## 1. No email notifications while replying by telegram bot?
Potentially bug about your theme/plugin. Try to find the code of sending email.

You may find some hook like this:
``php
add_action('comment_post', 'comment_mail_notify');	
``
Change `comment_post` to `wp_insert_comment` will solve this issue.

[Reference commit](https://github.com/BennyThink/WordPressGit/commit/c64a3a5e70e10239ba9217debf16a075e2a13874)

# Credits
* [Basic Auth](https://github.com/WP-API/Basic-Auth)

# License
GPLv2