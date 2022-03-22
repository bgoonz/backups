# Practical JavaScript Accessibility - SitePoint

[https://www.sitepoint.com/practical-javascript-accessibility/](https://www.sitepoint.com/practical-javascript-accessibility/)

This article will show you some simple things you can do *right now*, to make your JavaScript more accessible. This is not bleeding-edge technology, but stuff we've been doing for years. This post expands on our introductory article, "[JavaScript Accessibility 101](https://www.sitepoint.com/javascript-accessibility-101/)."

## Three Core Principles

JavaScript accessibility comes down to three core principles:

- All JavaScript functionality must take a form that can be interpreted as text.
- All JavaScript functionality must be accessible to the keyboard.
- Time-based activity in JavaScript should be user-controllable, unless that would change its meaning.

Let's take each of those principles, and look at some of the practical stuff we can do to make it happen.

## Text Interpretation

The point of this principle is to represent information as text which has **meaningful structure**, that can be programatically determined. Solid element semantics should be the basis of all interactive content, but this is particularly true with assistive technologies.

A sighted user isn't always affected by semantics – a menu is a menu because it looks like a menu, whether it's built from a list or `<div>`s. But a blind user can only understand what their screenreader can interpret – a menu is a menu because it's a hierarchy of structured links. If we were building a tab-box, for example, it might look like the following example. Notice how various semantic tags are used.

```
<div class="box">
  <section class="panel">
    <h3 class="tab" tabindex="0">Section 1</h3>
    <p class="content">This is the content for Section 1</p>
  </section>
  <section class="panel">
    <h3 class="tab" tabindex="0">Section 2</h3>
    <p class="content">This is the content for Section 2</p>
  </section>
</div>
```

It's also important to make information programatically accessible. This means using standard DOM functions to add new content to the page, rather than using `document.write()` or `innerHTML`.

`innerHTML` is undeniably convenient, and usually much faster than adding new content node-by-node. The problem with `innerHTML` is that browsers often change the markup, so the resulting DOM is different from what you specified. In some rare cases, content added this way doesn't appear in the DOM at all.

To fix this problem, add the HTML via an intermediate, non-appended element as shown below. To use this function, pass it an HTML string and a target element reference. The function creates a virtual DOM then appends its node(s) to the target.

```
function appendHTML(target, html)
{
  var fragment = document.createElement('div');
  fragment.innerHTML = html;

  while(fragment.hasChildNodes())
  {
    target.appendChild(fragment.firstChild);
  }

  return target;
}
```

## Keyboard Accessibility

When making interactive content accessible to the keyboard, stick to a core set of keys: Tab, Enter, the four Arrow Keys, and Escape. These keys should be used unmodified, i.e. without Shift or other modifier keys having to be held down. If you really need to use other keys or modifier keystrokes, you should provide instructions to the user. Alt combinations are still best avoided though, because they're used for native menu shortcuts.

Most keys also have a default browser action, and it's sometimes necessary to block the default, to prevent a behavioural conflict. For example, when using the Up-Arrow and Down-Arrow keys in a dropdown menu, you wouldn't want them to scroll the page at the same time. The standard way to do this is to use `preventDefault()`, as in this example, taken from a menu script:

```
menu.addEventListener('keydown', function(e)
{
  if(/^(3[789]|40)$/.test(e.keyCode.toString()))
  {
    switch(e.keyCode)
    {
      case 37:
        //... handle left-arrow
        break;
      case 38:
        //... handle up-arrow
        break;
      case 39:
        //... handle right-arrow
        break;
      case 40:
        //... handle down-arrow
        break;
    }

    e.preventDefault();
  }
}, false);
```

If the `keyCode` matches an arrow key, the function handles the key as applicable and then calls `preventDefault()`. If any other key is pressed, the event is ignored, keeping the default behavior. Be careful to ***never*** block the Tab key, or you'll trap the user focus!

Note that the example above uses `keydown` rather than `keypress`, because most browsers don't (and shouldn't) fire the `keypress` event for control keys. The `keydown` event also fires continually if the key is held down, so there may be situations where you prefer to use `keyup` instead – which doesn't repeat, but can't block default actions.

