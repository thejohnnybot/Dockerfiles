FROM shanesveller/elixir-lang:alpine

WORKDIR /usr/src/app

ADD . /usr/src/app

RUN mix do deps.get, deps.compile

EXPOSE 4000

CMD ["mix", "phoenix.server"]
