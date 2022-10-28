# Untitled

Untitled is Bryan's starter theme for Ghost. The idea is to have a blank (but fully-functional) slate for new Ghost sites.

I always get frustrated dealing with the front-end defaults that live inside Ghost's 1st party themes. I always find myself stripping out CSS classes and restructuring markup and getting really frustrated w/ the build scripts.

So here it is, finally.

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

## todos
- [x] Ghost membership - gated pages, etc
- [x] Ghost comments - moderation not working? showing sign in banner when signed in
- [x] Ghost search
- [x] navigation
- [ ] styling support for ghost editor cards (?)
- [x] pages? (tags, author, etc.)
- [ ] Conditional display of desc, bio, comments on templates
- [ ] Edit billing redirects. They go back to /accounts right now, but maybe I should add a url param so I can show success and cancel messaging)
- [ ] indication for members only and paid post types (index and on posts)
- [ ] sign in / sign up messaging (success, error, etc)
- [ ] clarify messaging around membership actions (redirects to stripe, email login links, etc)
- [ ] sign in / sign up form formatting (add name field to sign up form)
- [ ] distinguish account creation from purchasing a subscription
- [ ] fix empty comment counts
- [ ] conditional display logic on sign in page?

I'm not sure why I'm fighting against the logic for displaying the paid tiers alongside the free one. In all reality, there's only going to be one paid newsletter, and even if there are multiples those become "products" that just lead into stripe. I think the move is to pull the free tier out of the product page. This is also what Craig mod does: separate signup form and then he has buttons that kick the user into memberful to complete checkout.

this means I need to think of it as a "subscription center" and a product page.

also think this is getting to the point where I shouldn't worry about solving all these problems for my boilerplate right now. like the "newsletters" feature works, BUT it requires portal to manage the opt-in. I'm thinking I just leave my custom stuff for now. It's workable if I only have one newsletter, and if i require more then I just settle for Portal for the time being.

base requirement is a single membership (monthly & yearly) and a single newsletter for sending updates. If I need additional paid products, I think I have that covered. But if I need to have a second newsletter, say for a pop-up thing, then I have to use portal. I think until they provide the ability to interact with {{newsletters}} (that's hypothetical) I probably should stick with portal.