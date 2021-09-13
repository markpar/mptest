# Detox/Auth0 Test Repo

This repo contains a sample React Native app to which Detox and React Native Auth0 have been added.  It reproduces the build break detailed in https://github.com/auth0/react-native-auth0/issues/387.

### Instructions
1. Clone the repo.
2. `npm install`
3. `npx detox build -c android.emu.debug`

**Expect**:  Successful Android build.
**Actual**:  Build error about Auth0 placeholders in the `androidTest` build.
```
/Users/mparris/dev/mptest/node_modules/react-native-auth0/android/build/intermediates/tmp/manifest/androidTest/debug/manifestMerger10599473213081257025.xml Error:
        Attribute data@host at manifestMerger10599473213081257025.xml requires a placeholder substitution but no value for <auth0Domain> is provided.
/Users/mparris/dev/mptest/node_modules/react-native-auth0/android/build/intermediates/tmp/manifest/androidTest/debug/manifestMerger10599473213081257025.xml Error:
        Attribute data@scheme at manifestMerger10599473213081257025.xml requires a placeholder substitution but no value for <auth0Scheme> is provided.
```
### Background
I created this repro in this order:
1. `npx react-native init` to create the skeleton app, then verified it built and ran successfully
2. `npm install --save-dev detox@latest`  (`18.20.3` as of this writing)
3. Integrated Detox into the Android build using instructions at
   a. https://github.com/wix/Detox/blob/master/docs/Guide.Jest.md
   b. https://github.com/wix/Detox/blob/master/docs/Introduction.Android.md
4. `npm install --save react-native-auth0@latest`  (`2.9.0` as of this writing)
