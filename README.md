<div align="center">
  <h1>nexus</h1>
  <h4 align="center">Self-hosteable social network</h4>
</div>

<div align="center">

![Build](https://github.com/whizzbit/nexus-server/workflows/build/badge.svg)
![Lint](https://github.com/whizzbit/nexus-server/workflows/fmt/badge.svg)

</div>

>  Nexus formal definition: a relationship or connection between people or things. [Source][5].

# Deployment

This application is published to a Heroku Dyno instance using the
[emk/heroku-buildpack-rust][6] on every push to `main` [throught this action][7].

# Development

## Requirements

- Rust and Cargo ([Rustup](https://rustup.rs))
- [Diesel CLI](#install-diesel-cli)

## Getting Started

1. Clone this repository

```bash
git clone https://github.com/whizzbit/nexus-server.git
```

2. Create a copy of `.env.sample` in a new file with the name: `.env`

3. Execute Docker containers running `docker-compose up`

4. Run database migrations running `diesel migration run`. [You must complete Diesel Setup First](#install-diesel-cli).

5. Open a new terminal session and run the server

```bash
cargo run
```

## Install Diesel CLI

This project uses Diesel ORM to perform database related operations.

It's recommended to install the Diesel CLI binary using `cargo install`
to use this project.

1. Install `libpq`

1.1. (macOS) Install `libpq` using Homebrew

```bash
brew install libpq
```

1.2. (Ubuntu/Linux) Install `libpq` using `apt-get`

```bash
sudo apt-get update && sudo apt-get install libpq-dev
```

> [Issues? Perhaps this StackExchange question may help][4].

2. The add the library to your PATH

```bash
echo 'export PATH="/usr/local/opt/libpq/bin:$PATH"' >> ~/.zshrc
```

3. Finally install Diesel CLI

```bash
cargo install diesel_cli --no-default-features --features "postgres"
```

## GraphQL

The API exposed is build using async-graphql, which is a GraphQL implementation
build for Rust.

Visit the playground on [http://host:port/graphql][3], when running
the project locally.

> This GraphQL implementation uses the [Cursors Connections Pattern][2].

### The `DateTime` scalar

Our GraphQL gateway implements the `DateTime` scalar to specify date values.
You can read more on this scalar here: [DateTime][1].

# Contributing

Every kind of contribution to this project is welcome, please, don't hesitate
to open a Pull Request or Issue. I will be happy to help!

[1]: https://www.graphql-scalars.com/date-time/#only-date-time
[2]: https://relay.dev/graphql/connections.htm
[3]: http://0.0.0.0:7878/graphql
[4]: https://askubuntu.com/a/713442
[5]: https://www.merriam-webster.com/dictionary/nexus
[6]: https://github.com/emk/heroku-buildpack-rust.git
[7]: https://github.com/whizzbit/nexus-api/blob/main/.github/workflows/deploy.yml