Another important consideration is making sure we maintain a **logical content-order**. For example, when rich tooltips are used, they must be inserted directly after the element that triggered them, so you can Tab to them, and so that screenreaders read them next. For example, a simple tooltip might look something like this:

A rich tooltip positioned above the linked-term.

You can see how the main tooltip text has brackets around it, while the links at the bottom have square-brackets and a delimiting pipe-symbol. The text is also wrapped in `<em>` to add semantic emphasis. When CSS is disabled the content looks like this:

The same tooltip viewed without CSS, showing the explanation as parenthesised text.

Here's the HTML for that example:

```
<blockquote>
  <p>
    Assistive technologies can derive information
    from their attributes and text; for example, a
    dynamic menu would be made using links organised
    into nested lists, in which the menu levels are
    denoted by the hierarchy, and by the use of
    <span id="context">
      <a href="http://www.maxdesign.com.au/2006/01/17/about-structural-labels/"
         title="descriptive headings used to indicate the main components of a web page, such as global site navigation, local navigation and footer information">
        structural labels
      </a>
    </span>
    around each top-level link.
  </p>
</blockquote>
```

The `<span>` around the link provides an insertion target, so the tooltip can be added directly after the link; it also provides a relative context for the tooltip's absolute positioning:

```
#context
{
  position:relative;
}
#context > span.tooltip
{
  position:absolute;
  bottom:1.7em;
  right:0;
}

#context > span.tooltip
{
  width:18em;
  padding:6px 8px;
  white-space:normal;
  border:1px solid #555;
  font:normal normal normal 0.85em/1.4 arial,sans-serif;
  text-align:right;
  background:#ffd;
  box-shadow:1px 2px 3px -1px rgba(0,0,0,0.5);
}
#context > span.tooltip > em
{
  display:block;
  padding:4px 4px 8px 4px;
  text-align:left;
  font-style:normal;
}
```

Here's the JavaScript for that example:

```
var
infotext,
tooltip = null,
context = document.getElementById('context'),
trigger = context.getElementsByTagName('a').item(0);

trigger.addEventListener('click', function(e)
{
  if(tooltip === null)
  {
    infotext = trigger.getAttribute('title');
    trigger.removeAttribute('title');

    tooltip = document.createElement('span');
    tooltip.className = 'tooltip';

    var info = tooltip.appendChild(document.createElement('em'));
    info.appendChild(document.createTextNode(' (' + infotext + ') '));

    tooltip.appendChild(document.createTextNode('[ '));

    var more = tooltip.appendChild(document.createElement('a'));
    more.setAttribute('href', trigger.getAttribute('href'));
    more.appendChild(document.createTextNode('reference'));

    tooltip.appendChild(document.createTextNode(' | '));

    var google = tooltip.appendChild(document.createElement('a'));
    google.setAttribute('href', 'http://www.google.com/search?q=Structural+Labels');
    google.appendChild(document.createTextNode('search'));

    tooltip.appendChild(document.createTextNode(' ]'));

    tooltip = context.appendChild(tooltip);
  }
  else
  {
    trigger.setAttribute('title', infotext);

    context.removeChild(tooltip);
    tooltip = null;
  }

  e.preventDefault();
}, false);
```

`preventDefault()` is used in this case to stop the link from being followed when it's clicked to trigger (or remove) the tooltip. This is why the tooltip also includes the original reference link, so there's no loss of content compared with the static markup.

## Control Over Time-based Activity

The most common time-based activity that JavaScript is used for is content animation. It is important to ensure that the animation has a pause button, and ideally, a means to view the content fully-revealed. For example, a scrolling news-ticker could be built like this:

