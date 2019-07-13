1. 在第一个练习中，练习的是三列布局，核心是float加margin负值。
   - 设置了float属性的元素display属性会变为inline-block。
   - 设置了float属性的元素会脱离文档流。
   - margin-left和margin-top设置为负值，可以移动元素。即使元素写在DOM的后面，也能通过设置负值显示在最前面（在设置了float属性的前提下）。
   - margin-right和margin-bottom设置为负值，元素不会移动。
2. 第二个练习中，要求的是wrapper的宽度是50%，位置在最左侧。navigation、extra宽度分别为25%。依次位于content的右侧。
   - 如果不考虑扩展性，我们可以这样设置CSS样式：
   ```
   .wrapper {
            width: 50%;
            float: left;
            background: #ebccd1;
        }
        .navigation {
            width: 25% ;
            float: left ;
            background: #c7254e;
        }
        .extra {
            width: 25% ;
            float: left ;
            background: #c9e2b3;
        }
   ```
   因为三个元素的宽度是50% 25% 25%，恰好是整个页面的宽度。在宽度允许的情况下，设置float属性的元素尽可能会在同一行。这样做的缺点是：内容区宽度要小于页面宽度，且无法调换元素先后顺序（按照文档流的顺序）。
   - 最好还是结合float和margin-left负值来实现布局，这样可扩展性高。顺序可调。
   - margin-left设置负值，如果是百分数，是相对于父元素的宽度。
   - margin-left设置负值，移动的起始位置是相对于元素的原本位置而言。
   - 一个元素设置了margin-left为负值，则向左移动，后面的元素也跟着移动，填补原来的空缺。
3. 第三个练习，要求wrapper的宽度是50%，位置在最右侧，navigation、extra宽度分别为25%。依次位于content的左侧。
   - 三个元素的float属性还是left。但是注意设置wrapper的左外边距为50%。
   - 对于navigation和extra，依旧使用margin-left设置负值，进行移动。
4. 第四个练习，要求是container宽度是700px且居中，而wrapper是400px也要居中，而navigation和extra宽度为150px，分别在content的两侧。
   - 对于块级元素，设置了宽度的情况下，水平居中的方法是：
   `margin: 0 auto ;`
   - 如果块级元素设置了float属性，则使用`margin: 0 auto ;`的方式设置水平居中，不起作用。我们必须指定margin-left和margin-right的值。
   - navigation和extra的位置依旧是float属性结合margin-left负值向左移动。
5. 第五个练习，要求是container宽度是700px且居中，而wrapper是400px也要左对齐，而navigation和extra宽度为150px，依次在content的右侧。
   - 三个元素的宽度已知，且总和等于父元素的宽度，因此可以直接设置float属性为left即可。
   - 如果元素在浏览器中的呈现的位置不是文档流的顺序，则可以通过margin-left负值进行调整。
6. 第六个练习，要求container 宽度700px且居中而wrapper 右对齐且宽度400px，navigation和extra宽度是150px，依次位于content左侧。
   - 第一种实现方式是设置float为left，并设置margin-left为负值，使navigation和extra移动到指定位置。
   - 第二种实现方式是设置float为right，此时需要设置margin-right，来移动navigation和extra。
   - 一个元素设置了float属性为right，那么设置margin-left为负值时，该元素不会向左移动。设置margin-right为负值，则该元素向右移动。设置float属性为left同理。
   - 如果两个元素同时设置float属性为left。则第一个元素设置margin-right为负值，比如为20px，第二个元素会把第一个元素看成宽度缩小20px（所以会覆盖一部分），但是第一个元素没有任何变化，而是依然保持原先的宽度。设置float属性为right时，margin-left为负值也是这样的类似的效果。
7. 第七个练习，要求wrapper居中且宽度自适应，margin-left及margin-right为200px。extra、navigation 宽度200px，分别位于content两侧。
   - 中间宽度自适应，两边宽度固定。
   - 统一设置三个元素为向左浮动。
   - wrapper设置margin属性为：`margin 0 200px ;`
   - wrapper的width属性不能设置为100%。因为这样会占据整个父元素的宽度。而左侧还留有200px的的外边距，整体效果就是wrapper偏右，而且extra和navigation无法移动过来（超出了浏览器的窗口范围）。
   - navigation和extra还是通过给margin-left设置负值（百分比和固定像素值），来向左移动到指定位置的。
8. 第八个练习，要求wrapper 左对齐且宽度自适应，margin-right为400px。navigation、extra 宽度200px，依次位于content右侧。
   - 可以使用向左浮动实现这个布局。
   - 自适应宽度的话，不需要指定width值。这样内容区宽度会根据内容以及页面的变化而自行调整。
   - 也可以通过向右浮动实现布局。这里要注意的是：extra的移动距离不确定，因为main的宽度是不定的。所以要使用calc()函数动态计算距离。
9. 第九个练习，要求是wrapper 右对齐(float:right)且宽度自适应，margin-left为400px。extra、navigation 宽度200px，依次位于content左侧。
   - 这个布局比较简单。依旧是向右浮动结合margin-right设置负值向右移动元素。
   - 设置margin-left用于给navigation和extra留下空间。
10. 第十个练习，要求navigation 宽度200px，位于content左侧，而content位于中间，宽度自适应。extra 宽度33%，位于content右侧。
    - 三个元素依旧设置向左浮动。
    - content宽度自适应，通过设置wrapper的margin-left和margin-right实现。不能设置width为100%。
    - navigation的宽度固定。通过设置margin-left为负值，向左移动到指定位置。
    - extra的宽度为百分数，则实际宽度根据父元素的宽度而定。
11. 第十一个练习，要求wrapper左对齐，宽度自适应，而navigation宽度为200px，位于wrapper的右侧。extra是25%，位于navigation的右侧。
    - wrapper宽度自适应，extra的款式是25%，而navigation的宽度是200px，单位不统一。所以此时需要使用calc()函数进行计算。
    - calc()函数的特点：
       1. 用来计算动态的数值，可以百分比，px，em等单位混合使用。
       2. 使用四则混合运算（+ - * /），注意，每个运算符前后要加空格，否则浏览器不识别。
       3. 使用标准的数学运算优先级规则。
    - wrapper、navigation、extra统一向左浮动，wrapper设置margin-right，给navigation和extra预留出空间。
    - navigation和extra设置好宽度后，设置margin-left为负值，向左移动。
    - 不确定数值的地方都使用calc()函数进行计算。
    - 可以不使用calc()函数，完成这个布局：
       1. wrapper的宽度100%，这样wrapper可以平铺整个页面。
       2. wrapper的margin-left设置为-25%，向左平移25%，因为宽度是100%，所以右侧会留出25%的空间，给extra。
       3. **content没有设置宽度，所以默认是继承父元素的宽度，是100%**
       4. **wrapper向左移动了25%，部分内容被遮挡，所以需要设content的margin-left为25%，这样把wrapper的平移抵消掉，从而内容区可以正常显示。**
       5. **设置margin-right为200px，给navigation留出空间。**
       6. navigation和extra向左浮动。因为预留出了固定的空间，所以直接向左移动即可。
    - 第二种不使用calc()的方法没有第一种简单，代码量也多一些。推荐使用第一种方法。
