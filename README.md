# PX-Programming-Language
It is a normal programming language made by me in JavaScript....

# PX Programming Language

PX is a simple, lightweight programming language designed to be similar to JavaScript but with its own unique syntax and features. It includes support for basic programming constructs, custom import/export mechanisms, and web server functionality.

## Table of Contents

- [Features](#features)
- [Syntax](#syntax)
  - [Variables](#variables)
  - [Functions](#functions)
  - [Imports and Exports](#imports-and-exports)
  - [Web Server](#web-server)
  - [Discord Integration](#discord-integration)
- [PX Package Manager (PXPM)](#px-package-manager-pxpm)
  - [Installation](#installation)
  - [Usage](#usage)
- [Example Code](#example-code)
- [Contributing](#contributing)
- [License](#license)

## Features

- Simple and intuitive syntax
- Support for variable declarations, function definitions, and asynchronous functions
- Supports almost all JavaScript features
- Custom import/export system
- Built-in web server functionality
- Discord.js integration for creating bots [Experimental]
- PX Package Manager (PXPM) for managing packages

## Syntax

### Variables

PX uses `fix` for constants and `let` for variables and `out` for console output:

```px
fix pi = 3.14;
let count = 10;
out(pi + count);
```

### Functions

Functions in PX are defined using `func` and `async func` for asynchronous functions:

```px
func greet(name) {
    out("Hello, " + name + "!");
}

async func fetchData(url) {
    let response = await fetch(url);
    let data = await response.json();
    out(data);
}
```

### Imports and Exports

PX uses `inc` for imports and `exp` for exports:

In `module.px`
```px
func greet() {
    out("Hello, World!");
}

exp greet;
```

In `main.px`
```px
inc greet from './module.px';

greet();
```

For importing packages, use `incp`:

In `main.px`
```px
incp colorize from "colors";

func main() {
    out(colorize("Hello, World!", "blue"));
    out(colorize("This is an error message.", "red"));
}

main();
```

### Web Server

PX can start a web server using the `webpx` package:

In `main.px`
```px
incp webpx from "webpx";

fix app = webpx.createApp();

app.get('/', (req, res) => {
    res.writeHead(200, { 'Content-Type': 'text/plain' });
    res.end('Hello, world!\n');
});

app.get('/about', (req, res) => {
    res.writeHead(200, { 'Content-Type': 'text/plain' });
    res.end('About Page\n');
});

app.listen(8080, () => {
    out('Server is running on port 8080');
});
```

### Discord Integration [Experimental / Unavailable]

PX supports Discord.js integration:

```px
enable Discord;

client.on(Discord.Events.messageCreate, (message) => {
    if (message.content === '!ping') {
        message.reply('Pong!');
    }
});

client.login('YOUR_DISCORD_BOT_TOKEN');
```

## PX Package Manager (PXPM)

PXPM is a CLI tool for managing PX packages.

### Installation

To install PXPM globally go to releases and download `pxpm`.

### Usage

Initialize a new PX project:

```sh
pxpm init
```

Install a package from a GitHub repository:

```sh
pxpm install https://github.com/user/repo
```

For example:

```sh
pxpm install https://github.com/meowdev7/colors
```

## Example Code

Here's an example PX file with some features:

```px
incp colorize from "colors";
incp webpx from "webpx";

fix app = webpx.createApp();

func greet(name) {
    out(colorize("Hello, " + name + "!", "blue"));
}

app.get('/', (req, res) => {
    res.writeHead(200, { 'Content-Type': 'text/plain' });
    res.end('Hello, world!\n');
});

app.listen(8080, () => {
    out("Web server enabled!");
    greet("World");
});
```

### Made by meowdev7
Open an issue if you find one.
