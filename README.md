# Make The Pix

![showcase](https://github.com/mKsDEV08/makethepix/blob/master/alert-server/static/images/makethepix_showcase.gif)

## Installation

Cloning repo

```cli
git clone https://github.com/mKsDEV08/makethepix.git
```

Creating Python virtual enviroment

```cli
python3 -m venv .venv
source .venv/bin/activate
```

Setting-up database

```sql
CREATE DATABASE makethepix;
USE makethepix;
```
```sql
CREATE TABLE `users` (
  `id` int NOT NULL AUTO_INCREMENT,
  `username` varchar(16) NOT NULL,
  `password_hash` varchar(162) NOT NULL,
  `alert_id` varchar(24) NOT NULL,
  `balance` double NOT NULL,
  `lang_choose` varchar(6) DEFAULT 'com.br',
  `pix_key` text NOT NULL,
  `pitch_choose` double NOT NULL,
  PRIMARY KEY (`id`)
);
```
```sql
CREATE TABLE `messages` (
  `id` int NOT NULL AUTO_INCREMENT,
  `message` varchar(300) NOT NULL,
  `sender_name` varchar(16) NOT NULL,
  `status` varchar(8) DEFAULT 'pending',
  `value` double NOT NULL,
  `receiver_alert_id` varchar(24) NOT NULL,
  PRIMARY KEY (`id`)
);
```

### alert-server

Installing `alert-server` dependencies

```cli
cd alert-server
pip install -r requirements.txt
```

Change MySQL credentials on `helpers.py`
```python
connection = mysql.connector.connect(
    user = 'root',
    host = 'localhost',
    password = 'password',
    database = 'makethepix'
)
```

Starting `alert-server`

```cli
python wsig.py
```
