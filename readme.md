<h1 align="center">
  <a href="https://raw.githubusercontent.com/svbygoibear/go-deps-with-glide/master/img/go_glide.png"><img src="https://raw.githubusercontent.com/svbygoibear/go-deps-with-glide/master/img/go_glide.png" alt="go-deps-with-glide" width="100"></a>
  <br>
  go-deps-with-glide
  <br>
</h1>

<h4 align="center">A mash-up on using glide with golang in a sample application.</h4>
<br>
<p align="center">
    <img src="https://raw.githubusercontent.com/svbygoibear/go-deps-with-glide/master/img/go_glide.gif" alt="go-deps-with-glide">
</p>
<br>

## Introduction
Wondering how to get started with dependency management using Glide with Go? No sample application to start with and to compare? Well this repo should get you up and running on how to set up Glide to manage your Go dependencies.

## Why use Glide?
For dependencies, instead of relying on a dependency registry, Go relies on public URLs which hosts some files using VCS systems.
Traditionally all packages are imported by specifying a full path which starts from the configured `$GOPATH/src` (unless it is the standard library which uses `$GOROOT/src`) - and importing new packages for use involved getting it using Go in terminal:
```
$ go get github.com/labstack/echo
```
This in turn downloads the source code into `$GOPATH/src/github.com/labstack/echo` which enables you to use it as an import `github.com/labstack/echo`

## Setting Up

### Get Go-ing
To use this sample, you will need [Go](https://golang.org) installed on your computer. **The steps documented in this project works with version 1.6.0 and up of Go.**
Follow the instructions from the [official page](https://golang.org/doc/install). 

After you've completed the installation and ran a quick test, check your go version from command line:
```
$ go version
```
You'll see something like this printed out - remember to use go1.6.0 or higher:
```
go version go1.8.3 darwin/amd64
```
### Workspace Structure


### Glide-ing Dependencies

### IDE Specific Settings
#### IntelliJ Idea

## Using Project

## Further Reading
- [Glide](https://glide.sh)
- [Glide GitHub](https://github.com/Masterminds/glide)
- [Creating a Makefile for your Go project](https://vincent.bernat.im/en/blog/2017-makefile-build-golang)
- [Glide Caching](https://github.com/Masterminds/glide/issues/178)