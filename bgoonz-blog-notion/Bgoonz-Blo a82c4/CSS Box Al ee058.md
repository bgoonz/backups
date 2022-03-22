# CSS Box Alignment Module Level 3

[https://www.w3.org/TR/css-align-3/#gaps](https://www.w3.org/TR/css-align-3/#gaps)

![CSS%20Box%20Al%20ee058/self-v-context-start-tb.svg](CSS%20Box%20Al%20ee058/self-v-context-start-tb.svg)

![CSS%20Box%20Al%20ee058/self-v-context-self-start-tb.svg](CSS%20Box%20Al%20ee058/self-v-context-self-start-tb.svg)

inline-axis 'start' alignment with LTR context

![CSS%20Box%20Al%20ee058/distribute.svg](CSS%20Box%20Al%20ee058/distribute.svg)

The [distributed alignment](https://www.w3.org/TR/css-align-3/#distributed-alignment) values

![CSS%20Box%20Al%20ee058/scroll-align-padding.jpg](CSS%20Box%20Al%20ee058/scroll-align-padding.jpg)

Issue: Replace this image with a proper SVG.

![CSS%20Box%20Al%20ee058/scroll-align-overflow.jpg](CSS%20Box%20Al%20ee058/scroll-align-overflow.jpg)

Overflow is not part of the [alignment subject](https://www.w3.org/TR/css-align-3/#alignment-subject), even for a [scroll container](https://www.w3.org/TR/css-overflow-3/#scroll-container). 
 Replace this image too.

A box's   is aligned to the corresponding edge of its  and it has a  for a "first"  when, in the relevant axis:

- 
    
    There are no   and the relevant  either is or aligns identically to  or ; or
    
- 
    
    There is only an  -edge , which absorbs any positive free space and disables the effects of any ,  its  does not overflow its  under circumstances that would cause it to effectively end-align instead (such as having a  with an opposite ).
    

A box's   is aligned to the corresponding edge of its  and it has a  for a "last"  when, in the relevant axis:

- 
    
    There are no   and the relevant  either is or aligns identically to   its self-alignment is what would result from an  ; or
    
- 
    
    There is only an  -edge , which absorbs any positive free space and disables the effects of any   its  does not overflow its  under circumstances that would cause it to effectively start-align instead.
    

![CSS%20Box%20Al%20ee058/place-content-abspos.svg](CSS%20Box%20Al%20ee058/place-content-abspos.svg)

Instead of always sizing within the available space between the [inline-start](https://www.w3.org/TR/css-writing-modes-4/#inline-start) static position and the [inline-end](https://www.w3.org/TR/css-writing-modes-4/#inline-end) [containing block](https://www.w3.org/TR/css-display-3/#containing-block) edge as specified in [[CSS2]](https://www.w3.org/TR/css-align-3/#biblio-css2), an absolutely-positioned element with [auto](https://www.w3.org/TR/css-position-3/#valdef-top-auto) insets will be sized with reference to the [static position rectangle](https://www.w3.org/TR/css-align-3/#static-position-rectangle)'s edge(s) *most appropriate* to its specified [self-alignment](https://www.w3.org/TR/css-align-3/#self-align).

![CSS%20Box%20Al%20ee058/gutters-gaps.svg](CSS%20Box%20Al%20ee058/gutters-gaps.svg)
