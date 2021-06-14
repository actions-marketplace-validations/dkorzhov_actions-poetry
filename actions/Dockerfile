FROM python:3.8-alpine3.12

# System deps:
RUN apk update && apk add libc-dev zeromq-dev g++ git \
    build-base \
    cargo \
    gcc \
    jpeg-dev \
    libffi-dev \
    openjpeg-dev \
    openssl-dev \
    py-cffi \
    python3-dev \
    rust \
    zlib-dev

RUN pip install --upgrade setuptools

RUN pip --no-cache-dir install poetry

RUN echo "http://dl-cdn.alpinelinux.org/alpine/v3.12/community" >> /etc/apk/repositories \ 
    && apk update   && apk add --update-cache --no-cache libgcc libquadmath musl \
    && apk add --update-cache --no-cache libgfortran \ 
    && apk add --update-cache --no-cache gfortran freetype-dev libpng-dev openblas-dev lapack-dev

#RUN pip3 install pyzmq pillow kiwisolver scipy

WORKDIR /usr/src/app
COPY poetry.lock pyproject.toml /usr/src/app/
RUN poetry install --no-interaction --no-ansi

WORKDIR /opt/app

CMD [ "/bin/sh" ]