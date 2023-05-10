## Nginx Configuration
1. The server

        server {
          listen 80 default_server;
          listen [::]:80 default_server;
          server_name localhost;
        
          location / {
            proxy_set_header HOST $host;
            proxy_set_header X-Forwarded-Proto $scheme;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        
            proxy_pass http://127.0.0.1:3000;
          }
        }
        
2. Delete the default config in sites-enabled
3. Run the command below to symlink the new config file from sites-available to sites-enabled

       sudo ln -s /etc/nginx/sites-available/react /etc/nginx/sites-enabled/

4. Test your configuration to be sure that it is working fine

       sudo nginx -t

5. Restart/reload the Nginx configuration

       sudo systemctl restart nginx

6. Confirm the status of the Nginx configuration

       sudo systemctl status nginx

7. Test your app that it is running fine

        curl localhost:80
        curl localhost:3000