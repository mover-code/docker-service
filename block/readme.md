# 部署步骤

## 1. 修改conf/genesisi.json 中的挖矿地址 extraData   运行 `./geth init conf/genesisi.json --datadir ./data`  初始化

## 2. 将解锁密码写入conf/password.txt中   

## 3. `./geth account import 私钥文件.txt` 之后在root/.ethereum/keystore 文件下可以找到导入账户  然后复制到 data/keystore  此账户与上述挖矿地址账户一致

## 4. docker-compose up -d 拉取镜像

## 5. 修改容器blockChain 信息  `docker commit -c 'CMD ./geth --verbosity 1 --datadir data --config conf/geth.toml --networkid=(你希望的chainId) --gcmode archive --unlock (你的挖矿账户) --password conf/password.txt' blockChain ch:latest`

## 6. 修改docker-compose.yaml 容器中blockChain 的image 改为 上一步构建的 ch:latest

## 7. 运行docker-compose up -d

``` yaml
还需要nginx配置    location /socket {
        proxy_redirect off;
        proxy_pass http://127.0.0.1:4000; #转发到你本地的 9501 端口 对应 ws 的端口
        proxy_set_header Host $host;
        proxy_set_header X-Real_IP $remote_addr;
        proxy_set_header X-Forwarded-For $remote_addr:$remote_port;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection upgrade;
    }
合约验证的解决办法
```
