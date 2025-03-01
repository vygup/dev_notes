
Обычный запуск
```bash
jupyter lab
```

Запуск с указанным портом и IP без открытия браузера
```bash
jupyter lab --ip='0.0.0.0' --port=8888 --no-browser
```

Хеширование пароля для установки на вход
```bash
python -c "import hashlib, os; salt = os.urandom(6).hex(); hashed_password = hashlib.sha1(('MY_PASSWORD' + salt).encode('utf-8')).hexdigest(); print(f'sha1:{salt}:{hashed_password}')"
```

Запуск сервера с указание пароля
```bash
jupyter lab --notebook-dir=/home/vladx/notebooks --no-browser --NotebookApp.password='sha1:' --ip='0.0.0.0' --port=8888