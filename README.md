# @humanoids/react-native-recaptcha

This package is forked from `@haskkor/react-native-recaptchav3`. Refreshing the reCAPTCHA v3 token caused the following error:

```
Error evaluating injectedJavaScript: This is possibly due to an unsupported return type. Try adding true to the end of your injectedJavaScript string.
```

Also, `originWhitelist` needed to be specified. Fixes for these two issues have been applied.

Below you will find the original README with updated code snippets.

# react-native-recaptcha

[![npm](https://img.shields.io/npm/v/@humanoids/react-native-recaptcha.svg)](https://www.npmjs.com/package/@humanoids/react-native-recaptcha) [![npm](https://img.shields.io/npm/dt/@humanoids/react-native-recaptcha.svg)](https://www.npmjs.com/package/@humanoids/react-native-recaptcha)

_React native component to use the invisible reCAPTCHA v3 from Google_

https://www.google.com/recaptcha/intro/v3.html

## Installation

```
npm install --save @humanoids/react-native-recaptcha
```

or

```
yarn add @humanoids/react-native-recaptcha
```

**Note:** React Native Community Webview requires you to link the native dependencies (https://github.com/react-native-community/react-native-webview/blob/master/docs/Getting-Started.md)

## Demo

![automatic](https://user-images.githubusercontent.com/10620919/48578194-e1022c80-e97d-11e8-8bb9-6e96a8a25aec.gif) ![retrybutton](https://user-images.githubusercontent.com/10620919/48578212-ed868500-e97d-11e8-95ab-1d5ec0280b8f.gif)

## Usage

Automatically get a captcha token:

```
import ReCaptchaV3 from '@humanoids/react-native-recaptcha'

<ReCaptchaV3
  captchaDomain={'https://yourowndomainname.co.nz'}
  siteKey={'yourownsitekey'}
  onReceiveToken={(token: string) => Alert.alert('CAPTCHA', token)}/>
```

One could also use a trigger to request a new token using the reference of the component:

```
import ReCaptchaV3 from '@humanoids/react-native-recaptcha'

<ReCaptchaV3
  ref={(ref: RecaptchaV3) => this._captchaRef = ref}
  captchaDomain={'https://yourowndomainname.co.nz'}
  siteKey={'yourownsitekey'}
  onReceiveToken={(token: string) => Alert.alert('CAPTCHA', token)}/>

<TouchableOpacity onPress={() => this._captchaRef.refreshToken()}>
  <Text>Retry</Text>
</TouchableOpacity>
```

## Options

| Key                  | Description                                                   | Default | Required | Type                             |
| -------------------- | ------------------------------------------------------------- | ------- | -------- | -------------------------------- |
| **`captchaDomain`**  | Your url registered with Google reCAPTCHA                     | `None`  | `true`   | `string`                         |
| **`onReceiveToken`** | The callback used to get the captcha token from the component | `None`  | `true`   | `(captchaToken: string) => void` |
| **`siteKey`**        | The site key provided by Google reCAPTCHA                     | `None`  | `true`   | `string`                         |

## [Changelog](https://github.com/humanoidsbv/react-native-recaptcha/blob/master/CHANGELOG.md)

## Contributing

Pull requests are welcome.

## [License](https://github.com/humanoidsbv/react-native-recaptcha/blob/master/LICENSE)
