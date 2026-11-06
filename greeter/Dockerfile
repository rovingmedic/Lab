#!/bin/bash

FROM ubuntu:24.04

WORKDIR /app

COPY greet .

RUN chmod +x greet

ENV GREETING="Howzit"
ENV NAME="Shaun"

CMD ["./greet"]

