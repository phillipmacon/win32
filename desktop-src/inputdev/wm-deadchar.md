---
title: WM_DEADCHAR message (Winuser.h)
description: Posted to the window with the keyboard focus when a WM\_KEYUP message is translated by the TranslateMessage function.
ms.assetid: ada9a61c-dabf-447b-ae13-91803c097f0d
keywords:
- WM_DEADCHAR message Keyboard and Mouse Input
topic_type:
- apiref
api_name:
- WM_DEADCHAR
api_location:
- Winuser.h
api_type:
- HeaderDef
ms.topic: reference
ms.date: 05/31/2018
---

# WM\_DEADCHAR message

Posted to the window with the keyboard focus when a [**WM\_KEYUP**](wm-keyup.md) message is translated by the [**TranslateMessage**](/windows/desktop/api/winuser/nf-winuser-translatemessage) function. **WM\_DEADCHAR** specifies a character code generated by a dead key. A dead key is a key that generates a character, such as the umlaut (double-dot), that is combined with another character to form a composite character. For example, the umlaut-O character ( ) is generated by typing the dead key for the umlaut character, and then typing the O key.


```C++
#define WM_DEADCHAR                     0x0103
```



## Parameters

<dl> <dt>

*wParam* 
</dt> <dd>

The character code generated by the dead key.

</dd> <dt>

*lParam* 
</dt> <dd>

The repeat count, scan code, extended-key flag, context code, previous key-state flag, and transition-state flag, as shown in the following table.



| Bits  | Meaning                                                                                                                                                                                                                                                               |
|-------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0-15  | The repeat count for the current message. The value is the number of times the keystroke is autorepeated as a result of the user holding down the key. If the keystroke is held long enough, multiple messages are sent. However, the repeat count is not cumulative. |
| 16-23 | The scan code. The value depends on the OEM.                                                                                                                                                                                                                          |
| 24    | Indicates whether the key is an extended key, such as the right-hand ALT and CTRL keys that appear on an enhanced 101- or 102-key keyboard. The value is 1 if it is an extended key; otherwise, it is 0.                                                              |
| 25-28 | Reserved; do not use.                                                                                                                                                                                                                                                 |
| 29    | The context code. The value is 1 if the ALT key is held down while the key is pressed; otherwise, the value is 0.                                                                                                                                                     |
| 30    | The previous key state. The value is 1 if the key is down before the message is sent, or it is 0 if the key is up.                                                                                                                                                    |
| 31    | The transition state. The value is 1 if the key is being released, or it is 0 if the key is being pressed.                                                                                                                                                            |

For more detail, see [Keystroke Message Flags](about-keyboard-input.md#keystroke-message-flags).

</dd> </dl>

## Return value

An application should return zero if it processes this message.

## Remarks

The **WM\_DEADCHAR** message typically is used by applications to give the user feedback about each key pressed. For example, an application can display the accent in the current character position without moving the caret.

Because there is not necessarily a one-to-one correspondence between keys pressed and character messages generated, the information in the high-order word of the *lParam* parameter is generally not useful to applications. The information in the high-order word applies only to the most recent [**WM\_KEYDOWN**](wm-keydown.md) message that precedes the posting of the **WM\_DEADCHAR** message.

For enhanced 101- and 102-key keyboards, extended keys are the right ALT and the right CTRL keys on the main section of the keyboard; the INS, DEL, HOME, END, PAGE UP, PAGE DOWN and arrow keys in the clusters to the left of the numeric keypad; and the divide (/) and ENTER keys in the numeric keypad. Some other keyboards may support the extended-key bit in the *lParam* parameter.

## Requirements



| Requirement | Value |
|-------------------------------------|----------------------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows 2000 Professional \[desktop apps only\]<br/>                                               |
| Minimum supported server<br/> | Windows 2000 Server \[desktop apps only\]<br/>                                                     |
| Header<br/>                   | <dl> <dt>Winuser.h (include Windows.h)</dt> </dl> |



## See also

- [**TranslateMessage**](/windows/desktop/api/winuser/nf-winuser-translatemessage)
- [**WM\_KEYDOWN**](wm-keydown.md)
- [**WM\_KEYUP**](wm-keyup.md)
- [**WM\_SYSDEADCHAR**](wm-sysdeadchar.md)
- [Keyboard Input](keyboard-input.md)
- [About Keyboard Input](about-keyboard-input.md)

 

 

