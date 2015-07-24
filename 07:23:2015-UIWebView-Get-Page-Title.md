#UIWebView获取网页标题
```objective-c

- (void)webViewDidFinishLoad:(UIWebView *)webView

{

    [webView stringByEvaluatingJavaScriptFromString:@"document.title"];
    
}    

```