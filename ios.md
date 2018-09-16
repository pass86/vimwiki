# review
* https://developer.apple.com/app-store/ratings-and-reviews/
* StoreKit.framework
* [SKStoreReviewController requestReview]

# location
* CoreLocation.framework
* when in use
    * [CLLocationManager requestWhenInUseAuthorization]
    * NSLocationWhenInUseUsageDescription
* always
    * [CLLocationManager requestAlwaysAuthorization]
    * NSLocationAlwaysUsageDescription

# audio
* AVFoundation.framework
* microphone
    * [AVAudioSession requestRecordPermission]
    * NSMicrophoneUsageDescription

# plist
* https://developer.apple.com/library/content/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html

# bitcode
* Bitcode is an intermediate representation of a compiled program.
* https://help.apple.com/xcode/mac/current/#/devbbdc5ce4f

# Provisioning Profiles
* A provisioning profile includes signing certificates, device identifiers, and an App ID.

# Code signing
* Code signing (or signing) an app allows the system to identify who signed the app and to verify that the app has not been modified since it was signed.
