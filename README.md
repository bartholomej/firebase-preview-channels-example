# Firebase Preview Channels Starter

> Example/Starter app for [Firebase Preview Channels](https://firebase.googleblog.com/2020/10/preview-channels-firebase-hosting.html) with Angular 10 Universal and Github Actions CI/CD for autodeploy

## What is inside?

- Firebase multihosting
- Firebase Preview Channels
- Angular 10
- Angular Universal (SSR)
- [Github Actions](https://github.com/FirebaseExtended/action-hosting-deploy) for CI/CD deploy
- Typescript everywhere
- Yarn everywhere

## How it works?

### Deploy to Preview Channel on pull requests

If you create _pull request_ the action creates a new preview channel automatically.

Preview channel url format: `https://<site-name>--<channel-id>-<random-hash>.web.app`

### Deploy to your live channel on merge

If you merge pull request into `master` branch you will see your changes in production.

## Instructions

> How I did this example?
> Easily! See this manual... Commit by commit.

### Prerequisities

- Firebase tools
- Angular CLI
- Google Cloud Account

### Step by step...

#### 1. Create Angular App ([2c40b86])

> Automatically (no manual intervention in this commit)

```shell
ng new previewchannels-app
```

#### 2. Init Firebase ([65bc32a])

> Automatically (no manual intervention in this commit)

```shell
firebase init
```

#### 3. Cache `node_modules` ([eecc9d3])

> Cache node_ modules + ivy NGCC builds for faster installation and faster Angular build
>
> Manually!!

_see commit diff [eecc9d3] for more details_

#### 4. Add Angular Universal ([be4bffe])

> Automatically (no manual intervention in this commit)

```shell
ng add @nguniversal/express-engine
```

#### 5. Init Firebase function for Angular Universal ([a8c9f43])

> Automatically (no manual intervention in this commit)

```shell
firebase init functions
```

#### 6. Config Firebase multihosting + SSR deploy ([266d1e3])

> Manually!!

_see commit diff [266d1e3] for more details_

#### 7. Use Yarn everywhere ([5fbfb17])

> Manually!!

_see commit diff [5fbfb17] for more details_

## How can you try?

1. Fork this repository
2. Make some changes
3. Make pull request back to this repository
4. See what happens -> Your Firebase preview channel will be created and deployed...

I welcome you to customize this according to your needs ;)

## Other CI/CD configuration

### Bitbucket Pipelines

```yaml
pull-requests:
  '**':
    - step:
        script:
          - export CHANNEL=$(echo $BITBUCKET_BRANCH | sed -e 's/\//-/g') # Remove slash for Firebase Channel name
          - yarn
          - yarn build
          - yarn firebase hosting:channel:deploy ${CHANNEL} --project project-name --json --token "$FIREBASE_TOKEN"
```

## Donation

If this project have helped you save time please consider [making a donation](https://github.com/sponsors/bartholomej) for some 🍺 or 🍵 ;)

## License

Copyright &copy; 2020 [Lukas Bartak](http://bartweb.cz)

Proudly powered by nature 🗻, wind 💨, tea 🍵 and beer 🍺 ;)

All contents are licensed under the [MIT license].

[MIT license]: LICENSE
[2c40b86]: https://github.com/bartholomej/firebase-preview-channels-example/commit/2c40b86a5ffe7421c9f650bc83dc5f239adbd198

[65bc32a]: https://github.com/bartholomej/firebase-preview-channels-example/commit/65bc32a

[eecc9d3]: https://github.com/bartholomej/firebase-preview-channels-example/commit/eecc9d3

[be4bffe]: https://github.com/bartholomej/firebase-preview-channels-example/commit/be4bffe

[a8c9f43]: https://github.com/bartholomej/firebase-preview-channels-example/commit/a8c9f43

[266d1e3]: https://github.com/bartholomej/firebase-preview-channels-example/commit/266d1e3

[5fbfb17]: https://github.com/bartholomej/firebase-preview-channels-example/commit/5fbfb17