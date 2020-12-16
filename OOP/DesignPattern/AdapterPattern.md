# Adapter Pattern
- 나의 Class와 외부업체(오픈소스 등)의 클래스가 호환되지 않으므로 호환성을 위한 Adapter를 구성하는 것
- MyClass - Adapter(연결) - OpenSource
## 예시
- MyClass에서 누군가가 제공한 YourClass의 행위를 하고자 하는 경우
```java
class Client{
    
    private YourClassAdapter myToYourAdapter;
    
    public void doSomething(){
        ...
        myToYourAdapter.doTargetSomething();
        ...
    }
}

class Adapter{
    
    private Target target;
    
    public void doTargetSomething(){
        target.doSomething();    
    }
}

class Target{

    public void doSomething(){
        System.out.println("target did something");
    }    
}
```
- YourClassAdapter는 Adaptee인 YourClass를 Field로 가짐
- `호환성 문제로 인해 같이 쓸 수 없는` 클래스들을 연결하여 사용 가능 
- 다른 Class에서도 Adapter를 통한 Target 사용 가능
- 추가적인 요구사항 발생시 Adapter만 수정하여 사용 가능
