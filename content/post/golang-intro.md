---
author:
  description: danielfbm
  email: danielfbm@gmail.com
  github: https://github.com/danielfbm
  image: /images/avatar-64x64.png
  name: danielfbm
  twitter: https://twitter.com/danielfbm
  website: http://danielfbm.github.io/
categories:
- golang
- programming languages
date: 2017-01-31T23:00:00+08:00
description: first post with Hugo website engine
tags:
- golang
- go
- programming languages
- introduction
title: Golang introduction
draft: true
---

This is for those interested in the **go** programming language. This is my take as an introduction on this amazing language

Honestly there is plenty of resources on the web about [golang][golang] to fill a lot of content. This post is merely a summary of the things I find most useful and what attracts me the most while programming in [go][golang]


#### TL; DR

To install simply download the package for your OS in the [golang official download page][godownload]

If you are on macOS and have brew installed: `brew update && brew install golang` 

Check the examples on [this git repo](https://github.com/danielfbm/go-intro) to play:

```sh
# using the terminal of your choice navigate to the repo folder
go run <filename>.go
```

In general [golang][golang] is a very simple, modern and pleasant to use programming language. It is worth giving it a shot specially because of its impressive performance.

#### Download and Setup

If you don't have it installed head right to the official webpage and [download it][godownload].

After the setup, try the following command in your favorite terminal

```sh
go version
```

If everything was setup correctly you will be able to see the installed version and the platform in which you installed it.

As opposite to many languages, **go** uses *one main workspace* meaning that all your code, and the downloaded third party libraries will cohexist in the same folder structure. This sounds kind of weird in the beginning and most people would prefer to organize their projects in different paths. 

To set a workspace just set the `GOPATH` environment variable. An example would be to set this environment in a `go` folder in the user's home folder:

```sh
export GOPATH=~/go
```

Inside the workspace you can create three folders:

- `bin` stores all the compiled *golang* projects
- `src` stores all the source code
- `pkg` stores your OS related tools

If you are using a UNIX like system, just add the `export GOPATH` command in your `.profile` or `.bash_profile` to be loaded as soon as the user is logged in terminal.

You can find more information regarding the Go installation and workspace

- [Official documentation](https://golang.org/doc/install)
- [Post from William Kennedy](https://www.goinggo.net/2016/05/installing-go-and-your-workspace.html)



#### IDE

Although there are many idealists that follow the `vim` philosophy of coding, I prefer more complex and easier to use IDEs. Golang doesn't have any official IDE and probably never will, mostly because all the necessary tools either come with the **go** installer, or can be easily installed. 

Here I will explain the one I use and how to set it up for **go**.

##### Microsoft's Visual Studio Code

This lightweight IDE works perfectly for me and I have used it for several months and I really enjoy how you can integrate with the golang standard tooling. You can [download it here](https://code.visualstudio.com/Download).

By itself this IDE's features are not very impressive, but the main basics for any IDE. Its power comes from its Extensions. Besides browsing and searching for extensions from inside the IDE (`Shift + CMD + X ` on macOS), [VS Code's Extension Marketplace](https://marketplace.visualstudio.com/VSCode) website have as well the same feature.

To support **go** we will first install the [vscode-go](https://marketplace.visualstudio.com/items/lukehoban.Go) extension. Its source code is hosted on [this GitHub repo](https://github.com/Microsoft/vscode-go). After installation it will require installation of multiple **go** tools. Some of them will require a VPN if you are in a restricted access network:

- gocode: `go get -u -v github.com/nsf/gocode`
- godef: `go get -u -v github.com/rogpeppe/godef`
- gogetdoc: `go get -u -v github.com/zmb3/gogetdoc`
- golint: `go get -u -v github.com/golang/lint/golint`
- go-outline: `go get -u -v github.com/lukehoban/go-outline`
- goreturns: `go get -u -v sourcegraph.com/sqs/goreturns`
- gorename: `go get -u -v golang.org/x/tools/cmd/gorename`
- gopkgs: `go get -u -v github.com/tpng/gopkgs`
- go-symbols: `go get -u -v github.com/newhook/go-symbols`
- guru: `go get -u -v golang.org/x/tools/cmd/guru`
- gotests: `go get -u -v github.com/cweill/gotests/...`

With all the tools installed your VS Code will be ready for rock. By default a few features will be enabled:

###### Autocomplete

 Once you download some library you, or even using the standard library, the code will start to display auto-complete options as the code is typed.

###### Auto format

 Go has a very comprehensive, and sometimes hated, code writting rules. There is where `gofmt ` place an important rule. In this Extension the `gofmt` will be automatically executed everytime a file is saved. By default it will: 

- Remove unused imported libraries;
- Spacing code formatting (replacing spaces for tabs when necessary);
- Removing unecessary blank lines;

###### Auto-build and auto-lint

Together with formating the Extension also provides auto-building and linting on save, make it very quick and simple to see all the possible errors directly inside the IDE and simplifying the coding experience.



[golang]: https://golang.org/
[godownload]: https://golang.org/dl/

