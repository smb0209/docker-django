# 최초 세팅 방법 <br/>How to Start
## Web 도커 필요 <br/>Web Docker Container below is needed 
### Web 도커 git : https://github.com/smb0209/docker-web<br/>Web Docker git : https://github.com/smb0209/docker-web

1. python
   1. brew install pyenv
   2. pyenv install --list | grep 3.13
   3. pyenv install 3.13.0
   4. pyenv local 3.13.0
   5. echo -e '\nif command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.zshrc
   6. source ~/.zshrc
2. www-data 하위에 프로젝트가 형성 되어 있어야한다. 하위에서 아래 실행<br/>A project is needed and located in ./www-data. And execute below
   1. python -m venv vpython
   2. source vpython/bin/activate
   3. python -m pip install --upgrade pip
   4. pip install -r ./build/python/requirements.txt
   5. django-admin startproject ${PROJECT_NAME} ./www-data
   6. deactivate
3. docker-compose up -d --build
4. http://${PROJECT_NAME}.localhost