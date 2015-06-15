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
