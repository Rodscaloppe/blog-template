<!--
.. title: ok
.. slug: aula-sim
.. date: 2020-11-09 19:21:40 UTC
.. tags: sim
.. category: 
.. link: 
.. description: 
.. type: text
-->
# Detox

Gray box end-to-end testing and automation library for mobile apps.

[![NPM Version](https://img.shields.io/npm/v/detox.svg?style=flat)](https://www.npmjs.com/package/detox)
[![NPM Downloads](https://img.shields.io/npm/dm/detox.svg?style=flat)](https://www.npmjs.com/package/detox)
[![Build Status](https://img.shields.io/jenkins/s/http/jenkins-oss.wixpress.com:8080/job/multi-detox-master.svg)](https://jenkins-oss.wixpress.com/job/multi-detox-master/)

- [About](#about)
- [Getting Started](/docs/Introduction.GettingStarted.md)
- [Documentation](/docs/README.md)
- [Usage with Expo](/docs/Guide.Expo.md)

<img src="http://i.imgur.com/eoaDEYp.gif">

## What does a Detox test look like?

This is a test for a login screen, it runs on a device/simulator like an actual user:

```js
describe('Login flow', () => {
    
  it('should login successfully', async () => {
    await device.reloadReactNative();
    await expect(element(by.id('email'))).toBeVisible();
      
    await element(by.id('email')).typeText('john@example.com');
    await element(by.id('password')).typeText('123456');
    await element(by.text('Login')).tap();
      
    await expect(element(by.text('Welcome'))).toBeVisible();
    await expect(element(by.id('email'))).toNotExist();
  });
  
});
```

## About

High velocity native mobile development requires us to adopt continuous integration workflows, which means our reliance on manual QA has to drop significantly. Detox tests your mobile app while it's running in a real device/simulator, interacting with it just like a real user.

The most difficult part of automated testing on mobile is the tip of the testing pyramid - E2E. The core problem with E2E tests is flakiness - tests are usually not deterministic. We believe the only way to tackle flakiness head on is by moving from black box testing to gray box testing. That's where Detox comes into play.

* **Cross Platform:** Write cross-platform tests in JavaScript. Currently supports iOS and Android.
* **Runs on Devices** (not yet supported on iOS): Gain confidence to ship by testing your app on a device/simulator just like a real user.
* **Automatically Synchronized:** Stops flakiness at the core by monitoring asynchronous operations in your app.
* **Made For CI:** Execute your E2E tests on CI platforms like Travis without grief. 
* **Test Runner Independent:** Use Mocha, AVA, or any other JavaScript test runner you like.
* **Debuggable:** Modern async-await API allows breakpoints in asynchronous tests to work as expected.

## Supported versions

### Environment

* **OS**: MacOS 10.13 (High Sierra) or higher.
* **Xcode**: 10.1 or higher.

### React Native

Detox is built from the ground up to support React Native projects as well as pure native ones.

The following React Native versions have been tested:

| iOS    | Android                                                      |
| ------ | ------------------------------------------------------------ |
| <=0.60.4 | <=0.56 - Full support                                        |
|        | >=0.57 <=0.61 - Visibility edge-case: see this [RN issue](https://github.com/facebook/react-native/issues/23870)* |

Future versions are most likely supported, but have not been tested yet. Please open issues if you find specific issues with newer React Native versions.

> (*) A fix for this issue has been merged to React Native and is expected to be released in the upcoming major version (i.e. 0.62.x).

## Getting Started

Read the [Getting Started Guide](/docs/Introduction.GettingStarted.md) to get Detox running on your app in less than 10 minutes.



