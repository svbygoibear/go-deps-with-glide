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

To make code sharable between co-workers or setting up a scalable, automated environment outside of you local machine, you'll have to make use of `vendoring` in Go. This allows your applications to fetch dependencies not only from `$GOPATH/src` but makes a `vendor` folder available inside each project - which allows you to have dependencies inside and specific to the project itself, not just your global workspace.
 
Glide allows you to manage your dependencies in your vendor folder on a project level by having specific versions of your dependencies defined inside of a `glide.yaml` file:
```
package: go-deps-with-glide
import:
- package: github.com/labstack/echo
  version: ^3.2.1
```

There is also a `glide.lock` file which ensures that a project is always using the same version for each dependency specified whenever you execute `glide install` on that project.

## Setting Up

### Get Go-ing
To use this sample, you will need [Go](https://golang.org) installed on your computer. **The steps documented in this project works with version 1.5.0 and up of Go as we make use of `vendoring`.**
Follow the instructions from the [official page](https://golang.org/doc/install). 

After you've completed the installation and ran a quick test, check your go version from terminal:
```
$ go version
```
You'll see something like this printed out:
```
go version go1.8.3 darwin/amd64
```
### Workspace Structure
When getting started with Go, you'll notice that your workspace needs to have a specific structure - just to highlight this again, it is a good idea to keep up this pattern;
```
$HOME
    |_ go
        |_ bin
        |_ pkg
        |_ src
            |_ go-deps-with-glide
```

### Glide-ing Dependencies
#### Getting Glide
To install [Glide](https://github.com/Masterminds/glide) on Mac or Linux, you can use the following in terminal;
```
$ curl https://glide.sh/get | sh
```

If you have [Homebrew](https://brew.sh) installed on Mac OS X, you can also use that;
```
$ brew install glide
```

You can also download a versioned release by going here: https://github.com/Masterminds/glide/releases

And lastly if you've installed `Go`, you can use that to install Glide via terminal;
```
$ go get -u github.com/Masterminds/glide
```
This gets the latest snapshot and is not a release version.

For more information on installation, check out the steps [on their GitHub repo](https://github.com/Masterminds/glide#install).

#### Using Glide

### IDE Specific Settings
#### IntelliJ Idea

## Using Project

## Further Reading
- [Glide](https://glide.sh)
- [Glide GitHub](https://github.com/Masterminds/glide)
- [Creating a Makefile for your Go project](https://vincent.bernat.im/en/blog/2017-makefile-build-golang)
- [Glide Caching](https://github.com/Masterminds/glide/issues/178)
- [Vendoring in Go](https://goenning.net/2017/02/23/packages-vendoring-in-go/)