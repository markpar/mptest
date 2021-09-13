# Detox/Auth0 Test Repo

This repo contains a sample React Native app to which Detox and React Native Auth0 have been added.  It reproduces the build break detailed in https://github.com/auth0/react-native-auth0/issues/387.

### Instructions
1. Clone the repo.
2. `npm install`
3. `npx detox build -c android.emu.debug`

**Expect**:  Successful Android build.
**Actual**:  Build error about Auth0 placeholders in the `androidTest` build.
```
> Task :react-native-auth0:processDebugAndroidTestManifest FAILED
/Users/mparris/dev/breville-companion-app/node_modules/react-native-auth0/android/build/intermediates/tmp/manifest/androidTest/debug/manifestMerger16326133385671228905.xml Error:
        Attribute data@host at manifestMerger16326133385671228905.xml requires a placeholder substitution but no value for <auth0Domain> is provided.
/Users/mparris/dev/breville-companion-app/node_modules/react-native-auth0/android/build/intermediates/tmp/manifest/androidTest/debug/manifestMerger16326133385671228905.xml Error:
        Attribute data@scheme at manifestMerger16326133385671228905.xml requires a placeholder substitution but no value for <auth0Scheme> is provided.
```