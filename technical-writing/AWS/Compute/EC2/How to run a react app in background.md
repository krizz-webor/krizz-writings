## How to run a react app in background
Take a look on pm2 this should be exactly what you want.

To install pm2 :

    npm install pm2 -g


To start an application simply just run :

    pm2 start npm -- start
    
You can check logs via:

    pm2 logs
    
To stop current pm2 instances

list the pm2 processes, get the id, lets say the id is 0

    pm2 ps
    
then stop the id

    pm2 stop 0