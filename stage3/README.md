1. Installed nginx
2. Changed default listen port for apache to 81 to avoid conflict with nginx
3. Changed default config for nginx to forward traffic to apache
4. Changed entrypoint to run nginx with apache
