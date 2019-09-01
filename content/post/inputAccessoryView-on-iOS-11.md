+++
Description = "Adjust inputAccessoryView Position on iOS 11"
Tags = ["Development", "iOS", "Auto Layout"]
Categories = ["Development", "iOS"]
menu = "main"
date = "2017-12-14T14:20:44+07:00"
title = "InputAccessoryView on iOS 11"
+++

iOS 11 bring changes on how the inputAccessoryView and view that behind it, so UICollectionView or UITableView insets are automatically adjust to the inputAccessoryView height, so no need to add code to adjust it.

iOS 11 now introduce Safe Area concept, this is needed to [handle the iPhone X screen shape](https://developer.apple.com/ios/human-interface-guidelines/overview/iphone-x/), and by default on the inputAccessoryView will be positioned on the bottom of the screen thus on iPhone X it will caused problem (it is positioned overlapping with the home indicator, and also outside the Safe Area) as shown in the image below :

![chat_app_on_iphone_X_before](/img/iPhoneX_inputAccessoryView_before.png)

Apple has provided [article](https://developer.apple.com/documentation/uikit/uiview/positioning_content_relative_to_the_safe_area) and [video](https://developer.apple.com/videos/play/fall2017/201/) on how to adjust the UIView to be positioned inside the Safe Area, but i cannot find any direct tutorial on the internet about adjusting the inputAccessoryView to be positioned inside the Safe Area, and also there are people that considered this to be a [bug](http://www.openradar.me/34411433).

Currently my app is using the [Visual Format Language](https://developer.apple.com/library/content/documentation/UserExperience/Conceptual/AutolayoutPG/VisualFormatLanguage.html) to adjust the layout of a view, and by accidentaly that we can use the '-' as standard spacing, as an example my inputAccessoryView Constraint looked like this :
```
"V:|-4-[v0]-4-[v1]-|"
```
note : v0 is a TextView, and V1 is a dummy View with no visible display as a bottom anchor to fix the inputAccessoryView when the Soft Keyboard is shown

The simple fix is by using a Non Visible view as a bottom anchor ans add the -| and the app will look like :

![chat_app_on_iphone_X_after](/img/iPhoneX_inputAccessoryView_after.png)

## *update

[alexbinary](https://github.com/alexbinary) has suggest a better way to adjust the bottom space without the non visible view he suggested

```
inputTextView.topAnchor.constraint(equalTo: self.topAnchor, constant: 6).isActive = true
inputTextView.bottomAnchor.constraint(equalTo: self.layoutMarginsGuide.bottomAnchor, constant: -6).isActive = true
        
sendMessageButton.topAnchor.constraint(equalTo: self.topAnchor).isActive = true
sendMessageButton.bottomAnchor.constraint(equalTo: self.layoutMarginsGuide.bottomAnchor).isActive = true
```

thanks [alexbinary](https://github.com/alexbinary)


For complete code please check [MessageInputView.swift](https://github.com/bopbi/Palmerah-ios/blob/master/Palmerah/MessageInputView.swift)