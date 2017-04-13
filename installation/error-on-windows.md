# windows更新报错

## 背景

gitbook的新版本，在windows下有个bug，当文件内容发生更新时，gitbook报错然后退出：

```bash
Serving book on http://localhost:4000
Restart after change in file installation\error-on-windows.md

Stopping server
events.js:160
      throw er; // Unhandled 'error' event
      ^

Error: EPERM: operation not permitted, lstat 'C:\work\code\leaning\leaning-gitbook\_book'
    at Error (native)
```

导致在windows下更新内容时没法实时看到效果，除非每个更新都重新运行一次 `gitbook serve`。

## 信息

gitbook 官方已有bug，存在半年了，一直没有fix：

- [git serve can't restart when file changes](https://github.com/GitbookIO/gitbook/issues/1379)
- [gitbook-cli crashes with EPERM: operation not permitted on windows](https://github.com/GitbookIO/gitbook-cli/issues/51)

## 解决方法

在官方bugfix之前，暂时只能回避：

1. 不要在 windows 下使用gitbook：linux没有这个问题
2. 不是办法的办法：

	新建一个 `run.bat` ，内容如下：

    ```bash
    @Echo off
    :Start
    call gitbook serve
    goto Start
    ```

	每次崩溃之后立即重新启动一次，凑合着用吧。
