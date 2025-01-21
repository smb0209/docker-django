FROM python:3.13-bullseye

MAINTAINER Minbong Seo <dev.minbong@gmail.com>

ARG WEB_USER_ID
ARG WEB_GROUP_ID
ARG WEB_HOME_DIR
ARG DEV=false
ARG PROJECT_NAME=${PROJECT_NAME}

RUN addgroup --gid ${WEB_GROUP_ID} user
RUN adduser --gid ${WEB_GROUP_ID} --uid ${WEB_USER_ID} --home /home/user --disabled-password user

RUN mkdir ${WEB_HOME_DIR}
RUN chown -R user:user ${WEB_HOME_DIR}


COPY requirements.txt /tmp/requirements.txt
COPY requirements.dev.txt /tmp/requirements.dev.txt

RUN pip install --upgrade pip && \
    pip install -r /tmp/requirements.txt && \
    if [ $DEV = "true" ]; \
      # 개발용 패키지 설치 명령문
      then pip install -r /tmp/requirements.dev.txt ; \
    fi && \
    rm -rf /tmp

RUN cd /home/user && ln -s ${WEB_HOME_DIR} && chown -R user:user ${WEB_HOME_DIR}

USER user