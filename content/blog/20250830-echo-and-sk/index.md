+++
title = "Go Echo + Sveltekit is a dream team"
date = "2025-08-30T10:41:12-04:00"
description = "Using two nice pieces of technology to make some bullshit."
tags = ["education","zestiness","coding"]
+++

I spent half my morning trying to get a multi-page application using [Sveltekit](https://svelte.dev/docs/kit/introduction) to play nicely with a backend server written in [Go](https://go.dev) using the [Echo routing library](https://echo.labstack.com). Thes instructions probably work for other setups as well. So here goes.

My [naive but more attractive younger self](../blurt-have-i-become) was an idiot. He wanted to build an app that would use a Go backend and websockets to provide data to a Sveltekit frontend. The site was very simple and could easily be prerendered rather than being rendered on the fly. As it was he had the backend running on one port, and the Sveltekit application running on another node server/port. What a dumbass! This required a bunch of work and monitoring because if either of them crashed, neither worked. The code here will allow the whole thing to be compiled to a single excutable which will make deploying so much easier.

The downside is that you can't have any `+*.server.ts/js` files in your Sveltekit project. This should be okay because you can just outsource this to your Go application instead.

This is assuming you've got **Go 1.25+** installed and **(p)npm up to date** and some comfort with command lines and IDEs (or VSCode if you don't know what that is).

I'm using `gosk` for the project files, Go + SvelteKit. Short and sweet and I'll never remember why in a month. Perfect.

## Go backend and Echo routing

Alright so fire up a new project directory and initiate a new Go module:
```bash
mkdir gosk && cd gosk
go mod init example.com/gosk
```

Hey look at us we've got it going on. This will create a couple of files in the new directory.

Let's install all the Go libraries we need for this little project:
```bash 
go get github.com/labstack/echo/v4 github.com/labstack/echo/v4/middleware
```

We'll write some Go code now. Open your favourite code editor and create a new file, `main.go` and put this in it:
```go
package main

import (
    "embed"
    "log"
    "net/http"

	"github.com/labstack/echo/v4"
   	"github.com/labstack/echo/v4/middleware"
)

//go:embed frontend/build/*
var webAssets embed.FS

func main() {
    app := echo.New()

	app.Use(middleware.StaticWithConfig(middleware.StaticConfig{
		Root:       "frontend/build",
		Filesystem: http.FS(webAssets),
	}))
	
	app.GET("api/users", func(c echo.Context) error {
		return c.String(http.StatusOK, "users")
	})

	log.Fatal(app.Start(":3320"))
}
```

Simple! This will start an Echo server at port 3320, will serve any routes it can find normally and anything else will get sent into the `frontend/build` directory for Sveltekit to deal with. By using the `//go:embed` directive, we can bundle the Sveltekit app into the Go executable when we compile it. This means that we only need to worry about a single file rather than having to make sure that our `frontend/build` folder is available at runtime which makes the whole thing very portable. Go is great sometimes.

If you're in an IDE you'll be getting an error about the embed code not having any matching files, so we can't run it yet. Sveltekit will take care of this for us.


## Sveltekit Frontend

If you have npm installed, you should be able to run the following commands to create a new Sveltekit app from scratch. Check their website if it doesn't work since I'm going to be super lazy and never update this. Sorry.
```bash
npx sv create frontend
```
This will start an installation script that allows you to choose various options. Do whatever works for you, I install the Sveltekit minimal template and use Typescript but this is all up to you. Just don't select the library template. Be sure to include the `sveltekit-adapter` and be sure to choose `adapter-static` when it asks.

Once the setup is complete, run the steps as instructed:
```bash
cd frontend
npm run dev --open
```
The `--open` flag will open a browser to the correct address, feel free to leave it out. So now if you open a browser tab to `http://localhost:5173` you should see your new Sveltekit project. Easy!

Now we need to make a few tweaks to the Sveltekit configuration to allow us to serve this project from our Go backend.

## Configuration tweaks for Sveltekit

Create a new file `gosk/frontend/src/routes/+layout.ts` and add the following lines:
```typescript
export const prerender = true;
export const trailingSlash = 'always';
```
This will tell the Sveltekit compiler to prerender all of the pages in the application since it is in the root-level `+layout.ts` file. The `trailingSlash` needs to be added for Go to recognize paths correctly.

Now we can build the project to the `build` folder by using the command `npm build`. It should give some lines of output and tell you that it wrote the site to "..build". That's it we're done!

## Final product

Navigate back to the project root `gosk` directory. The warning that was there initially should be gone now since there should be files in the `frontend/build` directory. If it is finicky just delete the `*` in the embed line and re-add it and the warning should clear. If it doesn't, check in the `frontend/build` directory to make sure there are files and if not, troubleshoot.

Run the Go application using:
```bash
go run main.go
```

Once the application builds, open a browser and point it at `http://localhost:3320`. You should see your Sveltekit application! If you go again to `http://localhost:3320/api/users`, you should still see the "users" text.

Pat yourself on the back and go for a bike ride. The world is yours.

