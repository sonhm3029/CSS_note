# CSS note

## I. Transition

- Dùng để thêm thời gian khi thực hiện transform cho element

**Ví dụ:**

```html
    <head>
        <style>
            div {
                width: 100px;
                height: 100px;
                background-color: red;
                /* Thay dổi nhiều thuộc tính với dấu , */
                transition: width 2s, height 4s;
            }

            div:hover {
                width: 200px;
                height:200px;
            }
        </style>
    </head>    
    <body>
    <div></div>
```

[Xem ví dụ](https://replit.com/@SnHong3/TransitionExample#index.html)

- Set sự thay đổi theo thời gian với `transition-timing-function`. Các giá trị:
  - `ease` - transition effect ban đầu chậm, sau đó nhanh rồi lại chậm lại
  - `linear` -transiton với tốc độ như nhau tại mọi thời điểm
  - `ease-in` - transition với tốc độ chậm lúc bắt đầu
  - `ease-out` - transition chậm tại lúc kết thúc
  - `ease-in-out` - transition chậm tại lúc bắt đầu và kết thúc
  - cubic-bezier(n,n,n,n) - lets you define your own values in a cubic-bezier function

```html
<style>
    #div1 {transition-timing-function: linear;}
    #div2 {transition-timing-function: ease;}
    #div3 {transition-timing-function: ease-in;}
    #div4 {transition-timing-function: ease-out;}
    #div5 {transition-timing-function: ease-in-out;}
</style>
```

[Xem ví dụ](https://replit.com/@SnHong3/Transitonexample2#index.html)

- Delay transition với `transition delay`. Khi đó sau khi thực hiện tác động 1 khoảng tg nhất định thì changing effect mới xảy ra:

```html
    <style>
        div {
            transition-delay: 1s;
        }
    </style>
```

[Xem ví dụ](https://replit.com/@SnHong3/transitionexample3#index.html)

Sử dụng short hand:

```html
    <style>
        div {
            transition: width 2s linear 1s;
        }
    </style>
```

[Xem ví dụ](https://replit.com/@SnHong3/Transitionexample4#index.html)

Property | Description
---------|------------
transition | A shorthand property for setting the four transition properties into a single property
transition-delay | Specifies a delay (in seconds) for the transition effect
transition-duration | Specifies how many seconds or milliseconds a transition effect takes to complete
transition-property | Specifies the name of the CSS property the transition effect is for
transition-timing-function | Specifies the speed curve of the transition effect

## II. Flex Box

Xem ảnh sau để biết flex box ảnh hưởng thế nào đến content:

![flex_box_effect](./flex_terms.png)

Để tạo flex box cho một nhóm element nào đó chúng ta cần phải tạo một block contain chúng và block đó sẽ có thuộc tính `display: flex`

Khi đó block contain được gọi là `flex container` còn các element bên trong trực tiếp của nó được gọi là `flex item`. Như hình.

### 1. Các thuộc tính của flex container

**Theo dõi hình ta có các thuộc tính của `flex container`:**

Properties | Values
-----------|-------
`display`|`flex`/ `flex-inline`
`flex-direction`|`row/row-reverse` và `column/column-reverse`
`flex-wrap`|`wrap`/`no-wrap`
`justify-content`|`flex-start`/`flex-end`/`center`/ `space-around`/ `space-between`
`align-items`|`flex-start`/ `flex-end` /`center`/`stretch` / `baseline`
`align-content`|`flex-start`/ `flex-end`/ `center`/ `space-around`/`stretch`/`space-between`

Trong đó:

- `flex-inline` để biến container thành `inline-block` element

- `flex-direction` sẽ quyết định chiều **main axis** với `row` là theo chiều ngang và `column` là theo chiều dọc. Tức là các element sẽ flex theo chiều nào. Còn -reverse sẽ đảo 2 điểm **start và end** của main-axis. Khi đó thứ tự xuất hiện của các element sẽ ngược lại với thứ tự khi chúng ta lập trình

- `flex-wrap`. Default nếu k để wrap thì flex item cứ thêm ở trên cùng một hàng kể cả khi màn hình to hay nhỏ dẫn để overflow contain block. vì vậy
  - `no wrap`: default
  - `wrap`: flex item sẽ tự xuống dòng theo chiều **cross axis** nếu chiều rộng màn hình không đủ

- `justify-content`: thuộc tính này dùng để căn lề cho các element theo chiều của **main axis**. Ví dụ nếu **main axis** và **cross axis** như trên hình đầu thì:
  - `flex-start` sẽ căn lề element về phía điểm start theo chiều ngang.
  - Ngược lại với `flex-end`
  - căn đều hai bên với `center`
  - `space between` sẽ thêm khoảng trống giữa các element không bao gồm lề ngoài cùng của phần từ đầu tiên và lề cuối của phần tử cuối cùng
  - `space around` giống `space between` nhưng sẽ có cả khoảng trống cho cả 2 bên lề đầu và cuối

- `align-items`: thuộc tính này dùng để căn lề cho các element theo chiều của **cross axis**
  - các giá trị `flex` như của **main axis** nhưng là theo chiều của **cross axis**
  - `stretch` sẽ làm cho element giãn ra full container theo chiều của **cross axis**

- `align-content`: căn lề cho flex line của element theo chiều của **cross axis** các giá trị giống với các thuộc tính trước.

**Chúng ta có thể căn chỉnh cho flex element chính giữa flex container bằng cách set 2 thuộc tính `justify-content` và `align-items` về `center`:**

```html
<style>
    .flex-container {
        display: flex;
        height: 300px;
        justify-content: center;
        align-items: center;
    }
</style>
}
```

### 2. Các thuộc tính của flex items

Property | Description
---------|------------
align-self | Specifies the alignment for a flex item (overrides the flex container's align-items property)
flex | A shorthand property for the flex-grow, flex-shrink, and the flex-basis properties
flex-basis | Specifies the initial length of a flex item
flex-grow | Specifies how much a flex item will grow relative to the rest of the flex items inside the same container
flex-shrink | Specifies how much a flex item will shrink relative to the rest of the flex items inside the same container
order | Specifies the order of the flex items inside the same container

- Trong đó `align-self` là thuộc tính tự align theo cross-axis, thuộc tính này sẽ ghi đè lên align-items của flex container.

- order là thuộc tính để sắp xếp thứ tự của element

- flex dùng short hand để set độ lớn của element

## III. Transform

Với `transform` property ta có thể sử dụng 2D transformation với các giá trị:

- `translate()`
- `rotate()`
- `scaleX()`
- `scaleY()`
- `scale()`
- `skewX()`
- `skewY()`
- `skew()`
- `matrix()`

### 1. translate

- `translate()` method dùng để di chuyển elment theo trục X và Y. Giống với `position` nhưng là dịch chuyển thuận.

- Khi dịch chuyển thì normal position của element remain tức là để lại khoảng trống tại vị trí ban đầu.

**Ví dụ:**

```html
    <style>
        div {
            transform: translate(50px, 100px);
    }
    </style>
```

Với giá trị trên sẽ di chuyển thẻ `div` sang phải 50px và xuống dưới 100px. Để giá trị âm sẽ di chuyển theo chiều ngược lại, sang trái hoặc lên trên.

[Xem ví dụ](https://www.w3schools.com/css/tryit.asp?filename=trycss3_transform_translate)

### 2. rotate

Quay element theo chiều kim đồng hồ với đơn vị `deg` (degree)

**Ví dụ:**

```css
    div {
        transform: rotate(20deg);
    }
```

Như vậy thẻ `div` sẽ quay theo chiều kim đồng hồ 20 degree. Nếu dùng giá trị âm nó sẽ quay ngược chiều kim đồng hồ.

### 3. scale

Dùng `scale()` method để thay đổi size của element

**Ví dụ:**

```css
    div {
        transform: scale(2, 3);
    }
```

Ví dụ ban đầu ta set `div` với `width = 50, height = 50` thì sau khi scale như trên, `width` tăng 2 lần lên 100px, `height` tăng 3 lần lên 150px. Nếu sử dụng giá trị < 1 thì nó sẽ là giảm đi.

Ta có thể dùng `scaleX(time)` và `scaleY(time)` để set riêng width hoặc height.

**Ta có thể sử dụng matrix() method để short hand các property trên:**

```css
    matrix(scaleX(),skewY(),skewX(),scaleY(),translateX(),translateY())
```

[Tham khảo thêm tại](https://www.w3schools.com/css/css3_2dtransforms.asp)

## IV.  Kết hợp transition và transform

Thêm duration vào transform để hiệu ứng được đẹp hơn

Ví dụ :

```html

    <!DOCTYPE html>
    <html>
        <head>
            <style> 
            div {
              width: 100px;
              height: 100px;
              background: red;
              transition: width 2s, height 2s, transform 2s;
            }

            div:hover {
              width: 300px;
              height: 300px;
              transform: rotate(180deg);
            }
            </style>
        </head>
        <body>

            <h1>Transition + Transform</h1>

            `<p>`Hover over the div element below:</p>

            <div></div>

            `<p>`<b>Note:</b> This example does not work in Internet Explorer 9 and earlier versions.</p>

        </body>
    </html>

```

[Xem ví dụ](https://www.w3schools.com/css/tryit.asp?filename=trycss3_transition_transform)

## V. Animation

Property | Description | Values
---------|-------------|--------
`@keyframes`|Khai báo animation
`animation-name`|tên của animation được khai báo bởi `keyframe`
`animation-duration`|khoảng thời gian diễn ra animation| Thời gian ví dụ `2s`
`animation-delay`|Khoảng thời gian delay trước khi diễn ra animation| Thời gian. Nếu mang giá trị âm ví dụ `-2` thì animation sẽ chạy từ thời điểm 2s trong `animation duration`
`animation-iteration-count`|Số lần lặp lại animation| số lần ví dụ `4` hoặc `infinitive` lặp mãi mãi
`animation-direction`|xác định animation sẽ được chạy thuận hay nghịch theo khai báo của `keyframe`|- `normal`: đây là default<br>- `reverse`: animation chạy ngược với khai báo trong `keyframe`<br> - `alternate`: animation sẽ chạy thuận đến kết thúc animation r lại chạy ngược lại.<br> - `alternate-reverse`: ngược lại với `alternate`
`animation-timing-function`|Set sự diễn ra nhanh hay chậm trên từng khoảng thời gian của animation|- `ease`: bắt đầu chậm, rồi nhanh, rồi kết thực chậm <br> - `linear`: Same speed thông suốt animation....
`animation-fill-mode`|Set trạng thái của element khi không xảy ra animation nữa|- none: default, nó sẽ trở về vị trí ban đầu khi kết thúc animation<br> - `forwards`: element sẽ remain trạng thái của last keyframe khi kết thúc animation.<br>- `backwards`: element sẽ apply trạng thái đầu tiên của `keyframe` trong suốt thời gian delay (trước khi bắt đầu animation)<br>- `both` element sẽ apply cả `forwards` và`backwards`.
`animation`|Công thức short hand

Để sử dụng Animation ta cần định nghĩa một `@keyframe` để xác định sự thay đổi của element từ trạng thái ban đầu đến trạng thái nào đó

**Ví dụ:**

```css
    @keyframes animation_name {
        from {background-color: red;}
        to {background-color green;}
    }
```

Ở trên ta đã định nghĩa một animation với thuộc tính `animation_name` là animation_name( cái này là do coder đặt). Có trạng thái thay đổi từ `background` màu đỏ ban đầu và kết thức là màu xanh lá cây.

Có thể sử dụng `%` để thêm nhiều style change khi animation đạt đến % nào đó của cả `animation-duration`.

```css
    @keyframes example {
        0%   {background-color: red;}
        25%  {background-color: yellow;}
        50%  {background-color: blue;}
        100% {background-color: green;}
    }

```

```css
    @keyframes example {
        0%   {background-color:red; left:0px; top:0px;}
        25%  {background-color:yellow; left:200px; top:0px;}
        50%  {background-color:blue; left:200px; top:200px;}
        75%  {background-color:green; left:0px; top:200px;}
        100% {background-color:red; left:0px; top:0px;}
    }
```

Như vậy với `0%` bằng với `from` và `100%` bằng với trạng thái cuối cùng. Ví dụ duration của animation là 4s thì animation trên sẽ diễn ra theo thứ tự: background đầu tiên có màu đỏ, giây thứ nhất sẽ chuyển thành màu vàng, giây thứ 2 sẽ chuyển sang màu xanh da trời và cuối cùng sẽ chuyển thành màu xanh lá cây.

- Sau khi định nghĩa `@keyframe` ta sẽ thêm animation vào style. Ví dụ cho vào thẻ `div`

**Syntax short hand của animation:**

Khai báo thông thường

```css
    div {
        animation-name: example;
        animation-duration: 5s;
        animation-timing-function: linear;
        animation-delay: 2s;
        animation-iteration-count: infinite;
        animation-direction: alternate;
    }
```

Với short hand

```css
    div {
        animation: example 5s linear 2s infinite alternate;
    }
```

[Xem thêm tại](https://www.w3schools.com/css/css3_animations.asp)

Ngoài ra còn có thuộc tính `animation-play-state` với các giá trị:

- `running`: default, chạy bình thường
- `paused`: animation được paused
- `initial`: Set thuộc tính về default value. [Đọc thêm](https://www.w3schools.com/cssref/css_initial.asp)
- `inherit`: Kế thừa propety từ parent element. [Đọc thêm](https://www.w3schools.com/cssref/css_inherit.asp)

Ví dụ cho `paused`:

```css
    div:hover {
        animation-play-state: paused;
    }

    @keyframes mymove {
        from {left: 0px;}
        to {left: 200px;}
    }
```

Khi element đang thực hiện animation mà bị hover nó sẽ đứng yên (dừng animation), khi bỏ hover nó sẽ tiếp tục animation.

**Chú ý: Đối với các animation thực hiện chuyển động thì cần set position của element khác static.**

[Xem thêm tại](https://www.w3schools.com/css/css3_animations.asp)

## VII Function

### 1. calc()

- Dùng để thực hiện tính toán trong CSS

**Ví dụ:**

```css
    #div1 {
        position: absolute;
        left: 50px;
        width: calc(100% - 100px);
        border: 1px solid black;
        background-color: yellow;
        padding: 5px;
        text-align: center;
    }
```

Ví dụ trên sẽ set `width` của `div` là `(chiều rộng parent - 100px)`

### 2. attr()

- Trả về giá trị attribute của element

**Ví dụ:**

```css
    a:after {content: " (" attr(href) ")";}
```

```html
    <a href="https://www.w3schools.com">Visit W3Schools</a>
```

Khi dùng như trên thì sẽ thêm vào sau content bên trong thẻ `a` là `(https://www.w3schools.com)`. Như vậy thẻ a sẽ hiện thị là: `Visit W3Schools (https://www.w3schools.com)`

### 3. rgb() và rgba()

Set màu. Trong đó:

- `rgb(r,g,b)` là hệ màu rbg thông thường
- `rgba(r,g,b,o)` là hệ mà với opacity là giá trị `o` cuối cùng trong công thức với chỉ số nằm trong đoạn **[0-1]**

## VIII. CSS Varibbles

CSS `var` dùng để gán giá trị cho một biến nào đó và sử dụng trong suốt css work space. Việc sủ dụng biến này khá giống với biến của các ngôn ngữ lập trình. Nó cũng phân ra làm hai loại:

- Biến toàn cục: dùng cho tất các element trong css work space
- Biến cục bộ: chỉ dùng được trong chính element declared nó.

**Ví dụ: thông thường ta sẽ set color property cho các element như sau.**

```css
    body { background-color: #1e90ff; }

    h2 { border-bottom: 2px solid #1e90ff; }

    .container {
        color: #1e90ff;
        background-color: #ffffff;
        padding: 15px;
    }

    button {
        background-color: #ffffff;
        color: #1e90ff;
        border: 1px solid #1e90ff;
        padding: 5px;
    }
```

Thay vì việc lặp lại các giá trị mã màu như trên ta có thể dùng biến như sau.

Đầu tiên cần declared biến. Ví dụ để declared biến toàn cục ta làm như sau:

```css
    :root {
        --blue: #1e90ff;
        --white: #ffffff;
    }
```

`:root` đại diện cho toàn bộ document. Việc đặt tên biến bắt buộc phải có `--` đằng trước. Như trên là `--blue`, đây chính là tên biến và `#1e90ff` là giá trị.

Để dùng biến trong các element ta sử dụng syntax:

```css
    var(tên biến, value)
```

```css
    :root {
        --blue: #1e90ff;
        --white: #ffffff;
    }

    body { background-color: var(--blue); }

    h2 { border-bottom: 2px solid var(--blue); }

    .container {
      color: var(--blue);
      background-color: var(--white);       
      padding: 15px;
    }

    button {
      background-color: var(--white);
      color: var(--blue);
      border: 1px solid var(--blue);
      padding: 5px;
    }
```

Trong đó lưu ý tên biến đúng quy ước là `--name`. Value là optional giá trị value sẽ được áp cho biến nếu như nó chưa được định nghĩa. Ví dụ ở trên ta đã định nghĩa 2 biến `--blue` và `--white` nhưng nếu ta có 1 class nào đó. Ví dụ:

```css
    .demo {
        color: var(--black, #000000);
    }
```

Biến `--black` chưa được định nghĩa cho nên nó sẽ nhận giá trị theo sau như khai báo là `#000000`. Dĩ nhiên nếu như ta để là `(--blue,#000000)` thì giá trị `#000000` không được áp dụng vì biến `--blue` đã được khai báo từ trước.

Việc sử dụng biến như trên giúp cho css của ta dễ đọc hơn. Nếu muốn đổi màu chỉ cần thay đổi giá trị tại phần khai báo lúc đầu.

### 1. Ghi đè var

Trong trường hợp biến cục bộ cùng tên với biến toàn cục thì nó sẽ ghi đè biến toàn cục.

**Ví dụ:**

```css
    :root {
        --blue: #1e90ff;
        --white: #ffffff;
    }

    body { background-color: var(--blue); }

    h2 { border-bottom: 2px solid var(--blue); }

    .container {
      color: var(--blue);
      background-color: var(--white);
      padding: 15px;
    }

    button {
        --blue: #000000;
      background-color: var(--white);
      color: var(--blue);
      border: 1px solid var(--blue);
      padding: 5px;
    }
```

Ví dụ trên ta đã ghi đè biến `--blue` trong button. Vì vậy boder của button sẽ có màu `#000000` thay vì `#1e90ff`

IX. CSS pseudo-class và pseudo-element

**TẤT CẢ PSEUDO ELEMENT:**

Selector | Example | Example description
---------|---------|--------------------
::after | p::after | Insert something after the content of each `<p>` element
::before | p::before | Insert something before the content of each `<p>` element
::first-letter | p::first-letter | Selects the first letter of each `<p>` element
::first-line | p::first-line | Selects the first line of each `<p>` element
::marker | ::marker | Selects the markers of list items
::selection | p::selection | Selects the portion of an element that is selected by a user

====================================================

**TẤT CẢ PSEUDO CLASSES:**

Selector | Example | Example description
---------|---------|--------------------
:active | a:active | Selects the active link
:checked | input:checked | Selects every checked `<input>` element
:disabled | input:disabled | Selects every disabled `<input>` element
:empty | p:empty | Selects every `<p>` element that has no children
:enabled | input:enabled | Selects every enabled `<input>` element
:first-child | p:first-child | Selects every `<p>` elements that is the first child of its parent
:first-of-type | p:first-of-type | Selects every `<p>` element that is the first `<p>` element of its parent
:focus | input:focus | Selects the `<input>` element that has focus
:hover | a:hover | Selects links on mouse over
:in-range | input:in-range | Selects `<input>` elements with a value within a specified range
:invalid | input:invalid | Selects all `<input>` elements with an invalid value
:lang(language) | p:lang(it) | Selects every `<p>` element with a lang attribute value starting with "it"
:last-child | p:last-child | Selects every `<p>` elements that is the last child of its parent
:last-of-type | p:last-of-type | Selects every `<p>` element that is the last `<p>` element of its parent
:link | a:link | Selects all unvisited links
:not(selector) | :not(p) | Selects every element that is not a `<p>` element
:nth-child(n) | p:nth-child(2) | Selects every `<p>` element that is the second child of its parent
:nth-last-child(n) | p:nth-last-child(2) | Selects every `<p>` element that is the second child of its parent, counting from the last child
:nth-last-of-type(n) | p:nth-last-of-type(2) | Selects every `<p>` element that is the second `<p>` element of its parent, counting from the last child
:nth-of-type(n) | p:nth-of-type(2) | Selects every `<p>` element that is the second `<p>` element of its parent
:only-of-type | p:only-of-type | Selects every `<p>` element that is the only `<p>` element of its parent
:only-child | p:only-child | Selects every `<p>` element that is the only child of its parent
:optional | input:optional | Selects `<input>` elements with no "required" attribute
:out-of-range | input:out-of-range | Selects `<input>` elements with a value outside a specified range
:read-only | input:read-only | Selects `<input>` elements with a "readonly" attribute specified
:read-write | input:read-write | Selects `<input>` elements with no "readonly" attribute
:required | input:required | Selects `<input>` elements with a "required" attribute specified
:root | root | Selects the document's root element
:target | #news:target | Selects the current active #news element (clicked on a URL containing that anchor name)
:valid | input:valid | Selects all `<input>` elements with a valid value
:visited | a:visited | Selects all visited links

**CHÚ Ý TỚI SYNTAX DẤU `:` VÀ `::`.**
