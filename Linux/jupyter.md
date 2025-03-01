jupyter lab

jupyter lab --ip='0.0.0.0' --port=8888 --no-browser

python -c "import hashlib, os; salt = os.urandom(6).hex(); hashed_password = hashlib.sha1(('MY_PASSWORD' + salt).encode('utf-8')).hexdigest(); print(f'sha1:{salt}:{hashed_password}')"

jupyter lab --notebook-dir=/home/vladx/notebooks --no-browser --NotebookApp.password='sha1:' --ip='0.0.0.0' --port=8888