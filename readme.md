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
The big advantage of this is that it allows you to commit your project **without** the vendor folder and its contents as the specific versions can be found again using Glide to install the dependencies as specified in the `glide.yaml` and `glide.lock` files.

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
When getting started with Go, you'll notice that your workspace needs to have a specific structure - just to highlight this again, it is a good idea to keep up this pattern:
```
$HOME
    |_ go
        |_ bin
        |_ pkg
        |_ src
            |_ go-deps-with-glide
```
For more on workspaces, you can look at the [golang guide](https://golang.org/doc/code.html#Workspaces).

### Glide-ing Dependencies
#### Getting Glide
To install [Glide](https://github.com/Masterminds/glide) on Mac or Linux, you can use the following in terminal:
```
$ curl https://glide.sh/get | sh
```

If you have [Homebrew](https://brew.sh) installed on Mac OS X, you can also use that:
```
$ brew install glide
```

You can also download a versioned release by [checking out the release page](https://github.com/Masterminds/glide/releases).

And lastly if you've installed `Go`, you can use that to install Glide via terminal;
```
$ go get -u github.com/Masterminds/glide
```
This gets the latest snapshot and is not a release version.

For more information on installation, check out the steps [on their GitHub repo](https://github.com/Masterminds/glide#install).

#### Using Glide
To read more about this, you can also reference the [Glide Documentation](https://github.com/Masterminds/glide#usage).

If you're starting up a new project (this step should be excluded from this sample project) you start with creating a new Glide workspace with the following command in terminal:
```
$HOME/go/src/go-deps-with-glide glide create # You can also use glide init
```

For this project, you'll have to install all the dependencies that's been listed in the `glide.yaml` and `glide.lock` files:
```
$HOME/go/src/go-deps-with-glide glide install 
```
You'll notice that this creates a `vendor` folder inside of your project which contains all the dependencies that you'll be using.

If you get a `[ERROR]	$GOPATH is not set.` message, it could be that you need to set your go path in your terminal session before installing:
```
$HOME/go/src/go-deps-with-glide export GOPATH=$HOME/git/go/
```

#### Updating Dependencies
When using `update` opposed to `install` it is very important to take note that running an update would actually fetch the latest versions of your dependencies/specified dependency and update your `glide.yaml` and `glide.lock` files.
I would suggest only using `update` on a specific dependency at a time if you're working on a current project as this could lead to potential breaking changes.

To update your dependencies, you simply run:
```
$HOME/go/src/go-deps-with-glide glide update
```
Or for short:
```
$HOME/go/src/go-deps-with-glide glide up
```

For more information on Glide's update feature check out the [Glide documentation](https://github.com/Masterminds/glide#glide-update-aliased-to-up).

### IDE Specific Settings
#### IntelliJ Idea
All explanations up until this point has been done with terminal in mind. It is possible to set up this project in IntelliJ as well. 
First thing is to download and install the go-lang-idea-plugin:
![screenshot](https://raw.githubusercontent.com/svbygoibear/go-deps-with-glide/master/img/go-lang-plugin.png)
Follow the steps outlined by the [go-lang-idea-plugin](https://github.com/go-lang-plugin-org/go-lang-idea-plugin/wiki/Documentation#setting-up-the-go-sdk).

## Using Project
After cloning this repository, you'll need to make sure that:
- You have the correct version of Go installed.
- You have your workspace set up.
- You have Glide installed.
- You've installed all your dependencies using Glide.

The next step is to see if your project builds. One of the upsides of using `Glide` is that you're able to use it with `Go`, thus to build your project you can just run `go build` as you normally would in terminal:
```
$HOME/go/src/go-deps-with-glide go build
```

You can also run your Go project as you normally would:
```
$HOME/go/src/go-deps-with-glide go run main.go
```

## Further Reading
- [Glide](https://glide.sh)
- [Glide GitHub](https://github.com/Masterminds/glide)
- [Creating a Makefile for your Go project](https://vincent.bernat.im/en/blog/2017-makefile-build-golang)
- [Glide Caching](https://github.com/Masterminds/glide/issues/178)
- [Vendoring in Go](https://goenning.net/2017/02/23/packages-vendoring-in-go/)
- [Glide yaml](https://github.com/Masterminds/glide#glideyaml)