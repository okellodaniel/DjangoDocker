# Pull official base Image

FROM python:3.9.6-alpine

# Set work directory

WORKDIR /usr/src/DjangoOnDocker

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install psycopg2 dependencies
RUN apk update && apk add postgresql-dev gcc python3-dev musl-dev

# install dependenies
RUN pip3 install --upgrade pip
COPY ./requirements.txt .
RUN pip install -r requirements.txt

# Copy entrypoint.sh
COPY ./entrypoint.sh .
RUN sed -i 's/\r$//g' /usr/src/DjangoOnDocker/entrypoint.sh
RUN chmod +x /usr/src/DjangoOnDocker/entrypoint.sh

# copy source code
COPY . .

# run entrypoint.sh
ENTRYPOINT ["/usr/src/DjangoOnDocker/entrypoint.sh"]