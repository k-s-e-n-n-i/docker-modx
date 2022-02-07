https://modx.pro/howto/19078
https://docs.docker.com/compose/environment-variables/

docker-compose build
docker-compose --env-file .env.development up
docker-compose --env-file .env.development up -d

Перенос modx
Можно не обновлять.
1. Пропишите новый путь к core в этих файлах:
/config.core.php
/manager/config.core.php
/connectors/config.core.php
/core/config/config.inc.php

2. Очистите полностью /core/cache/