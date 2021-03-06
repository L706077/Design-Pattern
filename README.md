# Design-Pattern

- [1](http://monkeycoding.com/?page_id=899)

- [2](https://www.gitbook.com/book/rongli/design-pattern/details)

- [3](https://openhome.cc/Gossip/DesignPattern/)

- [虛擬函式、抽象類別](https://openhome.cc/Gossip/CppGossip/PureVirtualFunction.html)

- [video1](https://www.youtube.com/watch?v=g3cN-_MBvZg)

- [video2-c++](https://www.youtube.com/channel/UCqDN2eVe-e-HCkbmw4fy4Tw)

- [video3-c++](https://www.youtube.com/watch?v=1oz1b6WLwZE)

### abstract class, virtual function, override
#### virtual function
如果要將某個函式成員宣告為虛擬函式，則要加上"virtual"關鍵字，然而C++提供一種語法定義「純虛擬函式」 （Pure virtual function），指明某個函式只是提供一個介面，要求繼承的子類別必須重新定義該函式<br/>

#### abstract class
一個類別中如果含有純虛擬函式，則該類別為一「抽象類別」（Abstract class），該類別只能被繼承，而不能用來直接生成實例，如果試圖使用一個抽象類別來生成實例，則會發生編譯錯誤。<br/>

----

### Creational創建型模式
如何有效率的產 生、管理 與操作物件，一直都是值得討論的課題， Creational 模式即與物件的建立相關，在這個分類下的模式給出了一些指導原則及設計的方向<br/>
- **Simple Factory Pattern簡單工廠模式**<br/>
- **Factory Method工廠模式**<br/>
- **Abstract Factory抽象工廠模式**<br/>
- **Singleton單例模式**<br/>
- **Builder建造者模式**<br/>

----

### Structural結構型模式
如何設計物件之間 的靜態結構，如何完成物件之間的繼承、實 現與依賴關係，這關乎著系統設計出來是否健壯（robust）：像是易懂、易維護、易修改、耦合度低等等議題。Structural 模式正如其名，其分類下的模式給出了在不同場合下所適用的各種物件關係結構。<br/>

- **Bridge橋接模式**<br/>
- **Adapter適配器模式**<br/>
- **Composite模式**<br/>
- **Decorator裝飾模式**<br/>
- **Façade外觀模式**<br/>
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

----

### Behavioral行為型模式
物件之間的合作行 為構成了程式最終的行為，物件之間若有設 計良好的行為互動，不僅使得程式執行時更有效率，更可以讓物件的職責更為清晰、整個程式的動態結構（像是物件調度）更有彈性。<br/>

- **Template Method樣板模式**<br/>
樣板方法模式：將一個演算法的骨架定義在一個父類別中，著重的是在父類別實作骨架，而將未實作抽象方法部份留待子類別來實作，在抽象父類別中定義好某個操作的整體流程，而在子類別中才將流程中一些未定的操作實現出來<br/>
在描述演算法流程輸廓時，並沒有提及如何顯示訊息、沒有提及如何取得使用者輸入等具體的作法，只是歸納出一些共同的流程步驟<br/>
Factory Method 模式將實際要建立的物件推遲至子類中決定，而 Template Method模式則是將框架中抽象的流程部份留待子類來解決<br/>
我們用泡茶和咖啡來解釋樣板方法模式，假設我們有以下兩個類別Coffee和Tea，我們可以看出兩個類別提供的方法，有很多類似的地方。<br/>
```C++
class Coffee{
public:
    void prepareRecipe(){
        boilWater();
        brewCoffeeGrinds();
        pourInCup();
    }
    void boilWater(){ cout << "煮開水" << endl; }
    void brewCoffeeGrinds(){ cout << "煮咖啡" << endl; }
    void pourInCup(){ cout << "倒入杯中" << endl; }
};

class Tea{
public:
    void prepareRecipe(){
        boilWater();
        steepTeaBag();
        pourInCup();
    }
    void boilWater(){ cout << "煮開水" << endl; }
    void steepTeaBag(){ cout << "泡茶" << endl; }
    void pourInCup(){ cout << "倒入杯中" << endl; }
};
```
創造一個Beverage類別，將Coffee和Tea類別相同的地方，抽取到Beverage類別內<br/>

```C++
#include <iostream>
using namespace std;

class Beverage{
public:
    void prepareRecipe(){
        boilWater();
        brew();
        pourInCup();
    }
    void boilWater(){ cout << "煮開水" << endl; }
    virtual void brew() = 0;
    void pourInCup(){ cout << "倒入杯中" << endl; }
};
class Coffee : public Beverage{
public:
    void brew(){ cout << "煮咖啡" << endl; }
};

class Tea : public Beverage{
public:
    void brew(){ cout << "泡茶" << endl; }
};

int main(){
    Coffee myCoffee;
    Tea myTea;
    myCoffee.prepareRecipe();
    myTea.prepareRecipe();
    return 0;
}
```
<br/>

- **Observer觀察者模式**<br/>
- **State狀態模式**<br/>
- **Strategy策略模式**<br/>
- **Command命令模式**<br/>
