## Box Model

Highlight all the boxes of a webpage with green border

```js
const allElem = document.querySelectorAll("*");
allElem.forEach(el => el.style.border = "2px solid green");
```

![[Pasted image 20240825123453.png]]


The box model comprises several layers, each serving a distinct purpose in the layout of an element:

***content box:***\
This is the area that contains the content of the block.

***padding box:***\
this layer surrounds the content box, providing space around the content.

***border box***:\
This includes the space of the border that encircles both the padding box & the content box.

***margin box***:\
This represents the external space outside the elements border.

### Box Properties

**Box size**
- intrinsic
- restricted

**Box type**
- inline
- block
- anonymous


Box size can be:

***intrinsic:***\
this means the box uses its content to determine the space it occupies.

***restricted:***\
this indicates that the box's size is governed by a set of rules applied to it. It can be:
- explicit *width* & *heights* set via css.
- constraints by parent elements or other boxes through mechanisms like:
	 1. *flex* or *grid* layout system
	 2. *percentage (%)* of the parent size
	 3. The *aspect-ratio* property of images, etc.
	 4. the presence of another children in the DOM tree.


There are several types of boxes:
- *block* level (including, but not restricted by display: block)
- *inline* level
- *anonymous* box


###### Block
- The element is rendered like a block
	- block level element takes 100% of the ==parent== container width
	- the ==height== of the content is equal to the ==intrinsic size==
- The element is rendered from ==top to bottom==.
- Participate in ==block context formatting (BCF)==

![[Pasted image 20240825125527.png]]


###### Anonymous

![[Pasted image 20240825125743.png]]



###### Mathematics of block element

the final width of the box is calculated below:

**box-sizing: content-box**

`width = margin-left + border-left + padding-left + content-width + padding-right + border-right + margin-right`

**box-sizing: border-box**

`width = margin-left + content-width + margin-right`

*the padding & the border is already included in content size.*


![[Pasted image 20240825130615.png]]



###### Inline Elements

The key characteristics of inline elements are:
- they render as a ==string==, flowing from left to right and from ==top to bottom==.
- They participate in an ==inline formatting context (IFC)==
- They generate ==inline-level== boxes.


![[Pasted image 20240825131603.png]]



###### Mathematics of inline elements

- Does not respond to ==width== & ==height== properties. completely ignores them.
- Doesn't react to ==vertical margins== , ignores them
- the height of the inline element is determined by the either ==intrinsic height== or the ==line-height== property.
- inline ==padding== does not alter the ==height== of the inline element.

`width = margin-left + border-left + padding-left + content-width + padding-right + border-right + margin-right`

![[Pasted image 20240825132400.png]]

## Browser Formatting Context

Think of it like a realm, when an element falls into this realm, a particular rules are applied.

for ex:\
if the element falls into the realm the element, then they should only take 100% of the width and it also should render from top to bottom.

![[Pasted image 20240825133142.png]]

we can even create a formatting context within a  formatting context.

The inner formatting context will be completely isolated from the outer formatting context.\
once an element enters into inner formatting context, it wont get affected by outer formatting context.

![[Pasted image 20240825133857.png]]


we can even create new type of formatting context, which we can call inline formatting context.

for ex:\
when elem 3 & 4 enters inline formatting context, it will appear from left to right, and the width should be content's width


![[Pasted image 20240825134227.png]]

###### Formatting context - key ideas

**The key ideas of formatting contexts:**
- ***Isolation***\
	elements within a context are shielded from the rules of external contexts.
- ***scalability***\
	introducing a new ruleset for elements is an simple as creating a new ==context== (ex: flex-box, grid)
- ***predictability***\
	with a strict set of rules, the placement of elements is predictable.


**Formatting context family:**
- flex
- grid
- inline
- block

![[Pasted image 20240825134835.png]]

**Exercise:**\

![[Pasted image 20240825135355.png]]

## Browser Positioning System

**Normal Flow**

this is the natural order of rendering element,\
in rtl languages, 
elements are rendered from top to bottom, from left to right.
and vice-versa.

To remove elements from normal flow using the ==position== property. This allows us to override how the browser positions the element.

![[Pasted image 20240825140130.png]]


###### Static

the positon: static is applied by default.

the browser applies static position to every element, everything is rendered from top to bottom, left to right.

![[Pasted image 20240825140453.png]]




###### relative

The element is positioned according to the normal flow of the document
- **offset** applied relative to itself based on the values of **top**, **right**, **bottom** & **left**.
- The **offset** does not affect the position of any other elements, thus, the space allocated for the element in the page layout remains the same as if the position were **static**.
- This value creates a new **Stacking context** when the value of **z-index** is not auto.

the browser renders the position relative the same as the normal flow, but the final position is determined by the the top ,right, left, and bottom property.

**the change of the position doesn't impact other element.**

the element is removed from the normal flow, thus it doesn't impact other element.

when we apply position relative, we create a new stacking context, a new kind of realm where we put out elements. This element is isolated from the normal flow.

![[Pasted image 20240825141811.png]]



###### Containing block

the containing block is kind of a reference point for the element, how it calculates its position on the screen.

so, for ex:\
for `<html>` the containing block is the browser viewport.

if u apply relative position to div, inside a body, then body is the containing block of div.\
as its the ==closest block-level ancestor== of div.


![[Pasted image 20240825142808.png]]


###### absolute

- the element is **removed from the normal document flow**.
- no space is reserved for the element in the page layout.
- Its **positioned relative** to its closest **positioned ancestor** if one exist. Otherwise, its placed relative to the **initial containing block**.
- final position is determined by the values of **top**, **bottom**, **left**, **right**
- this positioning creates a new **stacking context** when **z-index** value is not **auto**.


![[Pasted image 20240825144020.png]]



![[Pasted image 20240825144208.png]]


###### key summary

The importance of these types of positions -- relative & absolute -- lies in their ability to remove items from the normal flow.

if we use positioning wise, we can achieve:
- isolation\
	modifications made to elements positioned in this way will not affect other elements within the normal flow
- performance optimization\
	key prerequisite for optimizing & minimizing updates to the DOM tree.


## Stacking Context



![[Pasted image 20240825144804.png]]

## Reflow

30:00

reflow happens when javascript tries to modify the dom tree.


![[Pasted image 20240825145054.png]]






























