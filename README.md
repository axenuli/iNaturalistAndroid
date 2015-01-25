# iNaturalistAndroid

iNaturalistAndroid is an Android app for [iNaturalist.org](http://www.inaturalist.org).

## Eclipse Setup

### From a terminal

```bash
cd path/to/your/workspace
git clone REPO_PATH
# e.g. git clone git@github.com:inaturalist/iNaturalistAndroid.git, though it will be different 
# if you're working on your own fork

# Get the JAR deps
mkdir iNaturalistAndroid/libs/
cd iNaturalistAndroid/libs/
wget https://github.com/loopj/android-async-http/raw/master/releases/android-async-http-1.3.1.jar
wget http://psg.mtu.edu/pub/apache//commons/collections/binaries/commons-collections-3.2.1-bin.tar.gz
tar xzvf commons-collections-3.2.1-bin.tar.gz
wget http://apache.cs.utah.edu//commons/lang/binaries/commons-lang3-3.1-bin.tar.gz
tar xzvf commons-lang3-3.1-bin.tar.gz
wget http://archive.apache.org/dist/httpcomponents/httpclient/binary/httpcomponents-client-4.1.2-bin.tar.gz
tar xzvf httpcomponents-client-4.1.2-bin.tar.gz
cd ../../

# Get the FacebookSDK
git clone git://github.com/facebook/facebook-android-sdk.git
./facebook-android-sdk/scripts/build_and_test.sh
# Remove the file `facebook\libs\android-support-v4.jar` (since we have a newer copy of that file within our iNat project)

# Get the Android-PullToRefresh library
git clone git://github.com/budowski/Android-PullToRefresh.git

# Get the ActionBarSherlock library
wget https://codeload.github.com/JakeWharton/ActionBarSherlock/legacy.zip/4.4.0
# Extract only the `actionbarsherlock` folder
# Remove the file `actionbarsherlock\libs\android-support-v4.jar` (since we have a newer copy of that file within our iNat project)

# Get the Android Switch Backport library
wget https://github.com/BoD/android-switch-backport/archive/master.zip
# Extract only the `library` folder


# Copy the example config file and add your own API keys etc
cp iNaturalistAndroid/res/values/config.xml.example iNaturalistAndroid/res/values/config.xml
```

### From Eclipse

1. Open menu `File / Import...`
1. Choose `General / Existing Projects into Workspace`
1. `Select root directory` as `path/to/your/workspace/INaturalistAndroid`
1. Check the `INaturalistAndroid` project and click `Finish`
1. Open menu `File / Import...`
1. Choose `General / Existing Projects into Workspace`
1. `Select root directory` as `path/to/your/workspace/facebook-android-sdk/facebook`
1. Check the `FacebookSDK` project and click `Finish`
1. Right-click the `FacebookSDK` project and select `Build Path` -> `Configure Build Path`
1. Make sure that `android-support-v4.jar` does not appear (remove if so)
1. Copy the `android-support-v4.jar` file to your `INaturalistAndroid\libs` folder (from `/android-sdk/extras/android/support/v4`)
1. `Add JARs` -> Select the `INaturalistAndroid` project -> `libs` folder -> `android-support-v4.jar`
1. Install Google Play Services SDK (as specified in `http://developer.android.com/google/play-services/setup.html`) using the SDK Manager
1. Copy the `google-play-services.jar` file to your `INaturalistAndroid\libs` folder (from `/android-sdk/extras/google/google_play_services/libproject/google-play-services_lib/libs`)
1. `Add JARs` -> Select the `INaturalistAndroid` project -> `libs` folder -> `google-play-services.jar`
1. Open menu `File / Import...`
1. Choose `General / Existing Existing Android Code into Workspace`
1. `Select root directory` as `path/to/your/workspace/Android-PullToRefresh/library`
1. Check the `library` project and click `Finish`
1. Open menu `File / Import...`
1. Choose `General / Existing Android Code into Workspace`
1. `Select root directory` as `path/to/your/workspace/actionbarsherlock`
1. Check the `actionbarsherlock` project and click `Finish`
1. Open menu `File / Import...`
1. Choose `General / Existing Android Code into Workspace`
1. `Select root directory` as `path/to/your/workspace/android-switch-backport`
1. Check the `android-switch-backport` project and click `Finish`
1. Right-click the `iNaturalistAndroid` project and select `Properties`
1. Go to `Android` tab
1. Scroll down to the `Library` box and click `Add`
1. Select the `actionbarsherlock` , `PullToRefresh-library` and `android-switch-backport` projects and press OK
1. Press OK to close the dialog
1. Install Crashlytics for Android (follow instructions): http://download.crashlytics.com/android/eclipse/
1. Clean and rebuild the entire workspace (all imported projects)

In theory it should build now!
