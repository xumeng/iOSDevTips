# iOS解决UIBarButtonItem customView位置问题

iOS中在使用customView作为UIBarButtonItem时，位置经常严重不靠边，可以使用下述解决方案，原理为设置一个空白项。

```
UIBarButtonItem *rightItem = [[UIBarButtonItem alloc] initWithCustomView:rightBarView];
    UIBarButtonItem *spacer = [[UIBarButtonItem alloc] initWithBarButtonSystemItem:UIBarButtonSystemItemFixedSpace target:nil action:nil];
    spacer.width = -10; //(custom size)
    self.navigationItem.rightBarButtonItems = @[spacer, rightItem];
```