```
<div id="ticker">
  <ol>
    <li><a href="...">This is the first news item</a></li>
    <li><a href="...">This is the second news item</a></li>
  </ol>
</div>
<div id="buttons">
  <button id="pause-button" type="button">Pause</button>
  <button id="expand-button" type="button">Expand</button>
</div>
```

The markup is an *ordered* list because news-items are usually ordered in time, with the latest headlines at the top. The CSS for that example would be something like this:

```
#buttons
{
  display:none;
}
#buttons.script-enabled
{
  display:block;
}

#ticker.script-enabled,
#ticker.script-enabled > ol
{
  position:relative;
}

#ticker
{
  white-space:nowrap;
  overflow:hidden;
  margin:5px 0 0 0;
  padding:5px 10px;
  border:2px solid #555;
  background:#f2f2f2;
}
#ticker.script-enabled > ol,
#ticker.script-enabled > ol > li
{
  margin:0;
  padding:0;
  list-style-type:none;
}
#ticker.script-enabled > ol > li
{
  display:inline-block;
  margin-right:20px;
}

#ticker.script-enabled.expanded,
#ticker.script-enabled.expanded > ol
{
  position:static;
}
#ticker.script-enabled.expanded
{
  white-space:normal;
  overflow:hidden;
}
```

While the following JavaScript brings it all together:

```
var
container = document.getElementById('ticker'),
list = container.getElementsByTagName('ol').item(0),
buttons = document.getElementById('buttons'),
pauser = document.getElementById('pause-button'),
expander = document.getElementById('expand-button');

buttons.className = 'script-enabled';
container.className = 'script-enabled';

var scrollwidth = 0;
var items = list.getElementsByTagName('li');
for(var i = 0; i < items.length; i ++)
{
  scrollwidth += items[i].offsetWidth + 20;
}

var scrollstart = container.offsetWidth;
list.style.left = scrollstart + 'px';

var
timer = null,
moving = false,
scrolloffset = scrollstart;

function pause()
{
  moving = false;
  window.clearInterval(timer);
  timer = null;
}

function resume()
{
  moving = true;
  timer = window.setInterval(function()
  {
    scrolloffset -= 5;
    if(scrolloffset < (0 - scrollwidth))
    {
      scrolloffset = scrollstart;
    }
    list.style.left = scrolloffset + 'px';
  }, 100);
}

pauser.addEventListener('click', function()
{
  if(moving)
  {
    pause();
    pauser.firstChild.nodeValue = 'Resume';
  }
  else
  {
    resume();
    pauser.firstChild.nodeValue = 'Pause';
  }
}, false);

expander.addEventListener('click', function()
{
  pause();
  container.className = 'expanded';
  pauser.parentNode.removeChild(pauser);
  expander.parentNode.removeChild(expander);
}, false);

resume();
```

An important thing to note is that the `buttons` container is hidden by default, then only displayed when a `script-enabled` class is added. This is so that when the page is viewed without JavaScript, the user isn't left with buttons that don't do anything.

Similarly, the rules that apply the `overflow` and other properties that convert the list into a horizontal scroller, only come into effect when the `script-enabled` class is added. This is necessary because those styles obscure most of the content by default, so we need to ensure that doesn't happen unless the scripting is there.

The `Pause` button stops the scrolling so you can read each item in your own time, then changes to `Resume` so you can start it again. The `Expand` button also stops the scrolling but then adds an `expanded` class which overrides the `overflow` and other layout styles. This makes the content turn back into a static list of links.

## Conclusion

This has been a whirlwind tour of practical JavaScript accessibility! But if there's one thing I'd like you to take away, it's that **JavaScript accessibility isn't hard**. It only takes a little attention to the three core principles. Next time I'll be moving on to more advanced techniques like roving `tabindex`, drag and drop, and accessible Ajax!

[James Edwards](https://www.sitepoint.com/author/brothercake/)
James is a freelance web developer based in the UK, specialising in JavaScript application development and building accessible websites. With more than a decade's professional experience, he is a published author, a frequent blogger and speaker, and an outspoken advocate of standards-based development.
