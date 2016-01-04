FROM ubuntu:14.04

MAINTAINER Johnny Mejias <jmejias17@gmail.com>

RUN export DEBIAN_FRONTEND=noninteractive && \
    apt-get update -q && \
    apt-get -y install curl locales && \
    locale-gen "en_US.UTF-8" && \
    export LANG=en_US.UTF-8 && \
    curl -o /tmp/erlang.deb http://packages.erlang-solutions.com/erlang-solutions_1.0_all.deb && \
    dpkg -i /tmp/erlang.deb && \
    rm -rf /tmp/erlang.deb && \
    apt-get update -q && \
    apt-get install -y build-essential postgresql-client && \ 
    apt-get install -y erlang-base=1:18.2 erlang-dev=1:18.2 erlang-eunit=1:18.2 erlang-parsetools=1:18.2 erlang-xmerl=1:18.2 elixir=1.1.1-2 && \
    apt-get clean -y && \
    rm -rf /var/cache/apt/*

ENV LANG=en_US.UTF-8

RUN mix local.hex --force && \
    mix local.rebar --force

COPY . /usr/src/app
WORKDIR /usr/src/app

RUN mix do deps.get, compile

EXPOSE 4000

CMD ["mix", "phoenix.server"]
