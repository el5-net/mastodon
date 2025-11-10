Mastodon fork for [El5](https://el5.net)
===

[![DockerHub](https://img.shields.io/docker/pulls/maisuier/mastodon.svg?logo=docker&color=2496ED)](https://hub.docker.com/r/maisuier/mastodon)
[![Build Universal Image](https://github.com/maisuimiao/mastodon/actions/workflows/docker-build.yml/badge.svg)](https://github.com/maisuimiao/mastodon/actions/workflows/docker-build-main.yml)
[![Build AMD64 Image](https://github.com/maisuimiao/mastodon/actions/workflows/docker-build-amd64.yml/badge.svg)](https://github.com/maisuimiao/mastodon/actions/workflows/docker-build-dev.yml)

## Highlighted Features

- Maximum toot word count increased to 5000
- A bunch of awesome themes.
- The voting options increased to 16

## Specifications

### Version Control
This is a rebase fork of `tootsuite/mastodon`, all local changes are rebased on the top. To pull the latest commits of this repo, use `git reset --hard origin/main` instead of `git pull`. If you are going to develop based on this fork, I strongly recommend you always [cherry-pick](https://git-scm.com/docs/git-cherry-pick) your commits to the `HEAD` of this branch.

### Docker Images
The Docker images are listed [here](https://hub.docker.com/r/maisuier/mastodon/tags).

<table>
    <tr>
        <td>Tag</td>
        <td>Architecture</td>
        <td>Remarks</td>
    </tr>
    <tr>
        <td><code>latest</code></td>
        <td>amd64/arm64</td>
        <td rowspan=3>The latest image build from <code>main</code> branch (<strong>unstable sometimes</strong>).</td>
    </tr>
    <tr>
        <td><code>latest-arm64</code></td>
        <td>arm64</td>
    </tr>
    <tr>
        <td><code>latest-amd64</code></td>
        <td>amd64</td>
    </tr>
    <tr>
        <td><code>sha-*</code></td>
        <td>amd64/arm64</td>
        <td rowspan=3>The image build from commit with the specified SHA (<strong>unstable</strong>).</td>
    </tr>
    <tr>
        <td><code>sha-*-arm64</code></td>
        <td>arm64</td>
    </tr>
    <tr>
        <td><code>sha-*-amd64</code></td>
        <td>amd64</td>
    </tr>
    <tr>
        <td><code>YY.MM.DD</code></td>
        <td>amd64/arm64</td>
        <td rowspan=3>The image build from release. Normally a release was made every time rebase merging upstream code (<strong>stable</strong>).</td>
    </tr>
    <tr>
        <td><code>YY.MM.DD-arm64</code></td>
        <td>arm64</td>
    </tr>
    <tr>
        <td><code>YY.MM.DD-amd64</code></td>
        <td>amd64</td>
    </tr>
</table>

Readme referenced: [littlefox.rest](https://github.com/mashirozx/mastodon)

***
*Follows the original README*
***

<h1><picture>
  <source media="(prefers-color-scheme: dark)" srcset="./lib/assets/wordmark.dark.png?raw=true">
  <source media="(prefers-color-scheme: light)" srcset="./lib/assets/wordmark.light.png?raw=true">
  <img alt="Mastodon" src="./lib/assets/wordmark.light.png?raw=true" height="34">
</picture></h1>
> [!NOTE]
> Want to learn more about Mastodon?
> Click below to find out more in a video.

<p align="center">
  <a style="text-decoration:none" href="https://www.youtube.com/watch?v=IPSbNdBmWKE">
    <img alt="Mastodon hero image" src="https://github.com/user-attachments/assets/ef53f5e9-c0d8-484d-9f53-00efdebb92c3" />
  </a>
</p>

<p align="center">
  <a style="text-decoration:none" href="https://github.com/mastodon/mastodon/releases">
    <img src="https://img.shields.io/github/release/mastodon/mastodon.svg" alt="Release" /></a>
  <a style="text-decoration:none" href="https://github.com/mastodon/mastodon/actions/workflows/test-ruby.yml">
    <img src="https://github.com/mastodon/mastodon/actions/workflows/test-ruby.yml/badge.svg" alt="Ruby Testing" /></a>
  <a style="text-decoration:none" href="https://crowdin.com/project/mastodon">
    <img src="https://d322cqt584bo4o.cloudfront.net/mastodon/localized.svg" alt="Crowdin" /></a>
</p>

Mastodon is a **free, open-source social network server** based on [ActivityPub](https://www.w3.org/TR/activitypub/) where users can follow friends and discover new ones. On Mastodon, users can publish anything they want: links, pictures, text, and video. All Mastodon servers are interoperable as a federated network (users on one server can seamlessly communicate with users from another one, including non-Mastodon software that implements ActivityPub!)

## Navigation

- [Project homepage 🐘](https://joinmastodon.org)
- [Donate to support development 🎁](https://joinmastodon.org/sponsors#donate)
  - [View sponsors](https://joinmastodon.org/sponsors)
- [Blog 📰](https://blog.joinmastodon.org)
- [Documentation 📚](https://docs.joinmastodon.org)
- [Official container image 🚢](https://github.com/mastodon/mastodon/pkgs/container/mastodon)

## Features

<img src="./app/javascript/images/elephant_ui_working.svg?raw=true" align="right" width="30%" />

**Part of the Fediverse. Based on open standards, with no vendor lock-in.** - the network goes beyond just Mastodon; anything that implements ActivityPub is part of a broader social network known as [the Fediverse](https://jointhefediverse.net/). You can follow and interact with users on other servers (including those running different software), and they can follow you back.

**Real-time, chronological timeline updates** - updates of people you're following appear in real-time in the UI.

**Media attachments** - upload and view images and videos attached to the updates. Videos with no audio track are treated like animated GIFs; normal videos loop continuously.

**Safety and moderation tools** - Mastodon includes private posts, locked accounts, phrase filtering, muting, blocking, and many other features, along with a reporting and moderation system.

**OAuth2 and a straightforward REST API** - Mastodon acts as an OAuth2 provider, and third party apps can use the REST and Streaming APIs. This results in a [rich app ecosystem](https://joinmastodon.org/apps) with a variety of choices!

## Deployment

### Tech stack

- [Ruby on Rails](https://github.com/rails/rails) powers the REST API and other web pages.
- [PostgreSQL](https://www.postgresql.org/) is the main database.
- [Redis](https://redis.io/) and [Sidekiq](https://sidekiq.org/) are used for caching and queueing.
- [Node.js](https://nodejs.org/) powers the streaming API.
- [React.js](https://reactjs.org/) and [Redux](https://redux.js.org/) are used for the dynamic parts of the interface.
- [BrowserStack](https://www.browserstack.com/) supports testing on real devices and browsers. (This project is tested with BrowserStack)
- [Chromatic](https://www.chromatic.com/) provides visual regression testing. (This project is tested with Chromatic)

### Requirements

- **Ruby** 3.2+
- **PostgreSQL** 14+
- **Redis** 7.0+
- **Node.js** 20+

This repository includes deployment configurations for **Docker and docker-compose**, as well as for other environments like Heroku and Scalingo. For Helm charts, reference the [mastodon/chart repository](https://github.com/mastodon/chart). A [**standalone** installation guide](https://docs.joinmastodon.org/admin/install/) is available in the main documentation.

## Contributing

Mastodon is **free, open-source software** licensed under **AGPLv3**. We welcome contributions and help from anyone who wants to improve the project.

You should read the overall [CONTRIBUTING](https://github.com/mastodon/.github/blob/main/CONTRIBUTING.md) guide, which covers our development processes.

You should also read and understand the [CODE OF CONDUCT](https://github.com/mastodon/.github/blob/main/CODE_OF_CONDUCT.md) that enables us to maintain a welcoming and inclusive community. Collaboration begins with mutual respect and understanding.

You can learn about setting up a development environment in the [DEVELOPMENT](docs/DEVELOPMENT.md) documentation.

If you would like to help with translations 🌐 you can do so on [Crowdin](https://crowdin.com/project/mastodon).

## LICENSE

Copyright (c) 2016-2025 Eugen Rochko (+ [`mastodon authors`](AUTHORS.md))

Licensed under GNU Affero General Public License as stated in the [LICENSE](LICENSE):

```text
Copyright (c) 2016-2025 Eugen Rochko & other Mastodon contributors

This program is free software: you can redistribute it and/or modify it under
the terms of the GNU Affero General Public License as published by the Free
Software Foundation, either version 3 of the License, or (at your option) any
later version.

This program is distributed in the hope that it will be useful, but WITHOUT
ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS
FOR A PARTICULAR PURPOSE. See the GNU Affero General Public License for more
details.

You should have received a copy of the GNU Affero General Public License along
with this program. If not, see https://www.gnu.org/licenses/
```
