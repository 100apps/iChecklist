# iChecklist
 iOS App Store Submission Checklist

 iOS app提交审核要持续一周或者更久，在提交之前，我们一定要进行「自我审查」，避免被拒。有些问题，我们可能知道，但是由于不是在自己身上出现的，所以不能「感同身受」，很有可能还是掉进这个坑。所以这里制作了一个checklist，提交之前挨个检查，如果确认没有问题，再提交。

[App Store Review Guidelines](https://developer.apple.com/app-store/review/guidelines/)是官方读物，这里搜集的是具体事例，比官方的更易懂，更具体。

官方的Rejected分为`Binary Rejected`和`Metadata Rejected`。前者需要重新排队，后者不需要。

###使用微信、QQ等第三方登录(Binary Rejected)
官方审核的机器上没有安装QQ，在这种情况下，如果提示下载QQ，就会被拒绝。

```
10.6 Details

We were required to install the WeChat app before we can log-in via WeChat. The user should be able to log-in and access their account, without requiring additional applications to be installed.

Next Steps

If you choose to allow users to log-in via WeChat, please use methods that can authenticate users from within your app, such as a native web-view. 
```

###没有使用IDFA，但是却声明自己使用了。
有的统计工具会使用IDFA，为了安全起见，选择了使用IDFA，但是实际上并没有，所以被拒了。IDFA的选项，一定要根据真实情况选择。

```
Your iTunes Connect settings indicate that your app serves third-party advertisements. However, we were unable to locate ads in your app.

Please reply to this message to provide the steps for locating third-party ads in your app. When we hear back from you, we will continue the review.
```
###无法测试
我曾经开发过[体重宝](https://itunes.apple.com/app/id925697616)，一款扫描普通体重秤上的数字并识别纪录的软件，因为官方不可能买一个体重秤去试用，所以只能通过你提供的Demo视频来验证，所以你必须提供一个试用视频。另外，无论任何app，都最好附带一个Demo视频，可以放在YouTube上，这样可以很大程度的减轻审核员的工作量，更容易通过。

```
You can provide a link to a demo video of your app in iTunes Connect. Go to "Manage Your Applications," select your app, click "Edit Information," then scroll to the "Review Notes" section and add the demonstration video access details.
```
###应用内有检查更新的字样
from: <https://www.v2ex.com/t/174105>

版本更新统一走App Store，所以自己的app中，不能有检查更新的功能。2015年3月份，Apple更新规则，有检查应用功能的app直接拒绝。可以改成，当前版本xxx之类的
```
Your app includes an update button or alerts the user to update the app. To avoid user confusion, app version updates must utilize the iOS built-in update mechanism. We’ve attached screenshot(s) for your reference.

Next Steps

Please remove the update feature from your app. To distribute a new version of your app, upload the new app binary version into the same iTunes Connect record you created for the app’s previous version. Updated versions keep the same Apple ID, iTunes Connect ID (SKU), and bundle ID as the original version, and are available free to customers who purchased a previous version.
```

###与html网站功能类似
曾经做了一个移动站：m.example.com。为了快速上架，嵌套了一个UIWebview，然后load首页就提交审核，被拒，因为：
```
the App Store does not accept or distribute web apps
```
如果单纯地想复制一个功能一样的app，提交，也有可能审核不通过，因为：
```
We found that your app duplicates the content and functionality of apps currently submitted for review. 
```
from: <https://www.v2ex.com/t/120574>

###App Crashes
由于我们在开发环境下测试的app，但是提交到了Apple以后，审核员用的是线上环境，如果后台API有改动，一定要保质一致，避免崩溃。所以提交审核的时候，一定要用线上环境跑一遍。

###版权
from:<http://zhihu.com/question/20216099/answer/43732248>

比如新闻聚合累的应用，审核的时候一定不要出现明显没有授权的文章，比如BBC之类的

###出现第三方操作系统的名字或图标
from: <http://zhihu.com/question/20216099/answer/46606239>

第三方操作系统的图标或者名字，不能出现在应用内。例如出现Android的图标关键字被拒，截屏也一定要在iOS设备上截取，因为状态栏是不一样的。图标和Apple的相似也可能被拒绝。

###邀请码
app只有使用邀请码才能进入，被拒绝：

```
2.22 - Apps that arbitrarily restrict which users may use the App, such as by location or carrier, may be rejected

2.22 Details

Your app arbitrarily restrict users by requiring invitation code to register, which is not allowed on the App Store.

We’ve attached screenshot(s) for your reference.

Next Steps

Please revise your app to remove any functionality that limits who can use the app.
```

###应用截屏没有真正的截屏相关的图片

我们的app使用了设计师给的插画作截屏，被拒

```
3.3 - Apps with names, descriptions, screenshots, or previews not relevant to the content and functionality of the App will be rejected

3.3 Details

We also noticed that your marketing screenshot(s) do not sufficiently reflect your app in use.

We've attached screenshot(s) for your reference.

Next Steps

Please revise your screenshots to demonstrate the app functionality in use.

Since your iTunes Connect Application State is Rejected, a new binary will be required. Make the desired metadata changes when you upload the new binary.
```

###应用标题无关关键词堆砌

我们做aso的同事发过来一堆无关的关键词，堆砌到应用标题里面，比如，京东、淘宝之类的。被`元数据拒绝`


```
 3.4 - App names in iTunes Connect and as displayed on a device should be similar, so as not to cause confusion

3.4 Details

Your app name to be displayed on the App Store includes keywords or descriptors, which are not appropriate for use in an app name.

Specifically, the following words in your app name are considered keywords or descriptors:

宜家美物、绝美图库、装修攻略、常用软件、实惠海淘，生活助手，居家必备、时尚创意、最美装潢

Next Steps

Please revise your app name to remove all keywords and descriptions. Keywords can be entered in the Keywords field in iTunes Connect to be used as search terms for your app.

Resources

For information on how to revise your app name, please see Renaming a Project or App.

For information on changing the app name and other metadata in iTunes Connect, please see the section, “Viewing and Changing Your App’s Metadata,” in the iTunes Connect Developer Guide.

```

#版权问题

老外的版权意识很强，所有最好能够为App Store审核单独做一套数据。某些关键词比如android是绝对不能出现的。

而且是二进制拒绝，非常严重。

```
8.5 Details Your app includes content or features that resemble a well-known third-party material, Disney, without the necessary

     8.5 - Apps may not use protected third party material such as trademarks, copyrights, patents or violate 3rd party terms of use. Authorization to use such material must be provided upon request

8.5 Details

Your app includes content or features that resemble a well-known third-party material, Disney, without the necessary authorization. We’ve attached screenshot(s) for your reference.

Pursuant to your agreement with Apple, you represent and warrant that your application does not infringe the rights of another party, and that you are responsible for any liability to Apple because of a claim that your application infringes another party's rights. Moreover, we may reject or remove your application for any reason, at our sole discretion.

Next Steps

Please provide documentary evidence of rights to use this content in your app. Once Legal has reviewed your documentation and confirms its validity, we will proceed with the review of your app.

```

