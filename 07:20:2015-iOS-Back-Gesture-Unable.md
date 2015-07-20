##处理UINavigationController中interactivePopGestureRecognizer手势问题
自定义UINavigationController中的UIBarButtonItem后，右滑返回手势失效。

一般会直接对`interactivePopGestureRecognizer`的`Delegate`赋值即可。
但是经过测试后，还是会发现各种问题。
这里我们给出的解决方案如下：
在BaseViewController里开启或禁用： 
```objective
-(void)viewDidAppear:(BOOL)animated 
{ 
    [super viewDidAppear:animated]; 
    if ([self.navigationController respondsToSelector:@selector(interactivePopGestureRecognizer)]) { 
        if ([self.navigationController.viewControllers count] > 1) { 
            self.navigationController.interactivePopGestureRecognizer.enabled = YES; 
            self.navigationController.interactivePopGestureRecognizer.delegate = self; 
        }else{ 
            self.navigationController.interactivePopGestureRecognizer.enabled = NO; 
            self.navigationController.interactivePopGestureRecognizer.delegate = nil; 
        } 
    } 
}
```