FROM python:2-alpine

RUN apk add --no-cache --virtual .build-deps \
    git \
    gcc \
    musl-dev \
    linux-headers \
  && git clone https://github.com/AndreyPavlenko/aceproxy.git \
  && pip install -r aceproxy/requirements.txt \
  && apk del .build-deps \
  && adduser -S -H aceproxy \
  && sed -i \
    -e "s/\(vlcuse =\) False/\1 True/" \
    -e "s/\(videodestroydelay =\) [0-9]*/\1 30/" \
    -e "s/\(vlchost =\) .*/\1 'vlc'/" \
    -e "s/\(acehost =\) .*/\1 'acestream'/" \
    -e "s/\(aceproxyuser =\) .*/\1 'aceproxy'/" \
    aceproxy/aceconfig.py

WORKDIR /aceproxy

CMD ["python", "acehttp.py"]
