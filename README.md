#MultipleImageSelect
An android library that allows selection of multiple images from gallery. It shows an initial
album (buckets) chooser and then images in selected album. Can limit the number of images that
can be selected. Can be used in apps with APK 11 onwards.

Sample app can be found [here](https://github.com/darsh2/MultipleImageSelect/tree/master/sample) 
#Usage
1. Download this project repository as a zip. Extract it.
2. In Android Studio, select File > New > Import Module > Enter path to extracted project.
3. Sync changes in gradle build.
4. In project module's build.gradle file add under dependencies: compile project(':multipleimageselect'). Sync changes.
5. In project's AndroidManifest.xml, add the following under application node:
```xml
<activity
  android:name="com.darsh.multipleimageselect.activities.AlbumSelectActivity"
  android:theme="@style/MultipleImageSelectTheme">
  <intent-filter>
    <category android:name="android.intent.category.DEFAULT" />
  </intent-filter>
</activity>
```
   In the activity from where you want to call image selector, create Intent as follows:
```java
Intent intent = new Intent(this, AlbumSelectActivity.class);
//set limit on number of images that can be selected, default is 10
intent.putExtra(Constants.INTENT_EXTRA_LIMIT, numberOfImagesToSelect);
startActivityForResult(intent, Constants.REQUEST_CODE);
```
   and override onActivityResult as follows:
```java
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
  if (requestCode == Constants.REQUEST_CODE && resultCode == RESULT_OK && data != null) {
    //The array list has the image paths of the selected images
    ArrayList<String> images = data.getStringArrayListExtra(Constants.INTENT_EXTRA_IMAGES);
    ...  
}
```
#Screenshots
![Alt text](https://github.com/darsh2/MultipleImageSelect/blob/master/sample/src/main/res/drawable/screenshots/ss1.png?raw=true) ![Alt text](https://github.com/darsh2/MultipleImageSelect/blob/master/sample/src/main/res/drawable/screenshots/ss2.png?raw=true) ![Alt text](https://github.com/darsh2/MultipleImageSelect/blob/master/sample/src/main/res/drawable/screenshots/ss3.png?raw=true)
#Similar Projects
Similar libraries can be found [here](https://android-arsenal.com/tag/157)
#Acknowledgements
This library makes use of [Picasso](https://github.com/square/picasso) by Square Inc.
#License
```license
Copyright 2015 Darshan Dorai

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
