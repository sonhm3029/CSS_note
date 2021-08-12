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

            <p>Hover over the div element below:</p>

            <div></div>

            <p><b>Note:</b> This example does not work in Internet Explorer 9 and earlier versions.</p>

        </body>
    </html>

```

[Xem ví dụ](https://www.w3schools.com/css/tryit.asp?filename=trycss3_transition_transform)

## V. Animation

## VI. Keyframe

## VII Function