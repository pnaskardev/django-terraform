# pull official base image
FROM python:3.12.0-alpine

# set work directory
WORKDIR /usr/src/app

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install dependencies
RUN apk update && \
    apk add --no-cache gcc musl-dev libffi-dev && \
    pip install --upgrade pip

COPY ./requirements.txt .
RUN pip install -r requirements.txt

# Create a user with UID 1000 and GID 1000
RUN addgroup -g 1000 appgroup && \
    adduser -D -u 1000 -G appgroup appuser
# Switch to this user
USER appuser

# copy project
COPY . .