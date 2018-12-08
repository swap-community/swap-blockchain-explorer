# Swap Blockchain Explorer

 - [https://swap.coinscope.cc/](https://swap.coinscope.cc//)
 - [https://swaptest.coinscope.cc/](https://swaptest.coinscope.cc/) - testnet


[README_original.md](README_original.md)  


## nginx example
```
    server {
        listen       78.46.85.142:443 ssl http2;
        server_name  swaptest.coinscope.cc;

        ssl_certificate      /etc/letsencrypt/live/swaptest.coinscope.cc/fullchain.pem;
        ssl_certificate_key  /etc/letsencrypt/live/swaptest.coinscope.cc/privkey.pem;

        ssl_session_cache    shared:SSL:1m;
        ssl_session_timeout  5m;

        ssl_ciphers  HIGH:!aNULL:!MD5;
        ssl_prefer_server_ciphers  on;


        location ~ ^/?(.*) {
            proxy_pass http://127.0.0.1:8086/$1$is_args$args;
            proxy_buffering off;
            proxy_read_timeout 160;
            proxy_next_upstream error;
        }
    }
```
