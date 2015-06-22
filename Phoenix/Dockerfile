FROM ubuntu:15.04
MAINTAINER Johnny Mejias jmejias17@gmail.com

RUN locale-gen en_US.UTF-8
ENV LANGUAGE en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8

RUN apt-get update && apt-get -y install wget curl

RUN echo "deb http://packages.erlang-solutions.com/ubuntu vivid contrib" >> /etc/apt/sources.list

RUN mkdir /Downloads
WORKDIR /Downloads

RUN wget http://packages.erlang-solutions.com/ubuntu/erlang_solutions.asc
RUN apt-key add erlang_solutions.asc
RUN apt-get update && apt-get -y install elixir && mkdir /app

COPY mix.exs /app/mix.exs

WORKDIR /app

RUN git clone https://github.com/phoenixframework/phoenix.git && cd phoenix && git checkout v0.13.1 && mix do local.hex --force, local.rebar, deps.get, compile