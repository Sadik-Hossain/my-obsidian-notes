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


**what is the reflow?**\
When you read your HTML and CSS, the browser compiles two trees. 

One is the DOM, which is basically the object representation of your HTML. \
And the second one is CSSOM, which is the tree of all CSS rules that apply to some HTML elements.

And the final render tree is built using both of these trees. So basically merging that. Then there is a process called reflow. The reflow happens when some Javascript tries to modify the DOM tree or the styles. 

So for instance, it could be, you have the load more button and then you render more cards on your list.

Or it's also could be when you're rendering your React app, so you first load your index HTML. Then you provide the container where React should work and do the modification to the DOM via DOM API. So the reflow process is multi-step pipeline. 

First, it's usually kicked off by JavaScript then when we apply the DOM modification, the browser needs to recalculate the DOM and CSSOM sub tree.

So that reminds, it compiles all your style selectors then rebuilds the DOM and CSSOM tree.\
Then once it's ready, the browser needs to recalculate the positions and the HTML properties. So it's a layout phase. So and the style and layout phase are very CPU bound. This means that if we trigger reflow too much, we can block the render thread.

Once everything is ready, and now we need to draw the bitmap on the screen, the GPU is used, which is the paint phase.\
So the paint phase is basically drawing the pixels on your monitor. So it involves the GPU and it's separated from the CPU.\
So this means that it doesn't block the rendering thread and it's pretty fast because GPU is very good at drawing pixels on the screen.

And then the last phase is composite phase.\
when you have multiple layers on your screen. So the composite phase, just arrange them in the right order to make sure that everything is displayed correctly. And to prove that, we can optimize this pipeline.

Actually, first, let's look at the example of the reflow. So this is the Wikipedia page that we can use. And as you can see, this is how the browser renders the page into a reflow. So first, it goes from top to bottom. And then you will see that there are some styles loaded, and the browser needs to do the full reflow for the page.


You see we again go from top to bottom just adjusting the styles on the elements.  

Eric: So let's have a quick example of the non-optimized pipeline where we utilize the style layout, paint and composite face and optimize pipeline. So we need to open the codes inbox example. So right now we're rendering 2,000 rectangles on the screen, and the idea is, right now the page is using optimized pipeline.

So we mostly utilize the GPU. And as you can see, there is no lag on the screen. So we are getting our 60fps and we can measure the performance by going to the performance tab. And now we can try to see how much CPU is loaded. So we can run the quick snapshot and that should be enough.

So if we look at the CPU here, so we utilize 0% of CPU, so basically, it's a flat line.\
But we can switch this to the non-optimized pipeline. So let's try to run the snapshot now. And you see the buffer is filled in in three seconds.  
Eric: See now the CPU is loaded.


And the thing is, this Mac is 16 cores, but you don't have the 16 cores M.2 Macs on every device. And if we throttle the CPU here, you will see that CPU will work hard just to move these 2,000 rectangles. The difference in the pipeline sometimes and the code difference is very small.

[00:04:51]  
So if we look how everything is built, is just two lines. If we apply the margin-top property in animation, then what the browser does, it needs to recalculate the position of every element, like of all 2,000 rectangles, to render the frame. While we apply the translateY function, it only moves the pixels.

[00:05:16]  
It used only the GPU just to draw a new pixel set because the CSS transformation, they do not utilize CPU.



























