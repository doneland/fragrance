FROM python:3.8.0-alpine
WORKDIR /usr/src/app
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Install psycopg2 dependencies.
RUN apk update \
    && apk add postgresql-dev gcc python3-dev musl-dev

# Install dependencies.
RUN pip install --upgrade pip
COPY ./requirements.txt /usr/src/app/requirements.txt
RUN pip install -r requirements.txt

# Copy entrypoint.
COPY ./entrypoint.sh /usr/src/app/entrypoint.sh

# Copy project to container.
COPY . /usr/src/app

# Run entrypoint.
ENTRYPOINT [ "/usr/src/app/entrypoint.sh" ]