# css居中

> 绝对定位 + transform

```CSS
.center {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```

> 偏移50% + 负margin值

```CSS
.center {
    position: absolute;
    height: 100px;
    width: 100px;
    top: 50%;
    left: 50%;
    margin-top: -50px;
    margin-left: -50px;
}
```