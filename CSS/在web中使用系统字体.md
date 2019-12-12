# 在web中使用系统字体
[Using UI System Fonts In Web Design: A Quick Practical Guide](https://www.smashingmagazine.com/2015/11/using-system-ui-fonts-practical-guide/)

```css
font-family:
/* 1 / -apple-system, BlinkMacSystemFont,
/ 2 / “Segoe UI”, “Roboto”, “Oxygen”, “Ubuntu”, “Cantarell”, “Fira Sans”, “Droid Sans”,
/ 3 */ “Helvetica Neue”, sans-serif;
```

第一组是css属性，映射到系统的字体，这涵盖了很多基础，并且不会被误认为其他东西：
- -apple-system：targets San Francisco in Safari on Mac OS X and iOS, and it targets Neue Helvetica and Lucida Grande on older versions of Mac OS X. It properly selects between San Francisco Text and San Francisco Display depending on the text’s size.
- BlinkMacSystemFont：与 Max OS 上的 Chrome 等效。

第二组用于已知的系统UI字体：
- `Segoe UI` 指向 Windows 和 Windows 系统的手机.
- `Roboto` 指向安卓和较新的Chrome系统。 It is deliberately listed after Segoe UI so that if you’re an Android developer on Windows and have Roboto installed, Segoe UI will be used instead.
- Oxygen targets KDE, Ubuntu targets… well, you can guess, and Cantarell targets GNOME. This is beginning to feel futile because some Linux distributions have many of these fonts.
- Fira Sans targets Firefox OS.
- Droid Sans targets older versions of Android.
- Note that we don’t specify San Francisco by name. On both iOS and Mac OS X, San Francisco isn’t obviously accessible, but rather exists as a “hidden” font.
We also don’t specify San Francisco using .SFNSText-Regular, the internal PostScript name for San Francisco on Mac OS X. It only works in Chrome and is less versatile than BlinkMacSystemFont.

第三组是后备字体：
- Helvetica Neue targets pre-El Capitan versions of Mac OS X. It is listed close to the end because it’s a popular font on other non-El Capitan computers.
- sans-serif is the default sans-serif fallback font.
