# Facade Pattern
- 어떤 Sub-System의 일련의 인터페이스에 대한 통합된 인터페이스 제공
- 고수준 인터페이스를 정의하기 때문에 Sub-System을 더 쉽게 사용할 수 있음
## 문제 예시(HomeTheater)
### 해야할 일
```java
class WatcherA(){
    void watchMovie(){
        popcornMachine.on();
        popcornMachine.createPopcorn();
        
        light.off();
        
        screen.down();

        projector.on();
        projector.set(dvd);

        amp.on();

        dvd.play(movie);
        ...
    }
}

class WatcherB(){
    void watchMovie(){
        popcornMachine.on();
        popcornMachine.createPopcorn();
        
        light.off();
        
        screen.down();

        projector.on();
        projector.set(dvd);

        amp.on();

        dvd.play(movie);
        ...
    }
}
```
- 위와 같이 많은 class(팝콘 기계, 전등 스위치, 스크린, 프로젝터, 앰프, DVD 등)가 각자의 일들을 해야 함
- 영화를 켤 때 뿐만 아니라 끌 때에는 반대로 위의 일들을 해야 함

## Facade로 보다 쉬운 인터페이스 제공
```java
@AllArgsConstructor
class HomeTheaterFacade{
    Amp amp;
    DvdPlayer dvd;
    Projecter projector;
    Light light;
    PopcornMachine popcornMachine;
    Screen screen;
    
    void watchMovie();
    void endMovie();
    void listenToCd();
    endCd();
    listenToRadio();
    endRadio();
}

class WatchA(){
    HomeTheaterFacade homeTheater;
    void watchMovieA(){
        homeTheater = new HomeTheater(amp,dvd,...,screen);
        homeTheater.watchMovie();
    }
}

class WatchB(){
    HomeTheaterFacade homeTheater;
    void watchMovieB(){
        homeTheater = new HomeTheater(amp,dvd,...,screen);
        homeTheater.watchMovie();
    }
}
```
- 각각 Watcher들을 homeTheater 생성 후 watch만 하면 됨
- `최소 지식 원칙` 만족
## `최소 지식 원칙`(=데메테르의 법칙)
- 객체 사이의 상호작용은 될 수 있으면 `가장 가까운 관계만 허용`
```java
public float getTemp(){
    Thermometer thermometer = station.getThermometer();
    return thermometer.getTemperature();
} //최소 지식 원칙을 따르지 않은 경우

public float getTemp(){
    return station.getThermometer();
} //최소 지식 원칙을 따른 경우(가장 가까운 class인 station에서 결과 추출)
```