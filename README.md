# Openwhyd.org
[![All Contributors](https://img.shields.io/badge/all_contributors-22-orange.svg?style=flat-square)](#contributors) ![Travis-CI](https://travis-ci.org/openwhyd/openwhyd.svg?branch=master) [![OpenCollective](https://opencollective.com/openwhyd/backers/badge.svg)](#backers) [![OpenCollective](https://opencollective.com/openwhyd/sponsors/badge.svg)](#sponsors) [![frequently asked questions](https://img.shields.io/badge/help-FAQ-orange.svg)](https://github.com/openwhyd/openwhyd/blob/master/docs/FAQ.md) [![Music lover club on Facebook](https://img.shields.io/badge/chat-music%20lover%20club-blue.svg)](https://facebook.com/groups/openwhyd/) [![Like Openwhyd on Facebook](https://img.shields.io/badge/%F0%9F%91%8D-facebook-blue.svg)](https://facebook.com/openwhyd/) [![Follow Openwhyd on Twitter](https://img.shields.io/twitter/follow/open_whyd.svg?style=social&label=Follow)](https://twitter.com/open_whyd)

> Discover, collect and play music from Youtube, Soundcloud, Bandcamp, Deezer and other streaming platforms.

Music libraries like Spotify and Apple Music make it easy to play and collect music that is released officially by music labels.

Openwhyd, on the other hand, allows music lovers to discover, play and collect *any* musical gem that is available on the most popular streaming platforms, including:

- music videos, bootlegs and specific live performances,
- fresh tracks from new and/or local artists,
- DJ sets and rare remixes,
- or any song that can be found and streamed online.

**Free to use at [openwhyd.org](https://openwhyd.org), and [on your iPhone](https://openwhyd.org/iphone).**

## Features

[![Whyd Music Demo Video](./docs/openwhyd-demo-thumb.png)](https://www.youtube.com/watch?v=aZT8VlTV1YY "Whyd Music Demo Video")

Features:

- Playlists: made of tracks from **various sources**: Youtube, Soundcloud, Bandcamp, Deezer...
- Button: Add a track from **any web page**, in a few clicks, using our Google Chrome extension and bookmarklet
- Radio: **Subscribe** to music curators based on your musical taste, and listen to their latest discoveries
- Fame: Get a following by creating awesome playlists, and being featured in the "**Hot Tracks**" ranking
- Search: Add descriptions to your track, to make them **easier to find** when you need them
- Integration: Embed your playlists on your blog or website, so your visitors can listen to it directly.

## Development

### Status of the project

This product is the result of years of iterative development, by the start-up company [Whyd](https://whyd.com). Read [the full story from Whyd to Openwhyd](https://medium.com/openwhyd/music-amongst-other-topics-a4f41657d6d).

Since [its code was generously open-sourced by Whyd](http://eprnews.com/whyd-the-music-streaming-social-network-becomes-openwhyd-and-gives-keys-to-the-community-18067/), [Adrien Joly](https://github.com/adrienjoly) (ex-lead developer at Whyd) has been maintaining it on his spare time (i.e. replying to user feedback on twitter and facebook, maintaing issues based on user feedback, backing up openwhyd's database, updating SSL certificates...), and coordinating [contributors](https://github.com/openwhyd/openwhyd/network/members).

Here's what we have in mind for the future: [The Future of Openwhyd](https://medium.com/openwhyd/the-future-of-openwhyd-9a39e0839ac3).

We welcome contributors, including beginners!

- Latest stats, analytics and demographics: [Openwhyd data report, mid-october 2017](https://infograph.venngage.com/publish/c74df49b-2d2f-48bc-b9cb-5bc1f5908c37) 🔥
- A question / problem? --> Check out [our FAQ](https://github.com/openwhyd/openwhyd/blob/master/docs/FAQ.md)

### Tech stack

- Node.js
- Express-like Web Server
- jQuery
- HTML + CSS
- [Playemjs](https://github.com/adrienjoly/playemjs) for streaming tracks continuously

### Contribute

If you want to contribute, please:

- read the contribution guidelines: [CONTRIBUTING.md](https://github.com/openwhyd/openwhyd/blob/master/CONTRIBUTING.md);
- pick an issue from [our roadmap](https://github.com/openwhyd/openwhyd/projects/1), work on it, then propose a Pull-Request;
- if you need help, [ask us on Slack](https://openwhyd-slack.herokuapp.com/).

Also, be aware that this project has become open-source very recently, so please be kind and constructive about code quality, and about the management of this project.

Thank you for your understanding! ^^

### Setup (simple)

Docker makes it easy and safe to install and start the two servers required for Openwhyd: the MongoDB database server, and the *whydJS* web/application server. All you need is access to the shell (a.k.a. *terminal*), and to have Docker and Git installed on your machine.

1. Install [Docker Client](https://www.docker.com/community-edition) and start it
2. [Install Git](https://www.atlassian.com/git/tutorials/install-git) if you don't have it already
3. Clone openwhyd's repository: `git clone https://github.com/openwhyd/openwhyd.git`, then `cd openwhyd`
4. Build and launch Docker processes: `docker-compose up`
6. Open [http://localhost:8080](http://localhost:8080) in your web browser => you should see Openwhyd's home page! 🎉
7. When you're done, shutdown the Docker processes by pressing the `Ctrl-C` key combination in the shell instance where you had run `docker-compose up` (step 4).

Whenever you want to update your local clone of Openwhyd's repository to the latest version, run `git pull` from the `openwhyd` folder where you had cloned the repository (step 3).

Whenever you want to start the Docker processes after shutting them down (step 7), run `docker-compose up` again from the `openwhyd` folder where you had cloned the repository (step 3).

Whenever you just want to restart Openwhyd while the Docker processes are still running, run `docker-compose restart web` from a shell terminal.

Whenever you want to know what Docker processes are currently running: run `docker-compose ps`.

### Setup (manual)

* Install Node.js, MongoDB, GraphicsMagick or ImageMagick
* Make sure that `make` and `g++` are installed (required for building npm binaries, *I had to do [this](https://github.com/fedwiki/wiki/issues/46) and [this](https://www.digitalocean.com/community/questions/node-gyp-rebuild-fails-on-install)*)
* Make sure that a MongoDB server is running
* Make sure that the necessary environment variables are defined (see below)
* Make sure that the database is initialized (by running `mongo openwhyd_data whydJS/config/initdb.js` and `mongo openwhyd_data whydJS/config/initdb_team.js`)
* Make sure that dependencies are installed (`npm install`)
* If you want notifications to be pushed to your iPhone app, make sure that Apple Push Notification Service (APNS) certificates are copied to `/whydJS/config/apns` with the following filenames: `aps_dev.cert.pem`, `aps_dev.key.pem`, `aps_prod.cert.pem`, `aps_prod.key.pem`, and `Dev_Whyd.mobileprovision`. (you can test them using `test_apns.sh`)

### Usage

* `docker-compose up`, or `npm run run` (for development), or `npm start` (forever daemon)
* Open [http://localhost:8080](http://localhost:8080) (or `WHYD_URL_PREFIX`)
* During development, you may have to restart the server to have your changes taken into account. To restart the Docker container, use `docker-compose restart web`.

### Testing

Run unit tests only:

```bash
npm run test-unit
```

Run all tests, including acceptance tests (webdriver.io-based), from the `whydJS` folder:

```bash
# in a terminal session, start the "whydJS" application server
npm run run-for-tests
# in another terminal session, run the tests
npm test
```

Run all tests against the Docker container:

```bash
npm run test-docker
```

### Environment variables

* `WHYD_GENUINE_SIGNUP_SECRET` (mandatory. a secret key that is used to make sure that sign-ups are legit)
* `WHYD_SESSION_SECRET` (mandatory. a secret key used to sign session cookies)
* `WHYD_DEV_APNS_PASSPHRASE` (mandatory. the passphrase used to de-cypher APNS certificate and key, for iOS push notifications in DEV mode)
* `WHYD_APNS_PASSPHRASE` (mandatory. the passphrase used to de-cypher APNS certificate and key, for iOS push notifications in PRODUCTION mode)
* `WHYD_ADMIN_OBJECTID` (ObjectId of the user that can access to admin endpoints)
* `WHYD_ADMIN_NAME` (Full-text name of the user that can access to admin endpoints)
* `WHYD_ADMIN_EMAIL` (mandatory. Email address of the user that can access to admin endpoints)
* `WHYD_CONTACT_EMAIL` (mandatory. email for users to contact the site's team)
* `WHYD_CRASH_EMAIL` (mandatory when running with forever. email address of the site's administrator)
* `WHYD_URL_PREFIX` (default: `http://localhost:8080`)
* `WHYD_PORT` (default: `8080`)
* `WHYD_DEV` (default: `false`)
* `MONGODB_DATABASE` (example: `openwhyd_data`, or `openwhyd_test`)
* `MONGODB_HOST` (default: `localhost`)
* `MONGODB_PORT` (default: `27017`)
* `MONGODB_USER` (default: none)
* `MONGODB_PASS` (default: none)
* `SENDGRID_API_USER` (mandatory. email address of sendgrid account to be used for sending emails)
* `SENDGRID_API_KEY` (mandatory. key / password of sendgrid account)
* `SENDGRID_API_FROM_EMAIL` (mandatory. email address of email sender)
* `SENDGRID_API_FROM_NAME` (mandatory. name of email sender)
* `LAST_FM_API_KEY` (mandatory. for lastfm scrobbling)
* `LAST_FM_API_SECRET` (mandatory. for lastfm scrobbling)
* `ALGOLIA_APP_ID` (mandatory. for search index)
* `ALGOLIA_API_KEY` (mandatory. for search index)

## Support Openwhyd

### Backers

Support us with a monthly donation and help us continue our activities. [[Become a backer](https://opencollective.com/openwhyd#backer)]

<a href="https://opencollective.com/openwhyd/backer/0/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/0/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/1/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/1/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/2/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/2/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/3/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/3/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/4/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/4/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/5/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/5/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/6/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/6/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/7/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/7/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/8/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/8/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/9/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/9/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/10/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/10/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/11/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/11/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/12/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/12/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/13/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/13/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/14/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/14/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/15/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/15/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/16/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/16/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/17/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/17/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/18/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/18/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/19/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/19/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/20/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/20/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/21/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/21/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/22/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/22/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/23/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/23/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/24/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/24/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/25/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/25/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/26/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/26/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/27/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/27/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/28/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/28/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/backer/29/website" target="_blank"><img src="https://opencollective.com/openwhyd/backer/29/avatar.svg"></a>

### Sponsors
Become a sponsor and get your logo on our README on Github with a link to your site. [[Become a sponsor](https://opencollective.com/openwhyd#sponsor)]

<a href="https://opencollective.com/openwhyd/sponsor/0/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/0/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/1/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/1/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/2/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/2/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/3/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/3/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/4/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/4/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/5/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/5/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/6/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/6/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/7/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/7/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/8/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/8/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/9/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/9/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/10/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/10/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/11/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/11/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/12/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/12/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/13/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/13/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/14/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/14/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/15/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/15/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/16/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/16/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/17/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/17/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/18/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/18/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/19/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/19/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/20/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/20/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/21/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/21/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/22/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/22/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/23/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/23/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/24/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/24/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/25/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/25/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/26/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/26/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/27/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/27/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/28/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/28/avatar.svg"></a>
<a href="https://opencollective.com/openwhyd/sponsor/29/website" target="_blank"><img src="https://opencollective.com/openwhyd/sponsor/29/avatar.svg"></a>

### Contributors

Thanks goes to these wonderful people ([emoji key](https://github.com/kentcdodds/all-contributors#emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
| [<img src="https://d1qb2nb5cznatu.cloudfront.net/users/56004-large?1405472476" width="98px;"/><br /><sub>Gilles Poupardin</sub>](https://twitter.com/gillespoupardin)<br />[📢](#talk-undefined "Talks") [🤔](#ideas-undefined "Ideas, Planning, & Feedback") [💵](#financial-undefined "Financial") | [<img src="https://avatars0.githubusercontent.com/u/764618?v=4" width="98px;"/><br /><sub>Jie Meng-Gérard</sub>](https://github.com/jiem)<br />[💻](https://github.com/openwhyd/openwhyd/commits?author=jiem "Code") [🚇](#infra-jiem "Infrastructure (Hosting, Build-Tools, etc)") [💵](#financial-jiem "Financial") | [<img src="https://avatars3.githubusercontent.com/u/531781?v=4" width="98px;"/><br /><sub>Adrien Joly</sub>](https://adrienjoly.com/now)<br />[💻](https://github.com/openwhyd/openwhyd/commits?author=adrienjoly "Code") [📖](https://github.com/openwhyd/openwhyd/commits?author=adrienjoly "Documentation") [🐛](https://github.com/openwhyd/openwhyd/issues?q=author%3Aadrienjoly "Bug reports") [👀](#review-adrienjoly "Reviewed Pull Requests") [⚠️](https://github.com/openwhyd/openwhyd/commits?author=adrienjoly "Tests") [📢](#talk-adrienjoly "Talks") [💬](#question-adrienjoly "Answering Questions") | [<img src="https://avatars3.githubusercontent.com/u/910269?v=4" width="98px;"/><br /><sub>loickm</sub>](https://github.com/loickm)<br />[🎨](#design-loickm "Design") [💻](https://github.com/openwhyd/openwhyd/commits?author=loickm "Code") | [<img src="https://pbs.twimg.com/profile_images/708991890046246912/TrUSqpzo_400x400.jpg" width="98px;"/><br /><sub>Tony Hymes</sub>](https://twitter.com/tonyhymes)<br />[📢](#talk-undefined "Talks") [📝](#blog-undefined "Blogposts") [📋](#eventOrganizing-undefined "Event Organizing") [💬](#question-undefined "Answering Questions") | [<img src="https://avatars1.githubusercontent.com/u/603808?v=4" width="98px;"/><br /><sub>Damien Romito</sub>](http://www.choses.fr)<br />[💻](https://github.com/openwhyd/openwhyd/commits?author=damienromito "Code") [🔌](#plugin-damienromito "Plugin/utility libraries") | [<img src="https://s-media-cache-ak0.pinimg.com/avatars/alifecurated_1455886409_280.jpg" width="98px;"/><br /><sub>Claire Marion</sub>](https://github.com/cmdcmdcmd)<br />[🎨](#design-cmdcmdcmd "Design") [📝](#blog-cmdcmdcmd "Blogposts") [🤔](#ideas-cmdcmdcmd "Ideas, Planning, & Feedback") |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| [<img src="https://avatars1.githubusercontent.com/u/1169844?v=4" width="98px;"/><br /><sub>Julien Tanay</sub>](http://julientanay.com)<br />[🚇](#infra-Djiit "Infrastructure (Hosting, Build-Tools, etc)") [🔧](#tool-Djiit "Tools") [💻](https://github.com/openwhyd/openwhyd/commits?author=Djiit "Code") | [<img src="https://avatars0.githubusercontent.com/u/243268?v=4" width="98px;"/><br /><sub>Adrien Candiotti</sub>](https://github.com/SkinyMonkey)<br />[🚇](#infra-SkinyMonkey "Infrastructure (Hosting, Build-Tools, etc)") [💻](https://github.com/openwhyd/openwhyd/commits?author=SkinyMonkey "Code") [🤔](#ideas-SkinyMonkey "Ideas, Planning, & Feedback") | [<img src="https://media.licdn.com/media/p/3/000/272/357/1d22cf8.jpg" width="98px;"/><br /><sub>Constance Betinyani</sub>](https://www.linkedin.com/in/constance-betinyani-30b8b95a/)<br />[📝](#blog-undefined "Blogposts") [🔍](#fundingFinding-undefined "Funding Finding") | [<img src="https://d1qb2nb5cznatu.cloudfront.net/users/28089-large?1489180378" width="98px;"/><br /><sub>Alberto Fantappie</sub>](https://angel.co/alberto-fantappie)<br />[🔍](#fundingFinding-undefined "Funding Finding") [📋](#eventOrganizing-undefined "Event Organizing") | [<img src="https://media.licdn.com/media/AAEAAQAAAAAAAAe9AAAAJDBjMTM3ZjI2LTkyM2MtNGFiMS04ZDJhLTVkYmYxMjdhNWFiZA.jpg" width="98px;"/><br /><sub>Mathilde Vercelletto</sub>](https://www.linkedin.com/in/mathildevercelletto/)<br />[📖](https://github.com/openwhyd/openwhyd/commits?author= "Documentation") [💵](#financial-undefined "Financial") | [<img src="https://media.licdn.com/media/p/2/005/05c/069/29be303.jpg" width="98px;"/><br /><sub>Henri Lieutaud</sub>](https://github.com/ElBurritoPodrido)<br />[🤔](#ideas-ElBurritoPodrido "Ideas, Planning, & Feedback") | [<img src="https://avatars3.githubusercontent.com/u/8008820?v=4" width="98px;"/><br /><sub>François Burra</sub>](https://github.com/FrancoisBurra)<br />[🤔](#ideas-FrancoisBurra "Ideas, Planning, & Feedback") |
| [<img src="https://avatars0.githubusercontent.com/u/3294460?v=4" width="98px;"/><br /><sub>Grey Vugrin</sub>](http://greyvugrin@github.io)<br />[💻](https://github.com/openwhyd/openwhyd/commits?author=greyvugrin "Code") [🐛](https://github.com/openwhyd/openwhyd/issues?q=author%3Agreyvugrin "Bug reports") [🔧](#tool-greyvugrin "Tools") | [<img src="https://avatars3.githubusercontent.com/u/5300654?v=4" width="98px;"/><br /><sub>Marin le Maignan</sub>](https://github.com/Marinlemaignan)<br />[💻](https://github.com/openwhyd/openwhyd/commits?author=Marinlemaignan "Code") [🐛](https://github.com/openwhyd/openwhyd/issues?q=author%3AMarinlemaignan "Bug reports") [🤔](#ideas-Marinlemaignan "Ideas, Planning, & Feedback") | [<img src="https://pbs.twimg.com/profile_images/760481572923531264/4th1HNIe.jpg" width="98px;"/><br /><sub>Nicolas Leger</sub>](https://github.com/nicolasleger)<br />[🚇](#infra-nicolasleger "Infrastructure (Hosting, Build-Tools, etc)") [💻](https://github.com/openwhyd/openwhyd/commits?author=nicolasleger "Code") | [<img src="https://avatars2.githubusercontent.com/u/1911478?v=4" width="98px;"/><br /><sub>Serdar Sever</sub>](https://znk.github.io)<br />[💻](https://github.com/openwhyd/openwhyd/commits?author=znk "Code") [🐛](https://github.com/openwhyd/openwhyd/issues?q=author%3Aznk "Bug reports") | [<img src="https://avatars2.githubusercontent.com/u/19236802?v=4" width="98px;"/><br /><sub>Stanislas Châble</sub>](https://www.linkedin.com/in/stanislas-chable/)<br />[💻](https://github.com/openwhyd/openwhyd/commits?author=Selbahc "Code") [🐛](https://github.com/openwhyd/openwhyd/issues?q=author%3ASelbahc "Bug reports") | [<img src="https://avatars2.githubusercontent.com/u/3671070?v=4" width="98px;"/><br /><sub>Pia Mancini</sub>](http://piamancini.com)<br />[🔍](#fundingFinding-piamancini "Funding Finding") | [<img src="https://avatars2.githubusercontent.com/u/265349?v=4" width="98px;"/><br /><sub>Maurice Svay</sub>](http://svay.com/)<br />[💻](https://github.com/openwhyd/openwhyd/commits?author=mauricesvay "Code") [🐛](https://github.com/openwhyd/openwhyd/issues?q=author%3Amauricesvay "Bug reports") [🎨](#design-mauricesvay "Design") |
| [<img src="https://avatars3.githubusercontent.com/u/526294?v=4" width="98px;"/><br /><sub>Jénaïc Cambré</sub>](http://www.kadiks.net)<br />[💬](#question-kadiks "Answering Questions") |
<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/kentcdodds/all-contributors) specification. Contributions of any kind welcome!
