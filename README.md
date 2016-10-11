# Github.js

[![Downloads per month](https://img.shields.io/npm/dm/github-api.svg?maxAge=2592000)][npm-package]
[![Latest version](https://img.shields.io/npm/v/github-api.svg?maxAge=3600)][npm-package]
[![Gitter](https://img.shields.io/gitter/room/michael/github.js.svg?maxAge=2592000)][gitter]
[![Travis](https://img.shields.io/travis/michael/github.svg?maxAge=60)][travis-ci]
<!-- [![Codecov](https://img.shields.io/codecov/c/github/michael/github.svg?maxAge=2592000)][codecov] -->

Github.js provides a minimal higher-level wrapper around Github's API. It was concieved in the context of
[Prose][prose], a content editor for GitHub.

## [Read the docs][docs]

## Installation
Github.js is available from `npm` or [unpkg][unpkg].

```shell
npm install github-api
```

```html
<!-- just github-api source (5.3kb) -->
<script src="https://unpkg.com/github-api/dist/GitHub.min.js"></script>

<!-- standalone (20.3kb) -->
<script src="https://unpkg.com/github-api/dist/GitHub.bundle.min.js"></script>
```

## Compatibility
Github.js is tested on Node:
* 6.x
* 5.x
* 4.x
* 0.12

## GitHub Tools

The team behind Github.js has created a whole organization, called [GitHub Tools](https://github.com/github-tools),
dedicated to GitHub and its API. In the near future this repository could be moved under the GitHub Tools organization
as well. In the meantime, we recommend you to take a look at other projects of the organization.

## Samples

```javascript
/*
   Data can be retrieved from the API either using callbacks (as in versions < 1.0)
   or using a new promise-based API. For now the promise-based API just returns the
   raw HTTP request promise; this might change in the next version.
 */
import GitHub from 'github-api';

// unauthenticated client
const gh = new GitHub();
let gist = gh.getGist(); // not a gist yet
gist.create({
   public: true,
   description: 'My first gist',
   files: {
      "file1.txt": {
         content: "Aren't gists great!"
      }
   }
}).then(function({data}) {
   // Promises!
   let gistJson = data;
   gist.read(function(err, gist, xhr) {
      // if no error occurred then err == null

      // gistJson === httpResponse.data

      // xhr === httpResponse
   });
});
```

```javascript
import GitHub from 'github-api';

// basic auth
const gh = new GitHub({
   username: 'FOO',
   password: 'NotFoo'
});

const me = gh.getUser();
me.listNotifications(function(err, notifications) {
   // do some stuff
});

const clayreimann = gh.getUser('clayreimann');
clayreimann.listStarredRepos()
   .then(function({data: reposJson}) {
      // do stuff with reposJson
   });
```

```javascript
var GitHub = require('github-api');

// token auth
var gh = new GitHub({
   token: 'MY_OAUTH_TOKEN'
});

var yahoo = gh.getOrganization('yahoo');
yahoo.listRepos(function(err, repos) {
   // look at all the repos!
})
```

<<<<<<< HEAD
To read all the issues of a given repository

```js
issues.list(options, function(err, issues) {});
```

## Search API

```js
var search = github.getSearch(query);
```

### Search repositories

Suppose you want to search for popular Tetris repositories written in Assembly. Your query might look like this:

```js
var search = github.getSearch("tetris+language:assembly&sort=stars&order=desc");
search.repositories(options, function (err, repositories) {});
```

### Search code

Suppose you want to find the definition of the addClass function inside jQuery. Your query would look something like this:

```js
var search = github.getSearch("addClass+in:file+language:js+repo:jquery/jquery");
search.code(options, function (err, codes) {});
```

### Search issues

Let’s say you want to find the oldest unresolved Python bugs on Windows. Your query might look something like this:

```js
var search = github.getSearch("windows+label:bug+language:python+state:open&sort=created&order=asc");
search.issues(options, function (err, issues) {});
```

### Search users

Imagine you’re looking for a list of popular users. You might try out this query:

```js
var search = github.getSearch("tom+repos:%3E42+followers:%3E1000");
search.users(options, function (err, users) {});
```

Here, we’re looking at users with the name Tom. We’re only interested in those with more than 42 repositories, and only if they have over 1,000 followers.

##Setup

Github.js has the following dependency:

- btoa (included in modern browsers, an npm module is included in package.json for node)


## Compatibility

[![browser support](https://ci.testling.com/darvin/github.png)](https://ci.testling.com/darvin/github)

## Change Log

### 0.10.X

Create and delete repositories
Repos - getCommit

### 0.9.X

Paging (introduced at tail end of 0.8.X, note: different callbacks for success & errors now)

### 0.8.X

Fixes and tweaks, simpler auth, CI tests, node.js support, Raw+JSON, UTF8, plus:
Users - follow, unfollow, get info, notifications
Gists - create
Issues - get
Repos - createRepo, deleteRepo, createBranch, star, unstar, isStarred, getCommits, listTags, listPulls, getPull, compare
Hooks - listHooks, getHook, createHook, editHook, deleteHook

### 0.7.X

Switched to a native `request` implementation (thanks @mattpass). Adds support for GitHub gists, forks and pull requests.

### 0.6.X

Adds support for organizations and fixes an encoding issue.

### 0.5.X

Smart caching of latest commit sha.

### 0.4.X

Added support for [OAuth](http://developer.github.com/v3/oauth/).

### 0.3.X

Support for Moving and removing files.

### 0.2.X

Consider commit messages.

### 0.1.X

Initial version.
=======
[codecov]: https://codecov.io/github/michael/github?branch=master
[docs]: http://michael.github.io/github/
[gitter]: https://gitter.im/michael/github
[npm-package]: https://www.npmjs.com/package/github-api/
[unpkg]: https://unpkg.com/github-api/
[prose]: http://prose.io
[travis-ci]: https://travis-ci.org/michael/github
[xhr-link]: http://blogs.msdn.com/b/ieinternals/archive/2010/05/13/xdomainrequest-restrictions-limitations-and-workarounds.aspx
>>>>>>> refs/remotes/michael/master
