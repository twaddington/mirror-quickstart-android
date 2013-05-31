## mirror-quickstart-android

This is a sample Android application that demonstrates getting a valid OAuth2
token for use with the Google Glass Mirror API without creating a web service.

## Dependencies

This sample application depends on the Google Play Services library project.

## Getting Started

You'll need to first clone the repository to your workstation. The Google Play
Services library is not included in this repository, so you'll need to copy it
to the `libraries/GooglePlayServices` directory:

    $ cp -r $ANDROID_HOME/extras/google/google_play_services/libproject/google-play-services_lib/* libraries/GooglePlayServices

> Note: A build.gradle file has been included for your convenience in the
> `libraries/GooglePlayServices` directory.

After copying the Google Play Services library to the repo you should be able
to build and run the project from the command-line using the typical Gradle
build commands:

    $ ./gradlew installDebug

## Step 1: Generate the signing certificate fingerprint (SHA1)

Google verifies API requests sent from Android devices by matching the package
name and SHA1 signing certificate fingerprint with those defined by the application.

You need to generate the signing certificate's SHA-1 fingerprint by running the
following keytool command in a terminal:

    $ keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android

> Note: The above command expects you to be signing your app with the Android
> debug certificate.

## Step 2: Enable the Mirror API

Before the sample code will work you'll need to enable the Mirror API for your
app. You can do this in your app's API project in the [Google APIs Console][3].

1. Create an API project in the [Google APIs Console][3].
2. Select the **Services** tab in your API project, and enable the Mirror API.
3. Select the **API Access** tab in your API project, and click
   **Create an OAuth 2.0 client ID.**
4. In the **Branding Information** section, provide a name for your application
   (e.g. "Mirror Quickstart Sample"), and click **Next.**
  - Providing a product logo or a homepage URL is optional.
5. In the **Client ID Settings** section, do the following:
  1. Select **Installed application** for the **Application type.**
  2. Select **Android** for the **Installed application type.**
  3. Type "com.example.mirror.android" in **Package name.**
  4. Paste the SHA-1 fingerprint generated in Step 1 into the
     **Signing certificate fingerprint.**
  5. Click **Create Client ID.**

> Note: The Mirror API is currently only available to developers with Glass
> hardware. If you don't see it in your API list, you'll need to contact the
> Glass support and have it enabled.

## Resources

- [Google Play services and OAuth Identity Tools][1]
- [Quickstart: Run a Drive App on Android][2]

## License

This code is released under the Apache 2.0 license.

[1]: http://android-developers.blogspot.com/2012/09/google-play-services-and-oauth-identity.html
[2]: https://developers.google.com/drive/quickstart-android
[3]: https://code.google.com/apis/console/
