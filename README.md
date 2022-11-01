# Verso

Verso is the Ghost theme for bryanking.blog. In printing, versō means [*the wrong side of the page*](https://en.wikipedia.org/wiki/Recto_and_verso), and that describes my blog.

This repo was created using my [Ghost boilerplate, called Untitled](https://github.com/boldlybryan/untitled). Should you invent any useful new features in this theme, please consider copying them back into the template. Otherwise, some notes on local setup can be found below.

## Setup
Contrary to my belief, nothing actually needs to be built or scripted in order for a Ghost theme to get picked up by the theme admin. As long as a theme lives in the right place ```content/themes```, ghost just needs to be restarted and then you can activate the theme.

In this Untitled's case, you just need to clone this repo in ```content/themes``` and then run the (to be created) build scripts that manage dependencies the way I like.

## Configuration
There are a couple of modifications to make to ```config.development.json```:
1. Set up Mailgun (required for using the membership features in development environment)
```
"mail": {
    "transport": "SMTP",
    "options": {
        "service": "Mailgun",
        "auth": {
        "user": "postmaster@sandbox132de304f20c4bafad5a2208793bacae.mailgun.org",
        "pass": "fdf18a52b5fd704d5bab90b4a62417a1-8845d1b1-8e4f9a83"
        }
    }
}
```
2. Turn off search (if you don't want to load the script), adding this block to config:
```
"sodoSearch": {
    "url": false
},
  ```

## Memberships
This theme uses it's own pages instead of Ghost Portal for sign in, sign up, and account management. The template files can be found in ```/members```, and you'll need to upload ```routes.yaml``` inside Ghost, under the ```Advanced > Labs``` settings page. Official docs: [https://ghost.org/docs/themes/members/].

Additionally, you should turn on Stripe's test mode. It can be activated by going into the Portal settings and clicking ```connect to stripe``` under signup options. this will redirect you to stripe, and when you're there you just need to skip the signup flow to connect test mode. Then, you can add a complimentary subscription to a test user account to simulate what a paying customer will see.

## FUNHOUSE

List of ideas
* Spotify now playist