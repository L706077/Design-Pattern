# Design-Pattern

- [1](http://monkeycoding.com/?page_id=899)

- [2](https://www.gitbook.com/book/rongli/design-pattern/details)

- [虛擬函式、抽象類別](https://openhome.cc/Gossip/CppGossip/PureVirtualFunction.html)


### abstract class, virtual function, override
#### virtual function
如果要將某個函式成員宣告為虛擬函式，則要加上"virtual"關鍵字，然而C++提供一種語法定義「純虛擬函式」 （Pure virtual function），指明某個函式只是提供一個介面，要求繼承的子類別必須重新定義該函式<br/>

#### abstract class
一個類別中如果含有純虛擬函式，則該類別為一「抽象類別」（Abstract class），該類別只能被繼承，而不能用來直接生成實例，如果試圖使用一個抽象類別來生成實例，則會發生編譯錯誤。<br/>

