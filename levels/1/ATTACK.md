Pass a filename parameter that was highly likely not to exist, and so attempt could be an empty string.

curl 'http://localhost/ctf/1/?filename=does-not-exist&attempt='

