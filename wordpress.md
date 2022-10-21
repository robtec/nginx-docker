location / {
      
           proxy_pass  http://localhost:8000;
           proxy_redirect     off;
           proxy_set_header   Host $host;
           proxy_set_header   X-Real-IP $remote_addr;
           proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
           proxy_set_header   X-Forwarded-Host $server_name;
           proxy_set_header   X-Forwarded-Proto https;
           proxy_set_header   Upgrade $http_upgrade;
           proxy_set_header   Connection "upgrade";
           proxy_read_timeout 86400;
        }


define('FORCE_SSL_ADMIN', true);

if (strpos($_SERVER['HTTP_X_FORWARDED_PROTO'], 'https') !== false){
    $_SERVER['HTTPS'] = 'on';
    $_SERVER['SERVER_PORT'] = 443;
}
if (isset($_SERVER['HTTP_X_FORWARDED_HOST'])) {
    $_SERVER['HTTP_HOST'] = $_SERVER['HTTP_X_FORWARDED_HOST'];
}

define('WP_HOME','https://www.aispider.cc/');
define('WP_SITEURL','https://www.aispider.cc/');
