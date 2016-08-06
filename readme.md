### space-proxy 

Proxy Server for Private Spaces, via either Heroku Button deploy or Heroku Buildpack.

requires: a private space with dns-discovery enabled, *NOTE* dont use the button if you have a non dns-discovery space, it will absolutely not work.

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/heroku/heroku-buildpack-space-proxy)

### buildpack 

this repo is usable as a buildpack. it will add an nginx proxy to your app, available at `space-proxy/bin/space-proxy`.

Add that command as the web process in your Procifle.

Set the `SPACE_PROXY_BASIC_AUTH` in nginx format. e.g. `space:{PLAIN}proxy`

```
heroku config:set SPACE_PROXY_BASIC_AUTH=space:{PLAIN}proxy
```

Optionally set the `SPACE_PROXY_DEFAULT_BACKEND`

```
heroku config:set SPACE_PROXY_DEFAULT_BACKEND=1.service.other-app.app.localspace:8080
```
