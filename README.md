 <h1 align="center">Huawei-Admob Mediation Github Documentation</h3>

# Introduction

In this documentation we explained how to use Huawei-Admob mediation with in the different platforms.

# Compatibility

|   | Banner Ad | Interstitial Ad | Rewarded Ad | Native Ad |
| --- | --- | --- | --- | --- |
| Native (Java/Kotlin) | ✅ | ✅ | ✅ | ✅ |
| React Native | ✅ | ✅ | ✅ | ✅ |
| Flutter |✅|✅| ✅ | ❌ |
| Cordova |✅|✅| ❌ | ❌ |

# How to start?
  
## Create an ad unit on Huawei Publisher Service

1. Sign in to [Huawei Developer Console] (https://developer.huawei.com/consumer/en/console) and create an AdUnit

## Create a custom event on Google AdMob

1. Sign in to [Google AdMob console] ([https://apps.admob.com/v2](https://apps.admob.com/v2))
2. Go to "**Mediation -> Create a new Mediation Group**" (or, use one of the existing Mediation groups)
3. Under the "**Ad Sources**" section, click "**Add Custom Event**" Give it a label (eg: Huawei Banner Custom Event) and an eCPM, click "**Continue**"
4. Enter the class name "**com.hmscl.huawei.admob\_mediation.all\_ads**" as the Class Name, and your Huawei's AdUnit ID from step 1 as the parameter
5. Add the adapter and its dependencies into your project
6. Configuration of custom event is done.

## Create a custom event on Google Ad Manager

1. Sign in to [Google AdManager console] ([https://admanager.google.com/home/](https://admanager.google.com/home/))
2. Add Huawei as a Ad Network Company by selecting Other company in Ad Network section
3. Go to "**Delivery  -> Yield groups**" (or, use one of the existing groups)
4. 	Create a yield group and add Huawei as a yield partner
5. Enter the class name "**com.hmscl.huawei.admob\_mediation.all\_ads**" as the Class Name, and your Huawei's AdUnit ID from step 1 as the parameter
6. Add the adapter and its dependencies into your project
7. Configuration of custom event is done.

# Integrate the Huawei Mediation SDK

**Note** : A device with Huawei Mobile Services (HMS) installed is required

In the **project-level** build.gradle, include Huawei's Maven repository.

```groovy
repositories {
    google()
    jcenter() // Also, make sure jcenter() is included
    maven { url 'https://developer.huawei.com/repo/' } // Add this line
    maven {url "https://jitpack.io"} // Add this line
}

...

allprojects {
    repositories {
        google()
        jcenter() // Also, make sure jcenter() is included
        maven { url 'https://developer.huawei.com/repo/' } //Add this line
        maven {url "https://jitpack.io"} // Add this line
    }
}
```

In the app-level build.gradle, include Huawei Ads dependency (required by the adapter) and the adapter

```groovy
dependencies {
    implementation 'com.huawei.hms:ads:3.4.41.304'
    implementation 'com.github.Explore-In-HMS:huawei.admob_mediation:1.0.2'
}
```
> **_NOTE:_**  If your app can run only on Huawei mobile phones, you can integrate the Huawei Ads Lite SDK instead of Huawei Ads SDK (Optional)

```groovy
dependencies {
    implementation 'com.huawei.hms:ads-lite:13.4.41.302'
    implementation 'com.github.Explore-In-HMS:huawei.admob_mediation:1.0.2'
}
```

1. Generate a keystore file

2. Place the keystore file in the app directory

3. Modify the app module build.gradle file - update the signingConfigs to your keystore's setting

4. Build the project or run the app in your device / emulator

**Important:** _To add Huawei Ads Kit SDK and Mediation adapter, the native project should be opened with Android Studio._

# Platforms

## Native

This section demonstrates how to use AdMob mediation feature with Huawei Ads Kit on Native android app.

Firstly, integrate the Admob SDK for Android

[Admob Android SDK](https://developers.google.com/admob/android/quick-start) can be used for all ad types.

**Note** : Developers can find app level build.gradle in their project from __**"app-folder/app/build.gradle"**__

### **Banner Ad**

To use _Banner_ ads in Native android apps, please check the Admob SDK. Click [here](https://developers.google.com/admob/android/banner) to get more information about Admob SDKs _Banner_ Ad development.

### **Interstitial Ad**

To use Interstitial ads in Native android apps, please check the Admob SDK. Click [here](https://developers.google.com/admob/android/interstitial-fullscreen) to get more information about Admob SDKs Interstitial Ad development.

### **Rewarded Ad**

To use _Rewarded_ ads in Native android _Rewarded_, please check the Admob SDK. Click [here](https://developers.google.com/admob/android/rewarded-fullscreen) to get more information about Admob SDKs _Banner_ Ad development.

### **Native Ads**

To use _Native_ ads in Native android apps, please check the Admob SDK. Click [here](https://developers.google.com/admob/android/native/start) to get more information about Admob SDKs _Native_ Ad development.

## React Native


This section demonstrates how to use AdMob mediation feature with Huawei Ads Kit on React-Native.

**Important:** _There is no official React Native SDK for Admob therefore third party SDKs has been used in the demonstration._

Firstly, integrate the React Native Admob SDKs as below depending on type of ad

**Note**: Developers can find app level build.gradle in their project from __**"app-folder/app/build.gradle"**__

For **Banner** , **Interstitial** and **Rewarded** Ad type's [react-native-admob](https://github.com/sbugert/react-native-admob) SDK can be used.

For **Native** ad type [react-native-admob-native-ads](https://github.com/ammarahm-ed/react-native-admob-native-ads) SDK can be used.

Then use the following sample codes based on specific ad types.

## **Sample Codes Based on Ad Types**

### **Banner Ad**

```jsx
<AdMobBanner
adSize="fullBanner"
adUnitId={BannerAdId}
testDevices={[AdMobBanner.simulatorId]}
onAdFailedToLoad={error => console.error(error)} />
```

### **Interstitial Ad**

```jsx
AdMobInterstitial.setAdUnitID(InterstitialAdId);
AdMobInterstitial.setTestDevices([AdMobInterstitial.simulatorId]);
AdMobInterstitial.requestAd().then(() => AdMobInterstitial.showAd());
```

### **Rewarded Ad**

```jsx
AdMobRewarded.setAdUnitId(RewardedAdId);
AdMobRewarded.requestAd().then(() => AdMobRewarded.showAd());
```
### **Native Ads**

```jsx
<NativeAdView
adUnitID= {NativeAdId} 
onAdFailedToLoad={error => console.error(error)} /> 
```

## Flutter

This section demonstrates how to use AdMob mediation feature with Huawei Ads Kit on Flutter.

**Important:** _There is no official Flutter SDK for_ AdMob _therefore third party SDKs has been used in the demonstration._

Firstly, integrate the Flutter_ AdMob _SDKs as below depending on type of ad

**Note**: Developers can find app level build.gradle in their project from  __**"app-folder/android/app/build.gradle"**__

For **Banner** and **Interstitial** Ad types [admob\_flutter](https://github.com/kmcgill88/admob_flutter) SDK can be used.

For **Banner** and **Rewarded** Ad types [googleads-mobile-flutter](https://github.com/googleads/googleads-mobile-flutter) SDK can be used.

### **Native Ad**

Native ads are not supported with this SDK. To use Native ads in Flutter app, please check the HMS Core Ads Kit Flutter SDK. Click [here](https://developer.huawei.com/consumer/en/doc/development/HMS-Plugin-Guides-V1/native-ads-0000001050198817-V1) to get more information about HMS Core Flutter SDKs Native Ad development.

Then use the following sample codes based on specific ad types.


## **Sample Codes Based on Ad Types**

### **Banner Ad**

```dart
…
Admob.initialize();
…
child: AdmobBanner(
  adUnitId: "Your Banner Ad Unit ID",
  adSize: AdMobBannerSize.[Selected_Banner_Size],
  listener: (AdmobAdEvent event,
      Map<String, dynamic> args) {
    handleEvent(event, args, 'Banner');
  },
  onBannerCreated:
      (AdmobBannerController controller) {
  },
),
…
```
### **Interstitial Ad**

```dart
…
Admob.initialize();
…
interstitialAd = AdmobInterstitial(
  adUnitId: "Your Intersitatial Ad Unit ID",
  listener: (AdmobAdEvent event, Map<String, dynamic> args) {
    if (event == AdmobAdEvent.closed) interstitialAd.load();
    handleEvent(event, args, 'Interstitial');
  },
);
```
### **Rewarded Ad**

```dart
class RewardedAd extends AdWithoutView {
  ...
  static final String testAdUnitId = Platform.isAndroid
      ? 'Your Rewarded Ad Unit ID'
      : 'Your Rewarded Ad Unit ID';

  @override
  Future<void> load() async {
    await instanceManager.loadRewardedAd(this);
  }
}
```

## Cordova

This section demonstrates how to use AdMob mediation feature with Huawei Ads Kit on Cordova.

**Important:** _There is no official Cordova SDK for_ AdMob _therefore third party SDKs has been used in the demonstration._

Firstly, integrate the Cordova_ AdMob _SDKs as below depending on type of ad

**Note**: Developers can find app level build.gradle in their project from __**"app-folder/platforms/android/app/build.gradle"**__

For **Banner** and **Interstitial** Ad types [admob-plus](https://github.com/admob-plus/admob-plus) SDK can be used.

### **Rewarded Ad**

Rewarded ads are not supported with this SDK. To use Rewarded ads in Cordova app, please check the HMS Core Ads Kit Cordova SDK. Click [here](https://developer.huawei.com/consumer/en/doc/development/HMS-Plugin-Guides-V1/rewarded-ads-0000001050195456-V1) to get more information about HMS Core Cordova SDKs Rewarded Ad development.

### **Native Ad**

Native ads are not supported in Cordova. To use Native Ads in Cordova App please check the HMS Core Ads Kit Cordova SDK. Click [here](https://developer.huawei.com/consumer/en/doc/development/HMS-Plugin-Guides-V1/native-ads-0000001050197495-V1) to get more information about HMS Core Cordova SDK Native Ad development.

Then use the following sample codes based on specific ad types.

## **Sample Codes Based on Ad Types**

### **Banner Ads**
```js
showBannerAd() {
  const banner = new admob.BannerAd({
    adUnitId: '[Enter BannerAdID here]',
  })
  return banner.show({ position: 'bottom' })
},
```

### **Interstitial Ads**

```js
showInterstitialAd() {
  const interstitial = new admob.InterstitialAd({
          adUnitId: '[Enter InterstitialAdID here]',
  })
  return interstitial.load().then(() => interstitial.show())
},
```

# Screenshots

## AdMob
<table>
<tr>
<td>
<img src="https://user-images.githubusercontent.com/41696219/109941743-8626a780-7ce4-11eb-8aa8-4da1e3f1092f.png" width="200">

Banner Ad
</td>

<td>
<img src="https://user-images.githubusercontent.com/41696219/109941887-aa828400-7ce4-11eb-9409-d93adf506724.JPG" width="200">

Interstitial Ad
</td>

<td>
<img src="https://user-images.githubusercontent.com/41696219/109941974-c4bc6200-7ce4-11eb-81b8-e35a2589d528.JPG" width="200">

Rewarded Ad
</td>
<td>
<img src="https://user-images.githubusercontent.com/41696219/109942031-d43bab00-7ce4-11eb-815f-403918a6b7f4.png" width="200">

Native Ad
</td>
</tr>
</tr>
</table>

## Huawei
<table>
<tr>
<td>
<img src="https://user-images.githubusercontent.com/41696219/109942123-ee758900-7ce4-11eb-96a3-11cce5454c51.png" width="200">

Banner Ad
</td>

<td>
<img src="https://user-images.githubusercontent.com/41696219/109939330-01d32500-7ce2-11eb-9e39-6a9237ca8c54.JPG" width="200">


Interstitial Ad
</td>

<td>
<img src="https://user-images.githubusercontent.com/41696219/109942227-0baa5780-7ce5-11eb-8b69-086924473db0.png" width="200">

Rewarded Ad
</td>
<td>
<img src="https://user-images.githubusercontent.com/41696219/109942307-211f8180-7ce5-11eb-8c3e-7d21903bf6d1.png" width="200">

Native Ad
</td>

</tr>
</tr>
</table>




