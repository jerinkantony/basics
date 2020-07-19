FROM python:3.6-slim
WORKDIR /usr/src/app
RUN python -m pip install \
      parse 

COPY headlines.py .
CMD ["python", "headlines.py"]


