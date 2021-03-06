---
title: AM/PM
version: 1.6.0
signature: |
  // From 2.8.1 onward
  moment.locale('en', {
      meridiem : Function
  });

  // Deprecated in 2.8.1
  moment.lang('en', {
      meridiem : Function
  });
---


If your locale uses 'am/pm', `Locale#meridiem` can be omitted, as those values are the defaults.

If your locale needs any different computation for am/pm, `Locale#meridiem` should be a callback function that returns the correct string based on hour, minute, and upper/lowercase.

```javascript
moment.locale('zh-cn', {
    meridiem : function (hour, minute, isLowercase) {
        if (hour < 9) {
            return "早上";
        } else if (hour < 11 && minute < 30) {
            return "上午";
        } else if (hour < 13 && minute < 30) {
            return "中午";
        } else if (hour < 18) {
            return "下午";
        } else {
            return "晚上";
        }
    }
});
```

Before version **1.6.0**, `Locale#meridiem` was a map of upper and lowercase versions of am/pm.

```javascript
moment.locale('en', {
    meridiem : {
        am : 'am',
        AM : 'AM',
        pm : 'pm',
        PM : 'PM'
    }
});
```

This has been deprecated. The **1.6.0** callback function syntax is now used instead.
