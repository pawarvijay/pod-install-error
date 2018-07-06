### Command

```
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/bin/pod install
```

### Report

* What did you do : pod install?

* What did you expect to happen : install pod?

* What happened instead : error & fail?


### Stack

```
   CocoaPods : 1.5.2
        Ruby : ruby 2.2.6p396 (2016-11-15 revision 56800) [x86_64-darwin15]
    RubyGems : 2.6.8
        Host : Mac OS X 10.11.6 (15G21013)
       Xcode : 8.2.1 (8C1002)
         Git : git version 2.6.2
Ruby lib dir : /Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib
Repositories : master - https://github.com/CocoaPods/Specs.git @ ce4d5175f041db021cec41fe487f7505e6ec1c7a
```

### Plugins

```
cocoapods-check           : 1.0.0
cocoapods-deintegrate     : 1.0.2
cocoapods-plugins         : 1.0.0
cocoapods-plugins-install : 0.0.1
cocoapods-search          : 1.0.0
cocoapods-stats           : 1.0.0
cocoapods-trunk           : 1.3.0
cocoapods-try             : 1.1.0
```

### Podfile

```ruby
# Uncomment the next line to define a global platform for your project
platform :ios, '9.0'

target 'onthemove' do
    rn_path = '../node_modules/react-native'
    rn_maps_path = '../node_modules/react-native-maps'
  
    # See http://facebook.github.io/react-native/docs/integration-with-existing-apps.html#configuring-cocoapods-dependencies
    pod 'yoga', path: "#{rn_path}/ReactCommon/yoga/yoga.podspec"
    pod 'React', path: rn_path, subspecs: [
      'Core',
      'CxxBridge',
      'DevSupport',
      'RCTActionSheet',
      'RCTAnimation',
      'RCTGeolocation',
      'RCTImage',
      'RCTLinkingIOS',
      'RCTNetwork',
      'RCTSettings',
      'RCTText',
      'RCTVibration',
      'RCTWebSocket',
    ]
  
    # React Native third party dependencies podspecs
    pod 'DoubleConversion', :podspec => "#{rn_path}/third-party-podspecs/DoubleConversion.podspec"
    pod 'glog', :podspec => "#{rn_path}/third-party-podspecs/glog.podspec"
    # If you are using React Native <0.54, you will get the following error:
    # "The name of the given podspec `GLog` doesn't match the expected one `glog`"
    # Use the following line instead:
    #pod 'GLog', :podspec => "#{rn_path}/third-party-podspecs/GLog.podspec"
    pod 'Folly', :podspec => "#{rn_path}/third-party-podspecs/Folly.podspec"
  
    # react-native-maps dependencies
    pod 'react-native-maps', path: rn_maps_path
    pod 'react-native-google-maps', path: rn_maps_path  # Remove this line if you don't want to support GoogleMaps on iOS
    pod 'GoogleMaps'  # Remove this line if you don't want to support GoogleMaps on iOS
    pod 'Google-Maps-iOS-Utils' # Remove this line if you don't want to support GoogleMaps on iOS
    pod 'RNVectorIcons', :path => '../node_modules/react-native-vector-icons'
    pod 'ReactNativePermissions', :path => '../node_modules/react-native-permissions'

  end
  
  post_install do |installer|
    installer.pods_project.targets.each do |target|
      if target.name == 'react-native-google-maps'
        target.build_configurations.each do |config|
          config.build_settings['CLANG_ENABLE_MODULES'] = 'No'
        end
      end
      if target.name == "React"
        target.remove_from_project
      end
    end
  end
```

### Error

```
Errno::ENOENT - No such file or directory @ rb_sysopen - /Users/infonius/infoniusProjects/OnTheMoveAPP/node_modules/react-native/third-party-podspecs/DoubleConversion.podspec
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/2.2.0/open-uri.rb:36:in `initialize'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/2.2.0/open-uri.rb:36:in `open'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/2.2.0/open-uri.rb:36:in `open'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/external_sources/podspec_source.rb:19:in `block in fetch'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/user_interface.rb:85:in `titled_section'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/external_sources/podspec_source.rb:11:in `fetch'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/installer/analyzer.rb:697:in `fetch_external_source'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/installer/analyzer.rb:673:in `block (2 levels) in fetch_external_sources'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/installer/analyzer.rb:672:in `each'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/installer/analyzer.rb:672:in `block in fetch_external_sources'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/user_interface.rb:64:in `section'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/installer/analyzer.rb:671:in `fetch_external_sources'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/installer/analyzer.rb:85:in `analyze'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/installer.rb:243:in `analyze'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/installer.rb:154:in `block in resolve_dependencies'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/user_interface.rb:64:in `section'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/installer.rb:153:in `resolve_dependencies'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/installer.rb:116:in `install!'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/command/install.rb:41:in `run'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/claide-1.0.2/lib/claide/command.rb:334:in `run'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/lib/cocoapods/command.rb:52:in `run'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/lib/ruby/gems/2.2.0/gems/cocoapods-1.5.2/bin/pod:55:in `<top (required)>'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/bin/pod:22:in `load'
/Users/infonius/Applications/CocoaPods.app/Contents/Resources/bundle/bin/pod:22:in `<main>'
```
