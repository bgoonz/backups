# Accessibility in Modern Interfaces - SitePoint

[https://www.sitepoint.com/accessibility-in-modern-interfaces/](https://www.sitepoint.com/accessibility-in-modern-interfaces/)

Some of the things being done with JavaScript today are truly amazing. The Internet itself is still young, yet it's been through several evolutions in its short history – most significantly perhaps, is the explosion of incredible Web applications that came in the wake of AJAX. There was a loser though, and that was **accessibility**. But, now we've reached a point where accessibility is catching up, thanks to the development of the Web Accessibility Initiative's Accessible Rich Internet Applications (WAI ARIA).

## The Principles of ARIA

The core of the ARIA specification is a set of **attribute semantics**, for making interactive content accessible to assistive technologies. After all, how is a screenreader user supposed to know what the following markup represents?

```
<label>
  <button>25%</button>
</label>
```

ARIA adds vital role and state information that makes things comprehensible, as shown below.

```
<label>
  <button role="slider"
    aria-orientation="horizontal"
    aria-valuemin="0"
    aria-valuemax="100"
    aria-valuenow="25"
    aria-valuetext="25%">25%</button>
</label>
```

ARIA makes it possible to build dynamic interfaces, custom widgets, and all of the various components of modern Web applications, in a way that's accessible to screenreaders and other access technologies, using data attributes that fall into the following three broad groups.

- Attributes that describe the **role** of an element, like `dialog`, `progressbar`, or `slider`.
- Attributes that describe the **properties** of an element, like `aria-required`, `aria-multiselectable`, or `aria-valuemax`.
- Attributes that describe the **states** of an element, like `aria-selected`, `aria-hidden`, or `aria-valuenow`.

## ARIA's Role

For many of you, it's likely that your greatest familiarity with ARIA is with **landmark roles**, which can be used in any flavour of HTML to describe the main content blocks:

```
<div role="main" id="content"></div>
<div role="complementary" id="sidebar"></div>
<div role="navigation" id="menu"></div>
<div role="contentinfo" id="footer"></div>
```

In HTML5, landmark roles map to primary structural elements:

```
<article role="main" id="content"></article>
<aside role="complementary" id="sidebar"></aside>
<nav role="navigation" id="menu"></nav>
<footer role="contentinfo" id="footer"></footer>
```

Using landmark roles in addition to HTML5 structural elements is an example of **bridging technology** – an interim solution for the benefit of current generation assistive technologies, which support ARIA roles, but don't yet understand HTML5 semantics. ARIA was specifically designed to provide this kind of interim solution, and any of the current ARIA attributes may eventually be replaced with something better.

Formal specifications like HTML5 take a very long time to develop – significantly longer than developers take to come up with new ideas. Standards can only react to what was being done *last year*, while forward-thinking developers are far more interested in what we're doing *right now*. ARIA can bridge this gap.

## Keyboard Accessible Drag and Drop

Now we'll move on to an example which uses drag and drop to show how ARIA can add accessible semantics to common scripted behaviours. It wasn't very long ago that drag and drop was thought to be fundamentally inaccessible – an inherently mouse-based interaction that couldn't be translated to the keyboard. But, early innovations like my [dbx library](http://www.brothercake.com/site/resources/scripts/dbx/) showed that it could be done by thinking about what drag and drop actions are actually for, and then providing a keyboard interface that achieves the same result.

What we refer to as drag and drop is actually two different kinds of interaction. The first is content reordering, where elements can be moved up and down to sort them. The second is a grab and move action like dragging files between folders. The dbx library was designed with the first interaction in mind, while the ARIA specification is focused on the second.

In the following demo, drag and drop is implemented in three different ways – using the `draggable` attribute and its associated events (which are not keyboard accessible), supplementing that with mouse events for browsers that don't support `draggable`, and then adding key events to make it accessible to keyboard users.

- **[ARIA-enabled drag and drop demo](https://github.com/jsprodotcom/source/blob/master/accessibility-in-modern-interfaces.zip)**

The keyboard interactions are based on those recommended in the [ARIA authoring practices](https://www.w3.org/WAI/PF/aria-practices/#dragdrop):

1. Use Tab to move between items.
2. Press Space to select an item.
3. Use Tab to move between drop targets.
4. Press Enter or Ctrl+M to move the selected item into the selected drop target.
5. Or, press Esc to cancel and unselect the item.

The Space key does make sense, because that's already used to select radio buttons and checkboxes. And, the Ctrl+M shortcut is unintuitive and conflicts with the Minimize to Dock shortcut in Mac OS X. It seems to me that pressing Enter is far more obvious and available, so to compromise, both have been implemented. The demo also contains **roving `tabindex`** – using dynamic `tabindex` values to place elements in or out of the native tab order, depending on the current state of the interface. Each of the drop targets in the demo is a list, and each of the draggable objects is a list item. So, in its default state, only the items are in the tab-order:

```
<ul>
  <li tabindex="0">1</li>
  <li tabindex="0">2</li>
  <li tabindex="0">3</li>
</ul>

<ul>
  <li tabindex="0">4</li>
</ul>
```

Once you've selected an item, the lists need to be in the tab order so you can select one as a drop target. But, at this point the other items don't need to be in the tab order anymore, because you can't select another item until you're done with the current one. In addition to setting `tabindex="0"` on the parent lists, we also remove it from the individual items, and that takes them out of the tab order altogether. This is a simple thing to do, but it means the user only needs a couple of key presses to find the target they want, instead of having to tab past all the other items first!

```
<ul tabindex="0">
  <li>1</li>
  <li>2</li>
  <li>3</li>
</ul>

<ul tabindex="0">
  <li>4</li>
</ul>
```

The principle of roving `tabindex` can be used almost anywhere, making it so that the only elements in the tab order at any give time, are those the user can interact with ***right now***.

### Adding ARIA Semantics

Once we have keyboard support, the only other thing we need to do for assistive technologies, is to add two ARIA attributes – `aria-grabbed` and `aria-droptarget`. The first is a Boolean flag that indicates whether an element has been selected for dragging, while the second is a Boolean flag that indicates whether an element is now a drop target. So, in its default state, the items are not grabbed and there are no active drop targets:

```
<ul aria-dropeffect="none">
  <li aria-grabbed="false">1</li>
  <li aria-grabbed="false">2</li>
  <li aria-grabbed="false">3</li>
</ul>

<ul aria-dropeffect="none">
  <li aria-grabbed="false" tabindex="0">4</li>
</ul>
```

Once you've selected an item, it becomes grabbed, and the parent lists become drop targets.

```
<ul aria-dropeffect="move">
  <li aria-grabbed="true">1</li>
  <li aria-grabbed="false">2</li>
  <li aria-grabbed="false">3</li>
</ul>

<ul aria-dropeffect="move">
  <li aria-grabbed="false">4</li>
</ul>
```

To illustrate these changes, the demo includes a version with floating tooltips, that shows how the attributes change with each interaction. In this case, the `aria-droptarget` value is `move`, which means that the selected item will be moved from one target to another. Other possible values include `copy` to create a copy, and `link` to create a reference or shortcut.

## ARIA Doesn't Do Anything

Although there are different values for the `aria-droptarget` attribute, all they actually provide is *information* for assistive technologies, so they can tell the user what will happen. The attribute itself doesn't do anything at all. So, ARIA doesn't change how we build Web applications, it simply provides semantic attributes for describing them.

Another prime example of where ARIA can (and should) be used, is when making dynamic updates to a page via AJAX, which pre-ARIA screenreaders couldn't understand at all. Screenreaders use a kind of **virtual buffer**, which is a temporary snapshot of the current page that the device actually reads. When AJAX is used to load new content and add it to the DOM, the virtual buffer is *not* updated, and that's why the first generation of AJAX apps were inaccessible to screenreaders.

ARIA solves this problem with its `aria-live` attribute, which can be used to indicate when content changes, and how significant the change is. For example, if you set `aria-live="assertive"` on an element and then update its content, the change in content will be immediately communicated to the user. Or, if you set `aria-live="polite"`, it will be communicated when convenient for the user. These priorities are based on what the user is currently doing, so an `assertive` change would interrupt them immediately, while a `polite` change would wait until they're not busy. It's up to the screenreader to determine how those priorities manifest in the user's workflow.

From a developer's point of view, you simply have to think about how important the update is. The `polite` value would be used for most cases where content changes in the background, such as live news headlines or sports results. The `assertive` value would be used for things that require immediate attention, like form validation errors.

## Conclusion

ARIA isn't perfect, and has yet to fully implemented, but nevertheless I recommend you try to use it whenever applicable. All custom widgets and Web applications should have at least basic ARIA support, because it makes the difference between some accessibility and none at all.

If you'd like to find out more about using WAI ARIA, I'd recommend the [Introduction to WAI ARIA](http://dev.opera.com/articles/view/introduction-to-wai-aria/). Gez Lemon's [JuicyStudio](http://juicystudio.com/) and Steve Faulkner's [Paciello Group Blog](http://www.paciellogroup.com/blog/) are also useful bookmarks. Eventually, you'll find yourself reading the ARIA [specification](https://www.w3.org/TR/wai-aria/) and [authoring practices](https://www.w3.org/WAI/PF/aria-practices/) (good luck with that!)

You can also download the demo from this article:

- **[Download the ARIA-enabled drag and drop demo](https://github.com/jsprodotcom/source/blob/master/accessibility-in-modern-interfaces.zip)**

[James Edwards](https://www.sitepoint.com/author/brothercake/)
James is a freelance web developer based in the UK, specialising in JavaScript application development and building accessible websites. With more than a decade's professional experience, he is a published author, a frequent blogger and speaker, and an outspoken advocate of standards-based development.
