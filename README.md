# ez-vcard-android

Maps the Android vCard API to the [ez-vcard](http://github.com/mangstadt/ez-vcard) API.

Converts an [ez-vcard](http://github.com/mangstadt/ez-vcard) `VCard` object into the appropriate Android data fields, so it can be added to an Android user's contact list.

#Code Sample

```java
File vcardFile = ...
VCardReader reader = null;
try {
  reader = new VCardReader(vcardFile);
  reader.registerScribe(new AndroidCustomFieldScribe());

  ContactOperations operations = new ContactOperations(getApplicationContext());
  VCard vcard = null;
  while ((vcard = reader.readNext()) != null) {
      operations.insertContact(vcard);
  }
} finally {
  reader.close();
}
```

#Download

A downloadable JAR file does not exist yet.  You can either build the project yourself, or copy and paste the code into your project (please leave the copyright notice in the source code if you choose the latter option).

#Development Environment Setup Instructions

If you are not using an Android-enabled IDE, follow these instructions so you can get the project to a point where you can build it.

 * Go to https://developer.android.com/sdk/index.html
 * Click on "View All Downloads and Sizes"
 * Download the appropriate file for your OS in the "SDK Tools Only" table.
 * Unzip/install the file to a location of your choice.
 * Run the "tools/android" script in the installation to open the Android SDK Manager.
 * Install the the following packages (if some of these aren't in the list, install what you can, then restart the SDK Manager to see if they appear):
  * Tools -> Android SDK Tools (latest version)
  * Tools -> Android SDK Platform-tools (latest version)
  * Tools -> Android SDK Build-tools (version 19.0.3)
  * Android 4.4.2 (API 19) -> SDK Platform
  * Extras -> Android Support Library (latest version)
  * Extras -> Android Support Repository (latest version)
 * Open the "local.properties" file in the root of the Android Mapper project, change the "sdk.dir" property to point to where you unzipped/installed the SDK Tools. 
 * Run `./gradlew build` to build the application.
