# Linphone
对Linphone的封装，帮助快速移植

# 安装
通过`cocoapods`安装。仓库更新 `pod repo update` 
podfile文件eg:
```
platform :ios, '9.0'
source "https://gitlab.linphone.org/BC/public/podspec.git"
source "https://github.com/CocoaPods/Specs.git"

target 'linphonedemo2' do
  use_frameworks!

  
  pod 'linphone-sdk' , '4.3' 
  pod 'LinphoneIvna'
end
```

## 登录账号 

` [[ESSipManager instance]login:@"10020" password:@"123456" displayName:@"10020" domain:@"" port:@"5060" withTransport:@"TCP"];`

## 拨打电话

`[[ESSipManager instance]call:@"10019" displayName:@"10019"];`

## 挂断电话

` [[ESSipManager instance]hangUpCall];`

## 获取通话时间


`
[NSTimer scheduledTimerWithTimeInterval:1
    target:self
  selector:@selector(callDurationUpdate)
  userInfo:nil
   repeats:YES];
`

`- (void)callDurationUpdate { 
          int duration =
           linphone_core_get_current_call(LC) ? linphone_call_get_duration(linphone_core_get_current_call(LC)) : 0;
       self.timeLab.text = [LinphoneUtils durationToString:duration];
}`

## 其他的使用 请看ESSipManager.h文件
