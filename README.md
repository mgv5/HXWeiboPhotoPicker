# HXWeiboPhotoPicker - 仿微博照片选择器

<img src="http://wx1.sinaimg.cn/mw690/ade10dedgy1fdgf4qs610j20ku112n31.jpg" width="270" height="480"> 

## 一.  更新历史
- 2017-03-07 修复通过相机拍照时照片旋转90°的问题
- 2017-03-08 修复拍照之后,在浏览大图时选中图片,列表界面Cell没有选中的问题
- 2017-03-09 添加查看 LivePhoto 功能、是否查看GIF图和LivePhoto的控制开关,修复Cell重复注册3DTouch功能导致内存一直增加问题
- 2017-03-10 添加控制是否开启相机功能的开关 以及 控制相机功能是否内/外置开关.

## 二.  特性

- [x] 查看/选择GIF图片
- [x] 照片、视频可同时多选/原图
- [x] 3DTouch预览照片
- [x] 长按拖动改变顺序
- [x] 自定义相机拍照/录制视频
- [x] 自定义转场动画
- [x] 查看/选择LivePhoto IOS9以上才有用

## 三.  安装

- 手动导入：将项目中的“HXWeiboPhotoPicker”文件夹拖入项目中
- 只使用照片选择功能 导入头文件 "HXPhotoViewController.h"
- 选完照片/视频后自动布局功能 导入头文件 "HXPhotoView.h"

## 四.  要求

- iOS8及以上系统可使用. ARC环境.
- 在Xcode8环境下将项目运行在iOS10的设备/模拟器中，访问相册和相机需要配置两个info.plist文件。                                              Privacy - Photo Library Usage Description 和 Privacy - Camera Usage Description。
- 相机拍照功能请使用真机调试

## 五.  例子

- HXPhotoManager 照片管理类相关属性介绍
```
是否把相机功能放在外面 默认 NO   使用 HXPhotoView 时有用
outerCamera;

是否打开相机功能
openCamera;

是否开启查看GIF图片功能 - 默认开启
lookGifPhoto;

是否开启查看LivePhoto功能呢 - 默认开启
lookLivePhoto;

是否一开始就进入相机界面
goCamera;

最大选择数 默认10 - 建议必填
maxNum;

图片最大选择数 默认9 - 建议必填
photoMaxNum;

视频最大选择数  默认1
videoMaxNum;

图片和视频是否能够同时选择 默认支持
selectTogether;

相册列表每行多少个照片 默认4个
rowCount;
```

- Demo1
```objc
// 懒加载 照片管理类
- (HXPhotoManager *)manager
{
    if (!_manager) {
        _manager = [[HXPhotoManager alloc] initWithType:HXPhotoManagerSelectedTypePhotoAndVideo];
    }
    return _manager;
}

// 照片选择控制器
HXPhotoViewController *vc = [[HXPhotoViewController alloc] init];
vc.delegate = self;
vc.manager = self.manager; 
[self presentViewController:[[UINavigationController alloc] initWithRootViewController:vc] animated:YES completion:nil];

// 通过 HXPhotoViewControllerDelegate 代理返回选择的图片以及视频
- (void)photoViewControllerDidNext:(NSArray *)allList Photos:(NSArray *)photos Videos:(NSArray *)videos Original:(BOOL)original

// 点击取消
- (void)photoViewControllerDidCancel

```
- Demo2
```objc
// 懒加载 照片管理类
- (HXPhotoManager *)manager
{
    if (!_manager) {
        _manager = [[HXPhotoManager alloc] initWithType:HXPhotoManagerSelectedTypePhotoAndVideo];
    }
    return _manager;
}

self.navigationController.navigationBar.translucent = NO;
self.automaticallyAdjustsScrollViewInsets = YES;

HXPhotoView *photoView = [[HXPhotoView alloc] initWithFrame:CGRectMake((414 - 375) / 2, 100, 375, 400) WithManager:self.manager];
photoView.delegate = self;
photoView.backgroundColor = [UIColor whiteColor];
[self.view addSubview:photoView];

// 通过 HXPhotoViewDelegate 代理返回 选择、移动顺序、删除之后的图片以及视频
- (void)photoViewChangeComplete:(NSArray *)allList Photos:(NSArray *)photos Videos:(NSArray *)videos Original:(BOOL)isOriginal

// 当 HXPhotoView 更新frame改变大小时
- (void)photoViewUpdateFrame:(CGRect)frame WithView:(UIView *)view

```
## 六.  更多 

- 如果您发现了bug请尽可能详细地描述系统版本、手机型号和复现步骤等信息 提一个issue.

- 如果您有什么好的建议也可以提issue,大家一起讨论一起学习进步...

- 具体代码请下载项目  如果觉得喜欢的能给一颗小星星么!  ✨✨✨
 
- QQ : 294005139<a target="_blank" href="http://wpa.qq.com/msgrd?v=3&uin=294005139&site=qq&menu=yes"><img border="0" src="http://wpa.qq.com/pa?p=2:294005139:52" alt="点击这里给我发消息" title="点击这里给我发消息"/></a>
  
- [有兴趣可以加下刚刚创建的QQ群:531895229](//shang.qq.com/wpa/qunwpa?idkey=ebd8d6809c83b4d6b4a18b688621cb73ded0cce092b4d1f734e071a58dd37c26) 
