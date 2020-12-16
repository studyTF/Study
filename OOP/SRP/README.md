# Single Responsibility Principle
각 소프트웨어 모듈의 변경 이유는 `단 하나`이어야 한다.
## 오해
- 이름에서 비롯되어 한 모듈이 하나의 일만 해야 한다고 생각하기 쉬움
## 정확한 해석
- 하나의 모듈은 오직 `하나의 액터`에 대해서만 책임을 져야 한다.
- 액터 : 모듈의 변경을 요청하는 집단

## 위반 예시
### 1. 우연한 중복
- COO, CFO, CTO -> Employee[calculatePay, reportHours, save]
- Employee class는 COO, CFO, CTO 셋의 액터에 대한 책임을 가짐
```java
class Employee {
    public Long calculatePay(){
        ...
        Long regHours = regularHours();
        ...
    }

    public Long reportHours(){
        ...
        Long regHours = regularHours();
        ...
    }

    private Long regularHours(){
        ...
        return regHours;
    }
}
```
- 위 처럼 CFO가 사용하는 calculatePay()와 COO가 사용하는 reportHours()가 regularHours()를 공유
- 둘 중 `한 액터`가 regularHours의 로직을 변경하게 되면 큰 문제가 발생함

### 2. 병합
- 한 Class가 다양한 액터를 책임진다면, 병합이 발생할 가능성이 매우 높음
- CTO, CFO에 필요한 각각의 변경 사항을 각각 merge했다면 충돌이 발생

## 해결책
```java
class EmployeeData {
    //Data Class
}

class PayCalculator {
    
    private EmployeeData employeeData;
    public Long calculatePay(){
        ...
        doSomething(employeeData);
        return pay;
    }
}

class HourReporter {
    
    private EmployeeData employeeData;
    public Long reportHours(){
        ...
        doSomething(employeeData);
        return hours;
    }
}

class EmployeeSaver {
    
    private EmployeeData employeeData;
    public void saveEmployee(){
        ...
        save(employeeData);
    }
}
```
- 각 PayCalculator, HourReporter, EmployeeSaver class가 분리되어 서로의 존재를 모르고 Data Class만 사용하므로 중복에서 회피
### 단점
- 개발자가 세 가지 Class를 Instance화하여 추적해야 함.
### 해결책
#### [Facade Pattern](../DesignPattern/FacadePattern.md)
```java
class EmployeeFacade {
    
    private PayCalculator payCalculator;
    private HourReporter hourReporter;
    private EmployeeSaver employeeSaver;
    private EmployeeData employeeData;

    public Long calculatePay(){
        payCalculator = new PayCalculator(employeeData);
        return payCalculator.calculatePay();
    }

    public Long reportHours(){
        hourReporter = new HourReporter(employeeData);
        return hourReporter.reportHours();
    }

    public void saveEmployee(){
        employeeSaver = new EmployeeSaver(employeeData);
        employeeSaver.saveEmployee();
    }
}
```
- 세 Class에 대한 객체 생성 및 요청 메서드 위임하는 패턴
- (Facade Pattern)[../DesignPattern/FacadePattern.md]