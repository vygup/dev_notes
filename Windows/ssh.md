Перенос данных на сервер `scp`
```bash
scp -P 22 file remote_host:/directory
```

Перенос данных на примере записи в файл на сервере
```bash
cat id_rsa.pub | ssh -p 22 remote_host "cat >> ~/directory/file"
```