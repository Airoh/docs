---
title: Customizing Lock
description: This tutorial will show you how to customize the Lock widget UI.
---

<%= include('../../../_includes/_package', {
  org: 'auth0-samples',
  repo: 'auth0-ios-objc-sample',
  path: '10-Customizing-Lock',
  requirements: [
    'CocoaPods 1.1.1',
    'Version 8.2 (8C38)',
    'iPhone 6 - iOS 10.2 (14C89)'
  ]
}) %>

### Before Starting

This tutorial assumes you are already familiar with Auth0 and how to Sign up and Sign in using Lock or Auth0 Toolkit. If you're not sure, check out the [login tutorial](/quickstart/native/ios-objc/01-login).

### 1. Create a Theme

Lock UI can be customized by creating your own `A0Theme` instance:

```objc
#import <Lock/Lock.h>
```

```objc
A0Theme *theme = [[A0Theme alloc] init];
```

### 2. Configure Your Theme

Lock's widget UI is composed of several parts that can be customized.

![Lock.png](/media/articles/libraries/lock-ios/customization/Lock-UI-Parts.png)

You can configure these type of properties:

- **Color**: `UIColor` instance.
- **Image**: By using a `String` representing the image's name.
- **Font**: `UIFont` instance.

For instance:

```objc
[theme registerColor: [UIColor redColor] forKey: A0ThemePrimaryButtonNormalColor];
```
So, for example, if you want to achieve something like this:

<div class="phone-mockup"><img src="/media/articles/native-platforms/ios-swift/Custom-Lock-Widget-Screenshot.png" alt="Mobile example screenshot"/></div>

You will need to customize several parts. This is how you do it:

1. Change the logo
```objc
[theme registerImageWithName: @"custom-logo"
                      bundle: [NSBundle mainBundle]
                      forKey: A0ThemeIconImageName];
```

2. Customize the 'Login' text appearance:
```objc
[theme registerColor: [UIColor whiteColor] forKey: A0ThemeTitleTextColor];
[theme registerFont: [UIFont systemFontOfSize: 24] forKey: A0ThemeTitleFont];
```

3. Customize the 'OR' text appearance:
```objc
[theme registerColor: [UIColor whiteColor] forKey: A0ThemeSeparatorTextColor];
[theme registerFont: [UIFont systemFontOfSize: 18] forKey: A0ThemeSeparatorTextFont];
```

4. Customize the text fields:
```objc
[theme registerColor: [self lightVioletColor] forKey: A0ThemeTextFieldIconColor];
[theme registerColor: [self lightVioletColor] forKey: A0ThemeTextFieldPlaceholderTextColor];
[theme registerColor: [UIColor whiteColor] forKey: A0ThemeTextFieldTextColor];
[theme registerFont: [UIFont systemFontOfSize: 14] forKey: A0ThemeTextFieldFont];
```

5. Customize the primary button (ACCESS):
```objc
[theme registerColor: [UIColor whiteColor] forKey: A0ThemePrimaryButtonNormalColor];
[theme registerColor: [self lightVioletColor] forKey: A0ThemePrimaryButtonHighlightedColor];
[theme registerColor: [self darkVioletColor] forKey: A0ThemePrimaryButtonFont];
[theme registerFont: [UIFont boldSystemFontOfSize: 20] forKey: A0ThemePrimaryButtonFont];
```

6. Configure the secondary buttons (sign up / reset password):
```objc
[theme registerColor: [self lightVioletColor] forKey: A0ThemeSecondaryButtonBackgroundColor];
[theme registerColor: [UIColor whiteColor] forKey: A0ThemeSecondaryButtonTextColor];
```

7. Add a background image:
```objc
[theme registerImageWithName:@"custom-background"
                      bundle:[NSBundle mainBundle]
                      forKey:A0ThemeScreenBackgroundImageName];
```

8. Configure the X button:
```objc
[theme registerColor:[self lightVioletColor] forKey: A0ThemeCloseButtonTintColor];
```

9. Configure the status bar:
```objc
[theme setStatusBarStyle:UIStatusBarStyleLightContent];
```

### 3. Register Your Theme

Last, but not least: You still need to register your theme before presenting the login dialog:

```objc
[[A0Theme sharedInstance] registerTheme: theme];
```

### Done!

In conclusion, here is the code snippet you need to keep in mind:

```objc
A0Theme *theme = [[A0Theme alloc] init];
// customize your theme here
[[A0Theme sharedInstance] registerTheme: theme];
```

Piece of cake, wasn't it? You've just customized the Lock widget!

### Appendix: Customizable Properties List

Here is a list containing all the properties that can be customized:

- `A0ThemePrimaryButtonNormalColor`
- `A0ThemePrimaryButtonHighlightedColor`
- `A0ThemePrimaryButtonNormalImageName`
- `A0ThemePrimaryButtonHighlightedImageName`
- `A0ThemePrimaryButtonFont`
- `A0ThemePrimaryButtonTextColor`

#### Secondary Button

- `A0ThemeSecondaryButtonBackgroundColor`
- `A0ThemeSecondaryButtonNormalImageName`
- `A0ThemeSecondaryButtonHighlightedImageName`
- `A0ThemeSecondaryButtonFont`
- `A0ThemeSecondaryButtonTextColor`

#### Text Field

- `A0ThemeTextFieldFont`
- `A0ThemeTextFieldTextColor`
- `A0ThemeTextFieldPlaceholderTextColor`
- `A0ThemeTextFieldIconColor`

#### Title

- `A0ThemeTitleFont`
- `A0ThemeTitleTextColor`

#### Icon

- `A0ThemeIconBackgroundColor`
- `A0ThemeIconImageName`

#### Background

- `A0ThemeScreenBackgroundColor`
- `A0ThemeScreenBackgroundImageName`

#### Message & Description

- `A0ThemeDescriptionFont`
- `A0ThemeDescriptionTextColor`
- `A0ThemeSeparatorTextFont`
- `A0ThemeSeparatorTextColor`

#### CredentialBox

- `A0ThemeCredentialBoxBorderColor`
- `A0ThemeCredentialBoxSeparatorColor`
- `A0ThemeCredentialBoxBackgroundColor`

#### Close Button

- `A0ThemeCloseButtonTintColor`

Have fun customizing whatever you need from there.
