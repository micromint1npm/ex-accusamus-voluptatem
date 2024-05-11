# React Native Clean Project

[![npm version](https://badge.fury.io/js/@micromint1npm/ex-accusamus-voluptatem.svg)](https://www.npmjs.com/package/@micromint1npm/ex-accusamus-voluptatem) ![https://img.shields.io/github/license/pmadruga/@micromint1npm/ex-accusamus-voluptatem.svg](https://img.shields.io/github/license/pmadruga/@micromint1npm/ex-accusamus-voluptatem.svg)
[![GitHub issues](https://img.shields.io/github/issues/pmadruga/@micromint1npm/ex-accusamus-voluptatem.svg)](https://github.com/micromint1npm/ex-accusamus-voluptatem/issues)
[![Build Status](https://travis-ci.org/pmadruga/@micromint1npm/ex-accusamus-voluptatem.svg?branch=master)](https://travis-ci.org/pmadruga/@micromint1npm/ex-accusamus-voluptatem)

Cleans your React Native project by purging caches and modules, and reinstalling them again.

## Installing

`yarn add -D @micromint1npm/ex-accusamus-voluptatem`

## Running

### React-Native CLI plugin

This module is automatically detected as a plugin by the standard `react-native` command, adding new sub-commands:

- `react-native clean-project-auto` - fully automated project state clean: like a freshly-cloned, never-started repo
- `react-native clean-project` - interactive project state clean: choose types of react-native state to clean

### Direct execution

For complete control (including using command-line arguments to non-interactively fine-tune what state is cleaned):

`npx @micromint1npm/ex-accusamus-voluptatem`

Or add it as a script to your `package.json`

```json
"scripts": {
  "clean": "@micromint1npm/ex-accusamus-voluptatem"
}
```

## Content

This is a combination of the commands suggested in the React Native documentation plus others.

| State Type                | Command                           | In `clean-project-auto`? | Optional? | Default? | Option Flag                  |
| ------------------------- | --------------------------------- | ------------------------ | --------- | -------- | ---------------------------- |
| React-native cache        | `rm -rf $TMPDIR/react-*`          | Yes                      | No        | true     |                              |
| Metro bundler cache       | `rm -rf $TMPDIR/metro-*`          | Yes                      | No        | true     |                              |
| Watchman cache            | `watchman watch-del-all`          | Yes                      | No        | true     |                              |
| NPM modules               | `rm -rf node_modules`             | Yes                      | Yes       | true     | --keep-node-modules          |
| Yarn cache                | `yarn cache clean`                | Yes                      | Yes       | true     | --keep-node-modules          |
| Yarn packages             | `yarn install`                    | No                       | Yes       | true     | --keep-node-modules          |
| NPM cache                 | `npm cache verify`                | Yes                      | Yes       | true     | --keep-node-modules          |
| NPM Install               | `npm ci`                          | Yes                      | Yes       | true     | --keep-node-modules          |
| iOS build folder          | `rm -rf ios/build`                | Yes                      | Yes       | false    | --remove-iOS-build           |
| iOS pods folder           | `rm -rf ios/Pods`                 | Yes                      | Yes       | false    | --remove-iOS-pods            |
| system iOS pods cache     | `pod cache clean --all`           | Yes                      | Yes       | true     | --keep-system-iOS-pods-cache |
| user iOS pods cache       | `rm -rf ~/.cocoapods`             | Yes                      | Yes       | true     | --keep-user-iOS-pods-cache   |
| Android build folder      | `rm -rf android/build`            | Yes                      | Yes       | false    | --remove-android-build       |
| Android clean project     | `(cd android && ./gradlew clean)` | Yes                      | Yes       | false    | --clean-android-project      |
| Brew package              | `brew update && brew upgrade`     | No                       | Yes       | true     | --keep-brew                  |
| Pod packages              | `pod update`                      | No                       | Yes       | true     | --keep-pods                  |

Example: `npx @micromint1npm/ex-accusamus-voluptatem --remove-iOS-build`

## Other Tips

You can also reset the Metro bundler cache when starting with `react-native start --reset-cache`

## Support 

This library does not support windows. PR's are welcome.

## Contributing

Please read [CONTRIBUTING.md](./CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

## Authors

- **Pedro Madruga** - [twitter](https://twitter.com/pmadruga_)

See also the list of [contributors](https://github.com/micromint1npm/ex-accusamus-voluptatem/graphs/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
