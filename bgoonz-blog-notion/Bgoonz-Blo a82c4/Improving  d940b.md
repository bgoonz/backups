# Improving Usability With Extra Navigation Keys - SitePoint

[https://www.sitepoint.com/improving-usability-with-extra-navigation-keys/](https://www.sitepoint.com/improving-usability-with-extra-navigation-keys/)

When handling keyboard events in JavaScript, most scripts and applications tend to stick to the basic range of keys that provide core accessibility — the **Tab** key for serial navigation, the **Arrow** keys for drilling-down or for two-dimensional navigation, and the **Enter** and **Space** keys for clicking and selecting things.

This is all good, but there are some other common keys you might consider as well, that can significantly improve usability by providing more control — the **Page-up** and **Page-down** keys can be used for fast navigation over large groups of data, while the **Home** and **End** keys can be used as shortcuts to the first and last value.

Most Windows keyboards have dedicated keys for these, but they also work on the Mac via modifier combinations. For example, on my Macbook there's an extra **fn** (function) key, and this is used in combination with the four Arrow keys (e.g. **fn+up** for Page-up, and **fn+left** for Home).

## Slider controls

Slider controls are a perfect example of where these keys can be used to good effect. The Arrow keys are typically used to increment and decrement a slider by a single value, but we can also use the Page-up and Page-down keys to change the value by a larger proportion, as well as the Home and End keys to set the slider to its minimum and maximum.

The following code is an excerpt from a video player's seek slider:

```
switch(true)
{
  case (e.keyCode == 38 || e.keyCode == 39) :

    if(++value > max)
    {
      value = max;
    }
    break;

  case (e.keyCode == 37 || e.keyCode == 40) :

    if(--value < 0)
    {
      value = 0;
    }
    break;

  case (e.keyCode == 33) :

    if((value = value + Math.round(max / 10)) > max)
    {
      value = max;
    }
    break;

  case (e.keyCode == 34) :

    if((value = value - Math.round(max / 10)) < 0)
    {
      value = 0;
    }
    break;

  case (e.keyCode == 36) :

    value = 0;
    break;

  case (e.keyCode == 35) :

    value = (max - 1);
    break;
}
```

The `switch` statement adjusts the slider's value (and consequently, the video's seeking position) according to the event `keyCode` — by a single step for the Arrow keys, by 10% for the Page-up and Page-down keys, or to the start or end of the video for the Home and End keys, respectively. Where applicable, the value changes are constrained so they don't exceed their limits (e.g. so you can't seek past the end).

In this case, the slider was written from scratch to include these extra keys, but this is the kind scripting enhancement that's easy to retrofit, because all it requires is additional conditions for key-handling code which the script must already contain.

## Handling the key events

For reference, here are all the event `keyCode` values used in the previous example:

- `33` = Page-up
- `34` = Page-down
- `35` = End
- `36` = Home
- `37` = Left-arrow
- `38` = Up-arrow
- `39` = Right-arrow
- `40` = Down-arrow

Handling these keys is no different than handling any other navigation keys; if you'd like more information about that, check out my earlier article: **[Practical JavaScript Accessibility](https://www.sitepoint.com/practical-javascript-accessibility/)**.

The only thing I would pause to mention explicitly here, is that **navigational keys can only be handled with `keydown` and `keyup` events**, and *not* with `keypress` events (which are only used for keys that actually insert a character, such as letters and numbers). The `keydown` events can also be used to block default actions, which is often necessary when scripting with navigational keys, but make sure you only do this when the **focus is inside your widget**, so you don't end up blocking them all the time.

## Interpreting key behaviours

When using these extra keys — or any keys for that matter — it's important to stop and consider what the keystrokes will *mean* in the context of your script. Although we have a clear idea of what, for example, the Home key means in the context of a text-editor or word-processor, it may not be quite so obvious in a different behavioural context.

The slider is a good example because it's obvious what they should be used for, and I think we can take that specific example to derive a more general set of principles:

- Home means minimum, start or first
- End means maximum, end or last
- Page-up means increment by a chunk, or move to the next division or group
- Page-down means decrement by a chunk, or move to the previous division or group

So maybe, for example, in the context of a mail application's message view, the Home key might jump to the top of the list, and the End key to the end. Or in the context of a music player's volume control, Page-up might increase the volume by a quarter or a half, while Page-down does the opposite.

You'll have the best idea of how such keys relate to your own application. There are no hard and fast rules for this, and no absolute conventions, it's just a case of thinking about what existing keyboard actions achieve, and how these extra keystrokes might be used to make that easier or quicker.

[James Edwards](https://www.sitepoint.com/author/brothercake/)
James is a freelance web developer based in the UK, specialising in JavaScript application development and building accessible websites. With more than a decade's professional experience, he is a published author, a frequent blogger and speaker, and an outspoken advocate of standards-based development.
