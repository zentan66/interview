**为什么排版引擎解析CSS选择器时一定要从右往左解析？**

HTML经过解析生成DOM Tree，而在CSS解析完毕后，需要将解析的结果与DOM Tree的内容一起进行分析，并建立一棵Render Tree，用来绘图

Render Tree中的元素与DOM元素相对应，但并非一一对应：一个DOM元素可能会对应多个Renderer

在建立Render Tree时浏览器就要为每个DOM Tree中的元素根据CSS的解析结果来确定生成怎样的renderer。对于每个DOM元素，必须在所有Style Rules中找到符合的selector，并将对应的规则进行合并，选择器的「解析」实际就是这里执行的，在遍历DOM Tree时，从Style Rules中寻找对应的selector

如果解析CSS的时候是正向解析，例如「div div p em」，我们首先就要检查当前元素到html的整条路径，找到最上层的div，再往下找，如果不匹配就必须回到最上层的那个div，再匹配选择器中的第一个div，回溯若干次才能确定匹配与否

逆向匹配则不同，如果当前的DOM元素是div，而不是selector最后的em，那么只要一步就能排除

逆向匹配带来的优势是巨大的，但是如果在选择器结尾上加上「*」就大大降低了这种优势，这也就是很多优化原则提到的尽量避免在选择器末尾添加通配符的原因