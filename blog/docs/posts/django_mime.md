---
date: 2023-12-08
categories:
    - knowledge-base
    - django
    - nginx
---

# django app: Resource blocked due to MIME type mismatch

Running your Django app first time in production, you might bump into the issue of your browser blocking static resources (.css, .js) with a message "Resource blocked due to MIME type mismatch". I was googling a bit here and there, most results are providing a bit context demanding answers.

!!! Info ""Hint""
    The X-Content-Type-Options response HTTP header is a marker used by the server to indicate that the MIME types advertised in the Content-Type headers should be followed and not be changed.


    **(The document provided by the <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Content-Type-Options?utm_source=mozilla&utm_medium=firefox-console-errors&utm_campaign=default">link</a> "explaining" the issue in the browser)**

Dude, what do I do? Some answers on Stack Overflow recommend to turn of security features in your browser. Well, swiping the issue under the carpet does not make it go.

<!-- more -->

Long story short, running Django in production, you just have to properly set up your Nginx.
The instruction presumes you have everything going fine with **DEBUG = True** in your Django settings.

If you have your project static files in the folder **/var/www/mysite/myapp/myapp/static**, add the following **location** block to your server in nginx configuration:

!!! Example "nginx config"
    ``` nginx
        location /static/ {
            alias /var/www/mysite/myapp/myapp/static/;
        }
    ```

You would need to add this kind of block for every application in your project, having its own static files.


Restart your nginx, and that should be it.



!!! Tip
    To run your project locally with debug mode off, but keep static files unblocked by MIME type, launch it as usually, but add "--insecure" flag:
    ```
      $ ./manage.py runserver --insecure
    ```