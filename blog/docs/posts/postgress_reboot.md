---
date: 2023-12-25
categories:
    - knowledge-base
    - linux
    - postgres
---

# No /var/run/postgresql/.s.PGSQL after reboot (Ubuntu)

Rebooting the server, bumped into the following error, preventing my django server from functioning: <b>psql: error: connection to server on socket "/var/run/postgresql/.s.PGSQL.xxxx" failed: No such file or directory</b>

Not to easy to search the solution, tons of search spam (and of course stupid advises "purge porstgresql including databases and all the files and reinstall".

Thanks to Abdallah: <a href="https://www.abdallahyashir.com/how-to-fix-postgresql-error-connection-to-server-on-socket-failed/">https://www.abdallahyashir.com/how-to-fix-postgresql-error-connection-to-server-on-socket-failed/</a>

!!! example "Shellscript"

    ``` sh
        $ sudo -i -u postgres
        $ /usr/lib/postgresql/14/bin/pg_ctl restart -D /var/lib/postgresql/14/main
    ```
