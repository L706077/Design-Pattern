# Design-Pattern

- [1](http://monkeycoding.com/?page_id=899)

- [2](https://www.gitbook.com/book/rongli/design-pattern/details)

- [虛擬函式、抽象類別](https://openhome.cc/Gossip/CppGossip/PureVirtualFunction.html)


### abstract class, virtual function, override
#### virtual function
如果要將某個函式成員宣告為虛擬函式，則要加上"virtual"關鍵字，然而C++提供一種語法定義「純虛擬函式」 （Pure virtual function），指明某個函式只是提供一個介面，要求繼承的子類別必須重新定義該函式<br/>

#### abstract class
一個類別中如果含有純虛擬函式，則該類別為一「抽象類別」（Abstract class），該類別只能被繼承，而不能用來直接生成實例，如果試圖使用一個抽象類別來生成實例，則會發生編譯錯誤。<br/>


**Singleton模式**<br/>
**Observer模式**<br/>
**Template Method模式**<br/>

**Façade模式**<br/>
表象模式：提供了一個統一的介面，用來存取次系統的一群介面，讓次系統共容易使用<br/>
我們以泡咖啡來形容表象模式，假設泡咖啡有以下幾種流程：<br/>
1.煮開水<br/>
2.準備咖啡粉<br/>
3.倒入熱水<br/>
4.攪拌<br/>
```C++
#include <iostream>
using namespace std;

class Boil{
public:
    void boilWater(){ cout << "煮開水" << endl; }
};
class Coffee{
public:
    void blueMountain(){ cout << "準備藍山咖啡" << endl; }
    void mandheling(){ cout << "準備曼特寧咖啡" << endl; }
};
class Pour{
public:
    void pourHotWater(){ cout << "倒熱水" << endl; }
    void pourColdWater(){ cout << "倒冷水" << endl; }
};
class Stir{
public:
    void fastStir(){ cout << "快速攪拌" << endl; }
    void slowStir(){ cout << "慢慢攪拌" << endl; }
};

class MakeCoffee{
private:
    Boil m_boil;
    Coffee m_coffee;
    Pour m_pour;
    Stir m_stir;
public:
    MakeCoffee(Boil, Coffee, Pour, Stir);
    void process();
};
MakeCoffee::MakeCoffee(Boil boil, Coffee coffee, Pour pour, Stir stir){
    m_boil = boil;
    m_coffee = coffee;
    m_pour = pour;
    m_stir = stir;
}
void MakeCoffee::process(){
    m_boil.boilWater();
    m_coffee.blueMountain();
    m_pour.pourHotWater();
    m_stir.slowStir();
}
int main(){
    Boil boil; 
    Coffee coffee; 
    Pour pour; 
    Stir stir;
    MakeCoffee myCoffee(boil, coffee, pour, stir);
    myCoffee.process();   
    return 0;
}
```
<br/>

**State模式**<br/>
**Factory Method模式**<br/>
**Abstract Factory模式**<br/>
**Strategy模式**<br/>
**Command模式**<br/>
**Adapter模式**<br/>
**Composite模式**<br/>

