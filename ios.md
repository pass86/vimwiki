# review
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
