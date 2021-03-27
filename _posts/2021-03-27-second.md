# CHAPTER 10. 객체와 클래스

숫자와 하수까지 파이썬의 모든것은 객체이다. 하지만 파이썬은 특수 구문을 이용해서 대부분의 객체를 숨긴다. num=7을 입력했을때 7이 담긴 정수 유형의 객체를 생성하고 객체 참조를 num에 할당한다. 이번장에서느 객체를 직접 만들고 기존 객체의 행동을 수정하면서 객체를 자세히 살펴보자

### 10.1 객체란 무엇인가?

 * 객체는 데이터(변수, **속성**)와 코드(함수,**메서드**)를 포험하는 커스텀 자료구조다
 * 객체는 어떤 구체적인 것의 유일한 인스턴스를 나타낸다
 * 객체를 명사로, 메서드를 동사로 생각하면 된다. 
 * 객체는 개별 사물을 나타내며 해당 메서드는 다른 사물과 상호작용하는 방법을 정의한다

### 10.2 간단한 객체

기본 객체클래스를 먼저 살펴보고, 상속에 대한 내용은 나중에 다룬다

##### 10.2.1 클래스 선언하기: class

아무도 만들어본 적이 없는 새 객체를 생성하기 위해서 객체에 포함된 내용을 나타내는 클래스를 정의한다
2장에서는 객체를 플라스틱 박스에 비유했다. 클래스는 상자를 만드는 틀에 비유할 수 있다. 예를 들어 문자열은 'cat', 'duck' 과 같은 문자열 객체를 만드는 내장된 클래스이다. 파이썬은 리스트, 딕셔너리 등을 포함한 다른 표준 데이터 타입을 생성하는 내장클래스가 많이 있다. 커스텀 객체를 생성하기 위해 먼저 class 키워드로 클래스를 정의한다. 간단한 예제로 살펴보자


```python
# 고양이에 대한 정보를 나타내는 객체를 정의한다고 가정해보자, 각 객체는 고양이 한 마리를 나타낸다. 먼저 객체의 틀로 Cat 클래스를 정의한다.

#빈클래스 생성

class Cat():
    pass
```


```python
class Car:
    pass
```

함수와 마찬가지로, 클래스가 비어있다는 것을 나타내기 위해 pass 를 사용했다. 이것은 객체를 생성하기 위한 최소한의 정의이다. 함수처럼 클래스 이름을 호출하여 클래스로부터 객체를 생성할 수 있다


```python
a_cat=Car()
another_cat=Cat()
```

Cat( )은 cat 클래스로부터 개별 객체를 생성한다. 그리고 이런 개체를 a_cat 과 another_cat 이름에 할당한다. 그러나 Cat 클래스는 빈 클래스이기 때문에 생성한 객체만 존재할 뿐 아무것도 할 수 없다.

##### 10.2.2 속성

속성은 클래스나 객체 내부이 변수이다. 객체나 클래스가 생성되는 동안이나 이후에 속성을 할당할 수 있다. 속성은 다른 개체일 수 있다. Cat 객체 두 개를 다시 생성해 보자


```python
class Cat:
    pass

a_cat=Cat()
a_cat
```




    <__main__.Cat at 0x10edcdd30>




```python
another_cat=Cat()
another_cat
```




    <__main__.Cat at 0x10edcdc40>



Cat 클래스를 정의할 때 해당 클래스에서 객체를 출력하는 부분을 작성하지 않았다. 이 경우 파이썬 이 알아서 <__main__.Cat at 0x10cec84c0>와 같은것을 출력한다. 이런 기본 동작을 변경하는 방법을 10.7절 (덕타이핑) 에서 다룬다


```python
#첫 번째 각체에 속성 세 개를 할당해보자
a_cat.age=3
a_cat.name="Mr. Fuzzybuttons"
a_cat.nemesis=another_cat
```


```python
a_cat.age
```




    3




```python
a_cat.name
```




    'Mr. Fuzzybuttons'




```python
a_cat.nemesis
```




    <__main__.Cat at 0x10edcdc40>




```python
 # nemesis 속성은 다른 Cat 객체를 참조하므로 a_cat.nemesis를 사용하여 접근할 수 있지만, 
               #다른 객체에서는 name 속성이 할당되지 않았다        
a_cat.nemesis.name
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-10-a1038f106a6e> in <module>
          1 # nemesis 속성은 다른 Cat 객체를 참조하므로 a_cat.nemesis를 사용하여 접근할 수 있지만,
          2               #다른 객체에서는 name 속성이 할당되지 않았다
    ----> 3 a_cat.nemesis.name
    

    AttributeError: 'Cat' object has no attribute 'name'



```python
#다른 객체에 name 속성을 할당한다

a_cat.nemesis.name="Mr. Bigglesworth"
a_cat.nemesis.name
```

이와 같은 간단한 객체에서도 여러 속성을 저장하는데 사용할 수 있다. 즉, 리스트나 딕셔너리와 같은 자료구조를 사용하는 대신 여러 객체를 사용하여 다른 값을 저장할 수 있다. **속성**을 이야기할 때, 일반적으로 객체 속성을 의미한다. **클래스 속성**도 있다. 10.4.6절에서 차이점을 살펴본다.

##### 10.2.3 메서드

**메서드** 는 클래스 또는 객체의 함수이다. 메서든느 다른 함수와 비슷하지면 10.5.3절과 10.6절에 있는 특별한 방식으로 사용할 수 있다.(프로퍼티,인스턴스메서드, 클래스메서드, 정적메소드) 이따 살펴보자

##### 10.2.4 초기화

객체를 생성할 때 속성을 할당하려면 객체 초기화 메소드 **__init__()** 를 사용한다.


```python
class Cat:
     def __init__(self):
        pass
```

위 코드는 실제 파이썬 클래스 정의에서 볼 수 있다. __init__()는 클래스 정의에서 개별 객체를 초기화하는 특수 메서드이다. self매개변수는 개별 객체 자신을 참조하도록 지정한다. 
클래스 정의에서 __init__()을 정의할 때 첫 번째 매개변수 이름은 **self**이어야 한다. **self**는 예약어는 아니지만 일반적으로 사용한다. 따라서 다른 사람이 코드를 읽을 때 무슨 뜻인지 추측할 필요가 없다, 
그러나 위 코드에서도 실제로 뭔가 수행하는 객체를 만들지 않았다. 다음 코드에서 간단한 객체를 생성하고, 한 속성을 할당한다. 이번에는 초기화 메서드에 매개변수 이름을 추가한다.


```python
class Cat:
    def __init__(self, name):
        self.name=name
```

이제 name 매개변수에 문자열을 전달하여 Cat 클래스로부터 객체를 생성할 수 있다.


```python
furball=Cat('Grumpy')
```

코드가 어떻게 동작하는지 살펴보자
 * Cat 클래스의 정의를 찾는다
 * 메모리에 새 객체를 **초기화(생성)** 한다.
 * 객체의 __init__ 메서드를 호출한다. 새롭게 생성된 객체를 self에 전달하고, 인수('Grumpy')를 name에 전달한다.
 * 객체에 name 값을 저장한다
 * 새 객체를 반환한다
 * furball 변수에 이 객체를 연결한다.
 
이 객체는 파이썬의 다른 객체의 생성과정과 같다. 이 객체는 리스트, 튜플, 딕셔너리, 또는 셋의 요소로 사용할 수 있다. 이 객체를 함수에 인수로 전달할 수 있고, 함수에서 그 결과를 반환 할 수 있다. 우리가 전달한 name에 무엇이 있는지 살펴보자. 이것은 객체의 속성에 저장되어 있다. 이 속성은 직접 읽고 쓸 수 있다.


```python
print('Our latest addition: ', furball.name)

```

Cat 클래스 정의에서 name 속성을 self.name으로 접근하는 것을 기억하자. furball과 같은 객체를 생성할 때 furball.name은 self.name을 참조한다. 

모든 클래스 정의에서 __init__()메서드를 가질 필요가 없다. __init__() 메서드는 같은 클래스에서 생성된 다른 객체를 구분하기 위해 필요한 다른 뭔가를 수행한다. __init__() 메서드는 다른 언어에서 부르는 '생성자' 개념이 아니다. __init__()메서드 호출 전에 이미 객체를 만들었기 때문이다. __init__() 메서드를 초기화 메서드라고 생각하자.

### 10.3 상속

 어떤 코딩 문제를 해결할때 필요한 기능 대부분을 수행하는 기존 클래스를 찾을 것이다. 그리고 기존 클래스에 필요한 기능을 추가할 것이다. 이때 어떻게 해야할까?
기존 클래스를 수정하면 클래스가 더 복잡해질것이고, 코드를 잘못 건드려 수행할 수 없게 만들 수 있다. 
 물론 기존 클래스를 자르고 붙여넣기로 새 클래스를 만들어서 새 코드에 병합할 수 있다. 그러나 이것은 우리가 관리해야할 코드가 더 많아진다는 것을 의미하기도 한다. 그리고 같은 일을 수행하는 기존 클래스와 새로운 클래스가 서로 다른곳에 있어서 혼란스러워질 수 있다. 
 이 문제는 상속으로 해결 할 수 있다. 기존 클래스에서 일부를 추가하거나 변경하여 새 클래스를 생성한다. 코드를 재사용 하는 아주 좋은 방법이다. **상속**을 이용하면 새로운 클래스는 기존 클래스를 복사하지 않고, 기존 클래스의 모든코드를 사용할 수 있다.

##### 10.3.1 부모클래스 상속받기

필요한 것만 추가하거나 변경해서 새 클래스를 정의한다. 그리고 기존 클래스의 행동을 오버라이드(재정의)한다. 기존 클래스는 **부모**클래스, **슈퍼**클래스, **베이스**클래스라고 부른다. 새 클래스는 **자식**클래스, **서브**클래스, **파생된**클래스라고 부른다. 이 용어들은 객체 지향 프로그래밍에서 다르게 사용될 수 있다. 다음예제에서 상속을 사용해보자


```python
# 빈 클래스 Car 을 정의한다. 그리고 Car의 서브클래스 Yugo를 정의한다. 서브클래스 같은 class 키워드를 사용하지만, 괄호안에 부모클래스의 이름을 지정한다
class Car():
    pass

class Yugo(Car):
    pass

```

issubclass함수를 사용해 다른 클래스에서 파생되었는지 확인할 수 있다


```python
issubclass(Yugo, Car) 
```

그다음, 각 클래스로부터 객체를 생성한다. 


```python
give_me_a_car=Car()
give_me_a_yugo=Yugo()
```

자식클래슨느 부모클래스를 구체화한 것이다. 객체 지향 용어로 Yugo 는 Car dlek. give_me_a_yugo 객체는 Yugo클래스의 인스턴스이고, Car클래스가 할 수 있는 것을 상속받는다. 


```python
class Car():
    def exclaim(self):
        print("I'm a Car!")
        
class Yugo(Car):
    pass
```

마지막으로, 클래스로부터 객체를 만들고 exclaim( ) 메서드를 호출한다


```python
give_me_a_car=Car()
give_me_a_yugo=Yugo()
give_me_a_car.exclaim()
give_me_a_yugo.exclaim()
```

Yugo는 특별한 일을 하지않고 Car로 부터 exclaim() 메서드를 상속받았다. Yugo는 자신이 Car이라고 말하고 있다. Yugo의 정체성이 불분명해 보인다. 이를 위해 무엇을 할 수 있는지 다음절에서 살펴본다.

##### 10.3.2 메서드 오버라이드

이전 절의 예제에서 본 것 처럼 새 클래스는 부모 클래스로부터 모든 것을 상속받는다. 좀 더 나아가서 부모 메서드를 어떻게 오버라이드(대체) 하는지 살펴볼 것이다. Yugo는 아마다 어떤 식으로든 Car와 달라야 한다. 그렇지 않으면 새로운 클래스를 정의하는 것이 무슨 의미가 있겠는가? Yugo클래스에서 exclaim()메서드를 추가해보자


```python
class Car():
    def exclaim(self):
        print("I'm a Car!")
        
class Yugo(Car):
    def exclaim(self):
        print("I'm a Yugo! Much like a Car, but more Yugo-ish.")
```


```python
#두개의 클래스를 생성한다

give_me_a_car=Car()
give_me_a_yugo=Yugo()
```


```python
#각 객체의 exclaim()메서드를 호출한다

give_me_a_car.exclaim()
give_me_a_yugo.exclaim()

```

이 예제에서는 exclaim()메서드를 오버라이드 했다. __init__() 메서드를 포함한 모든 메소드를 오버라이드 할 수 있다. 이어서 Person클래스 사용한 또 다른 예를 설명할 것이다. 의사를 나타내는 MDPerson 과 변호사를 나타내는 JDPerson 서브클래스를 만들어보자


```python
class Person():
    def __init__(self, name):
        self.name=name
        
class MDPerson(Person):
    def __init__(self, name):
        self.name="Doctor"+name
        
class JDPerson(Person):
    def __init__(self, name):
        self.name=name+",Esquire"
```

이러한 경우 __init__() 초기화 메서드는 부모 클래스의 Person과 같은 인수를 취하지만, 객체의 인스턴스 내부에서는 다른 name값을 저장한다


```python
person=Person('Fudd')
doctor=MDPerson('Fudd')
lawyer=JDPerson('Fudd')
print(person.name)
print(doctor.name)
print(lawyer.name)
```

##### 10.3.3 메서드 추가하기

자식 클래스도 부모 클래스에 없는 메서드를 **추가** 할 수 있다. Car 클래스와 Yugo 클래스로 돌아가서 Yugo클래스에만 있는 새로운 메서드 need_a_push()를 정의해보자.


```python
class Car():
    def exclaim(self):
        print("I'm a Car!")
        
class Yugo(Car):
    def exclaim(self):
        print("I'm a Yugo! Much like a Car, but more Yugo-ish.")
    def need_a_push(self):
        print("A little help here?")
```


```python
# Car와 Yugo의 객체를 생성한다
give_me_a_car=Car()
give_me_a_yugo=Yugo()

```


```python
#yugo의 객체는 need_a_push() 메서드를 호출해 대답할 수 있다.

give_me_a_yugo.need_a_push()
```


```python
#그러나 제네릭 Car 객체는 그렇게 할 수 없다 (오류뜸)

give_me_a_car.need_a_push()

```

yugo는 Car가 하지 못하는 뭔가를 할 수 있으며, Yogo의 독특한 개성을 나타낼 수 있다.

##### 10.3.4 부모에게 도움받기: super()

지금까지 자식 클래스에서 메서드를 추가하거나 부모 클래스로부터 메서드를 오버라이드 하는 방법을 살펴봤다. 자식 클래스에서 부모 클래스를 호출하고 싶다면 어떻게 해야할까? **super( )** 메서드를 사용하면 된다. 이메일 주소를 가진 Person 클래스를 나타내는 EmailPerson이라는 새로운 클래스를 정의한다. 우선, 우리에게 친숙한 Person클래스를 정의해보자


```python
class Person():
    def __init__(self,name):
        self.name=name
```


```python
# 서브클래스의 __init__()메서드에 email 매개변수를 추가했다.

class EmailPerson(Person):
    def __init__(self,name,email):
        super().__init__(name)
        self.email=email
```

자식클래스에서 __init__()메서드를 정의하면 부모클래스의 __init__()메서드를 대체하는것이기 때문에 더 이상 자동으로 부모클래스의 __init__()메서드가 호출되지 않는다. 그러므로 이것을 명시적으로 호출해야한다. 코드에서 무슨 일이 일어나는지 살펴보자.

 * super() 메서든느 부모클래스(person)의 정의를 얻는다.
 
 
 * __init__()메서드는 Person.__init__() 메서드를 호출한다. 이 메서드는 self 인수를 슈퍼 클래스로 전달하는 역할을 한다. 그러므로 슈퍼 클래스에 선택적 인스를 제공하기만 하면 된다. 이 경우 Person()에서 받는 인수는 name 이다.
 
 
 * self.email=email은 EmailPerson 클래스를 Person클래스와 다르게 만들어주는 새로운 코드다.

계속해서 EmailPerson객체를 만들어보자


```python
bob=EmailPerson('Bob Frapples', 'bob@frapples.com')
```


```python
#객체의 name과 email 속성에 접근할 수 있다.

bob.name
```


```python
bob.email
```

왜 자식 클래스에서 다음과 같이 정의하지 않을까?


```python
class EmailPerson(Person):
    def __init__(Self, name,email):
        self.name=name
        self.email=email
```

위와 같이 정의할 수 있지만, 이것은 상속의 이점을 활용할 수 없다. 위에서 super()메서드를 사용하여 Person 클래스에서 일반 Person객체와 같은 방식으로 동작하게 만들었다. 
 super()메서드에 대해 또 다른 이점이 있다. Person클새스의 정의가 나중에 바뀌면 Person클래스로부터 상속받는 EmailPerson클래스의 속성과 메서드에 변경 사항이 반영된다
 자식클래스가 자신의 방식으로 무언가를 처리하지만, 여전히 부모클래스로부터 무언가가 필요할 때(현실의 부모와 자식관계처럼) super()메서드를 활용한다.

##### 10.3.5 다중상속

앞에서는 일반클래스와 부모클래스를 상속한 예제를 살펴봤다. 실제로 객체는 여러 부모 클래스를 상속받을 수 있다. 클래스가 가지고 있지 않은 메서드 또는 속성을 참조하면 파이썬은 모든 부모 클래스를 조사한다. 두 부모 클래스에서 같은 이름을 가진 경우 어떻게 될까? 누구의 것을 상속받을까?

 파이썬의 상속은 **메서드 해석순서(MRO)** 에달려있다. 각 파이썬 클래스에는 특수 메서드 mro()가 있다. 이 메서드는 해당 클래스 객체에 대한 메서드 또는 속성을 찾는데 필요한 클래스의 리스트를 반환한다. __mro__라는 유사한 속성은 해당 클래스의 튜플이다. 위 경우 먼저 선언된 부모 클래스를 상속받는다. 
 
 다음예제에서 최상의 클래스 Animal, 두 하위 클래스 Horse, Donkey를 정의한 후, 두 하위 클래스를 상속 받는 클래스를 만든다


```python
class Animal:
    def says(self):
        return 'I speak!'
    
class Horse(Animal):
    def says(self):
        return 'Neigh!'
    
class Donkey(Animal):
    def says(self):
        return 'Hee-haw!'
    
class Mule(Donkey, Horse):
    pass

class Hinny(Horse, Donkey):
    pass
```

**Mule** 클래스에서 메서드나 속성을 찾을 때 순서는 다음과 같다

 1. 객체자신(Mule)타입
 2. 객체의 클래스(Mule)
 3. 클래스의 첫 번째 부모 클래스(Donkey)
 4. 클래스의 두 번째 부모 클래스(Horse)
 5. 부모의 부모 클래스(Animal)

Donkey클래스와 Horse클래스의 선언 순서를 제외하고 Hinny클래스도 위와 같이 동작한다.


```python
Mule.mro()
[<class '__main__.Mule'>, <class '__main__.Donkey'>, <class '__main__.Horse'>, <class '__main__.Animal'>, <class 'object'>]
Hinny.mro()
[<class '__main__.Hinny'>, <class '__main__.Horse'>, <class '__main__.Donkey'>, <class '__main__.Animal'>, <class 'object'>]
```


```python
mule=Mule()
hinny=Hinny()
mule.says()
```


```python
hinny.says()
```

상속에서 부모 클래스를 엄마, 아빠 순서대로 나열하고, 자식 클래스에서 엄마, 아빠가 가진 같은 이름이 메서드나 속성을 호출한다면 엄마처럼 행동한다. 
**Horse**나 **Donkey**클래스에서 says() 메서드를 가지고 있지 않다면, **mule**이나 **hinny**객체는 부모의 부모인 **Animal** 클래스를 사용하여 **'I speak!'** 를 반환한다.

##### 10.3.6 믹스인

클래스 정의에 부모 클래스를 추가하여 상속받을 수 있다. 그러나 이를 헬퍼의 목적으로만 사용할 수 있다. 즉, 다른 상위 클래스와 메서드를 공유하지 않으며 이전 절에서 언급한 메서드 해석 순서의 모호성을 피한다. 이러한 부모클래스를 **믹스인** 클래스라고 한다. 로깅과 같은 '사이드'작업에서 이를 사용 할 수 있다. 다음 예제는 객체 속성을 출력하는 믹스인 클래스이다. 


```python
class PrettyMixin():
    def dump(self):
        import pprint
        pprint.pprint(vars(self))
        
class Thing(PrettyMixin):
    pass

t=Thing()
t.name="Nyarlathotep"
t.feature="ichor"
t.age="eldritch"
t.dump()

```

##### 10.4 자신: self

파이썬에서(공백 사용 외에) 어떤 한 비판은 인스턴스 메서드(이전 예제어서 봤던 메서드의 종류)의 첫 번째 인수를 self를 포함해야 한다는 것이다. 파이썬은 적절한 객체의 속성과 메서드를 찾기 위해 self 인수를 사용한다. 다음 예제에서 객체의 메서드를 어떻게 호출하고, 파이썬에서 실제로 은밀하게 무엇을 처리하는지 살펴보자


```python
# 이전 예제의 Car클래스에서 exclaim()메서드를 다시 호출해보자

a_car=Car()
a_car.exclaim()
```

파이썬이 은밀하게 처리하는 일은 다음과 같다

 * a_car 객체의 Car 클래스를 찾는다
 * a_car 객체를 Car 클래스 exclaim() 메서드의 self매개변수에 전달한다.

단지 재미로, 다음과 같은 방법으로 메서드를 실행할 수 있다. 이것은 일반 car.exclaim()구문과 똑같이 동작한다.


```python
Car.exclaim(a_car)
```

하지만 굳이 이렇게 더 긴 구문을 사용할 이유가 없다.

### 10.5 속성 접근

파이썬은 일반적으로 객체 속성과 메서드는 공개되어 있어서, 이를 개발자가 스스로 잘 관리 해야한다(이를 '동의 성인' 정책이라고 부른다). 이번 절에서는 직접 접근 방식과 일부 대안을 살펴본다.

##### 10.5.1 직접접근

이전 예제에서 살펴봤듯이, 속성 값을 직접 가져와서 설정할 수 있다.


```python
class Duck:
    def __init__(self, input_name):
        self.name=input_name
        
fowl=Duck('Daffy')
fowl.name
```

그러나 누군가 잘못 수정하면 어떻게 될까?


```python
fowl.name='Daphne'
fowl.name
```

다음 두 절에서는 실수로 어떤 개발자가 위 예제와 같이 수정하지 못하도록 속성에 대한 접근 프라이버서를 얻는 방법을 살펴본다.

##### 10.5.2 Getter/Setter 메서드

어떤 객체 지향 언어에서는 외부로부터 바로 접근할 수 없는 **private** 객체 속성을 지원한다. 개발자는 private 속성의 값을 읽고 쓰기 위해 **getter/setter**메서드를 사용한다
 
 파이썬에서는 private 속성이 없지만 조슴의 프라이버스를 얻기 위해서 애매한 속성 이름을 가진 Getter/Setter 메서드를 작성할 수 있다(가장 좋은 해결책은 다음 절에서 살펴볼 **프로퍼티**를 사용하는 것이다)
 
  다음 예제에서는 **hidden_name** 이라는 속성으로 **Duck** 클래스를 정의한다. 이 속성ㅇ르 외부에서 직접 접근하지 못하도록 getter(**get_name()**)과 setter(**set_name()**)메서드를 정의한다. 각 메서드가 언제 호출되는지 알아보기 위해 **print(  )함수**를 추가한다


```python
class Duck():
    def __init__(self, input_name):
        self.hidden_name=input_name
    def get_name(self):
        print('inside the getter')
        return self.hidden_name
    def set_name(self, input_name):
        print('inside the setter')
        self.hidden_name=input_name
        
don = Duck('Donald')
don.get_name()
don.set_name('Donna')
don.get_name()
```

##### 10.5.3 속성 접근을 위한 프로퍼티

속성 프라이버시를 위한 파이써닉한 방법은 **프로퍼치**를 사용하는 것이다. 
 두 방법으로 프로퍼티를 사용할 수 있다. 첫 번째 방법으로 먼저 **name=property(get_name, set_name)** 구문을 클래스 정의 마지막 줄에 추가한다.


```python
class Duck():
    def __init__(self, input_name):
        self.hidden_name=input_name
    def get_name(self):
        print('inside the getter')
        return self.hidden_name
    def set_name(self, input_name):
        print('inside the setter')
        self.hidden_name=input_name
        
    name=property(get_name, set_name)    
```

Getter/Setter 메서드는 여전히 동작한다.


```python
don = Duck('Donald')
don.get_name()
don.set_name('Donna')
don.get_name()
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-11-d8f11c3391e0> in <module>
    ----> 1 don = Duck('Donald')
          2 don.get_name()
          3 don.set_name('Donna')
          4 don.get_name()


    NameError: name 'Duck' is not defined


그러나 이제 속성 이름을 사용하여 hidden_name 속성을 가져오거나 설정할 수 있다.


```python
don = Duck('Donald')
don.name
don.name='Donna'
don.name
```

두 번째 방법은 데커레이터를 추가하고, 두 메서드 이름(get_name과 set_name)을 name으로 변경한다

  * getter메서드 앞에 @property 데커레이터를 쓴다
  * setter메서드 앞에 @name.setter 데커레이터를 쓴다

다음은 데커레이터를 사용한 코드다


```python
class Duck():
    def __init__(self, input_name):
        self.hidden_name=input_name
    @property
    def name(self):
        print('inside the getter')
        return self.hidden_name
    @name.setter
    def name(self, input_name):
        print('inside the setter')
        self.hidden_name=input_name
```


```python
#속성처럼 name에 접근 할 수 있다

fowl=Duck('Howard')
fowl.name
fowl.name='Donald'
fowl.name
```

##### 10.5.4 계산된 값의 프로퍼티

이전 예제에서는 객체에 저장된 속성(hidden_name)을 참조하기 위해 name 프로퍼티를 사용했다. 프로퍼티는 **계산된 값**을 참조할 수 있다. radius속성과 계산된 diameter프로퍼티를 가진 Circle클래스를 정의해보자 


```python
class Circle():
    def __init__(self, radius):
        self.radius=radius
        @property
        def diameter(self):
            return 2 * self.radius
```


```python
# radius 속성의 초깃값 5와 Circle 객체를 만든다
c=Circle(5)
c.radius
```


```python
#radius와 같은 속성을 계산된 diameter 프로퍼티로 참조할 수 있다. 
c.diameter
```


```python
#radius 속성은 언제든지 바꿀 수 있다. 그리고 diameter 프로퍼티는 현자 radius 값으로부터 계산된다

c.radius=7

```


```python
c.diameter
```

속성에 대한 setter 프로퍼티를 명시하지 않았다면 외부로부터 이 속성을 설정할 수 없다. 이것은 읽기전용 속성이다


```python
c.diameter=20
Traceback(most call last): #오류뜸
    
    
```

속성을 직접 접근하는 것보다 프로퍼티로 접근하면 여려 이점이 있다. 속성의 정의를 바꾼다면 모든 호출자를 수정할 필요 없이 클래스 정의에 있는 코드만 수정하면 된다.

##### 10.5.5 프라이버시를 위한 네임 맹글링

이전 절의 Duck 클래 예제에서 (완전하지 않지만) 숨겨진 hidden_name 속성을 호출했다. 파이썬은 클래스 정의 외부에서 볼 수 없도록 하는 속성에 대한 네이밍 컨벤션이 있다. 속성 이름 앞에 두 언더바(__)를 붙이면 된다. 


다음과 같이 hidden_name을 __name으로 바꿔보자


```python
class Duck():
    def __init__(self, input_name):
        self.__name=input_name
        @property
        def name(self):
            print('inside the getter')
            return self.__name
        @name.setter
        def name(self, input_name):
            print('inside the setter')
            self.__name=input_name
```

작성한 코드가 잘 동작하는지 살펴보자


```python
fowl= Duck('Howard')
fowl.name
```


```python
fowl.name= 'Donald'
```


```python
fowl.__name
```

아무런 문제가 없어 보인다. 그러나 __name 속성에 바로 접근 할 수 없다


```python
fowl.__name #오류뜸
```

이 네이밍 컨벤션은 속성을 private로 만들지 않지만, 파이썬은 이 속성이 우연히 외부 코드에서 발견할 수 없도록 이름을 **맹글링**이라 했다. 사실 다음과 같이 접근할 수 있다.


```python
fowl._Duck__name
```

inside the getter를 출력하지 않았다. 비록 이것이 속성을 완벽하게 보호할 수는 없지만, 네임 맹글링은 속성의 의도적인 직접 접근ㅇ르 어렵게 만든다

##### 10.5.6 클래스와 객체 속성

클래스에 속성을 할당할 수 있고 해당 속성은 자식 객체로 상속된다


```python
class Fruit:
    color= 'red'
    
blueberry=Fruit()
Fruit.color
```


```python
blueberry.color
```

그러나 자식 객체의 속성을 변경하면 클래스 속성에 영향을 미치지 않는다


```python
blueberry.color= 'blue'
blueberry.color
```


```python
Fruit.color
```

나중에 클래스 속성을 변경해도 기존 자식 객체에는 영향을 미치지 않는다.


```python
Fruit.color= 'orange'
Fruit.color
```


```python
blueberry.color
```

But it will affect new ones


```python
new_fruit= Fruit()
new_fruit.color
```

### 10.6 메서드 타입

어떤 메서드는 클래스의 일부이고, 어떤 메서드는 해당 클래스에서 작성된 객체의 일부이다. 어떤 메서드는 두 사항에 어느 것도 해당하지 않는다. 

 * 메서드 앞에 데커레이터가 없다면 이것은 **인스턴스 메서드**이다. 첫 번째 인수는 객체 자신을 참조하는 self이다.
 * 메서드 앞에 @classmethod 데커레이터가 있다믄 **클래스 메서드** 이다. 첫 번째 인수는 cls(또는 예약어인 class가 이닌 다른것) 이다. 클래스 자체를 참조한다
 * 메서드 앞에 @staticmethod 데커레이터가 있다면 **정적 메서드**이다. 첫 번쨰 인수는 위와 같이 자시느이 객체나 클래스가 아니다
 
 이어지는 절에서 자세하게 다룰 것이다.

##### 10.6.1 인스턴스 메서드

클래스 정의에서 메서드의 첫 번째 인수가 self라면 이 메서드는 **인스턴스 메서드** 이다. 이것은 일반적인 클래스를 생성할 때의 메서드 타입이다. 인스턴스 메서드의 첫 번째 매개변수는 self이고, 파이썬은 이 메서드를 호출할 때 객체를 전달한다. 인스턴스 메서드는 지금까지 예제에서 본 메서드이다.

##### 10.6.2 클래스 메서드

대조적으로 **클래스 메서드**는 클래스 전체에 영향을 미친다. 클래스에 대한 어떤 변화는 모든 객체에 영향을 미친다. 클래스 정의에서 함수에 @classmethod 데커레이터가 있다면 이것은 클래스 메서드이다. 또한 이 메서드의 첫 번째 매개변수는 클래스 자신이다. 파이썬에서는 보통 이 클래스의 매개변수를 **cls**로 쓴다. class는 예약어라서 사용할 수 없다. A 클래스에서 객체 인스턴스가 몇 개 만들어졌는지 알아보는 클래스 메서드를 정의해보자.


```python
class A():
    count=0
    def __init__(self):
        A.count +=1
    def exclaim(Self):
        print("I'm an A !")
    @classmethod
    def kids(cls):
        print("A has", cls.count, "little objects.")
```


```python
easy_a=A()
breezy_a=A()
wheezy_a=A()
A.kids()
```

self.count(객체 인스턴스 속성)을 참조하지 않고 A.count(클래스 속성)을 참조했다 kids()메서드에서 A.count를 사용하지 않고 cls.count를 사용했다.

### 10.7 덕 타이핑

파이썬은 **다형성**을 느슨하게 구현했다. 이것은 클래스에 상관없이 같은 동작을 다른 객체에 적용할 수 있다는 것을 의미한다. 새 Quote클래스 같은 __init__() 이니셜라이저를 사용해보자. 클래스에 다음 두 메서드를 추가한다. 

 * who() 메서드는 저장된 person 문자열의 값을 반환한다.
 * say() 메서드는 특정 구두점과 함께 저장된 words 문자열을 반환한다.
 
다음과 같이 구현하자 


```python
class Quote():
    def __init__(self, person, words):
        self.person=person
        self.words=words
        def who(self):
            return self.person
        def says(self):
            return self.words+'.'
class QuestionQuote(Quote):
    def says(self):
        return self.words + '?'
    
class ExclamationQuote(Quote):
    def says(self):
        return self.words + '!'    
```

QuestionQuote 와 ExclamationQuote 클래스에서 초기화 함수를 쓰지 않았다. 그러므로 부모의 __init__() 메서드를 오버라이드하지 않는다. 파이썬은 자동으로 부모 클래스의 Quote의 __init__()메서드를 호출해서 인스턴스 변수 person과 words를 저장한다. 그러므로 자식 클래스 QuestionQuote 와 ExclamationQuote 에서 생성된 객체의 self.words에 접근할 수 있다.

객체를 만들어서 결과를 살펴보자


```python
hunter=Quote('Elmer Fudd', "I'm hunting wabbits")
print(hunter.who(), 'says:', hunter.says())
```


```python
hunted1= QuestionQuote('Bugs Bunny', "What's up, doc")
print(hunted1.who(), 'says:', hunted1.says())
```


```python
hunted2= ExclamationQuote('Daffy Duck', "It's rabbit season")
print(hunted2.who(), 'says:', hunted2.says())
```

세 개의 서로 다른 says() 메서드는 세 클래스에 대하 서로 다른 동작을 제공한다. 이것은 객체 지향 언어에서 전통적인 다형성의 특징이다. 더 나아가 파이썬은 **who()** 와 **says()** 메서드를 갖고 있는 모든 객체에서 이 메서드를 실행할 수 있게 해준다. **Quote 클래스**와 관계없는 BabblingBrook 클래스를 정의해보자


```python
class BabblingBrook():
    def who(self):
        return 'Brook'
    def says(self):
        return 'Babble'
    
brook= BabblingBrook()
```

다음 함수에서 obj 인수와 who()와 say() 메서드를 실행해보자


```python
def who_says(obj):
    print(obj.who(), 'says', obj.says())
    
```


```python
who_says(hunter)
```


```python
who_says(hunted1)
```


```python
who_says(hunted2)
```


```python
who_says(brook)
```

brook 객체는 다른 객체와 전혀 관계없다. 예전부터 이러한 행위를 덕 타이핑이라고 불렀다

### 10.8 매직 메서드

기본적인 객체를 생성하고 사용할 수 있다. 이번 절에서는 조금 더 재미있는걸 배운다. 

a=3+8 과 같은 무언가를 입력했을 때, 값 3과 8이 정수 객체고 + 기호로 더하라는 것을 어떻게 알까? 그리고 name= "Daffy"+""+"Duck"을 입력하면 문자열을 연결한다는 것을 어떻게 알까? 또한 =기호를 사용하여 어떻게 결과를 얻을까? 파이썬의 특수 메서드(매직메서드)를 이용하여 이러한 연산자를 사용할 수 있다. 

이 메서드의 이름은 두 언더바(__)로 시작하고 끝난다. 왜 그럴까? 이 이름은 개발자가 이렇게 변수 이름을 짓지 않을 것이다. 위에서 이미 __init__()메서드를 사용했다. 이 메서드는 클래스의 정의로부터 생성된 새로운 객체를 초기화하고, 어떤 인수를 전달받는다. 간단한 Word클래스와 두 단어를 비교(대소문자무시)하는 equals()메서드가 있다고 가정한다. 즉, 'ha'와 'HA'는 같은 단어로 간주한다.

다음 첫 번째 예제는 평범한 메서드 equals()를 사용한다. self.text는 Word 객체의 문자열이다. 그리고 equals()메서드는 text와 word2(다른Word객체)의 텍스트 문자열을 비교한다. 


```python
class Word():
    def __init__(self, text):
        self.text=text
    def equals(self, word2):
        return self.text.lower()==word2.text.lower()
```


```python
#세 개의 서로 다른 텍스트 문자열로 Word 객체를 생성한다.
first= Word('ha')
second= Word('HA')
third= Word('eh')
```


```python
#문자열 'ha' 와 'HA'를 소문자로 바꾸면 이 둘은 똑같다
first.equals(second)
```


```python
#문자열 'eh'와 'ha'는 다르다
first.equals(third)
```

문자열을 소문자로 바꿔서 비교하는 equals()메서드를 정의했다. 파이썬의 내장된 타입처럼 first==second와 같이 비교했다면 좋다. 이렇게 구현해보자. equal()메서드를 특수 이름의 __eq__()메서드로 바꿔보자


```python
class Word():
    def __init__(self, text):
        self.text=text
    __eq__(self, word2):
        return self.text.lower()==word2.text.lower()
```


```python
#코드가 잘 동작하는지 살펴보자
first= Word('ha')
second=Word('HA')
third=Word('eh')
first==second
```


```python
first==third
```

__eq__()는 같은지 판별하는 파이썬의 특수 메서드 이름이다. [표 10-1] 과 [표 10-2]에 유용한 매직 메서드의 이름이 나열되어 있다 (p.271 참조)

+(__add__() 마법 메서드)와 -(__sub__() 마법 메서드)같은 산술 연산자의 사용에는 제한이 없다. 예를 들어 파이썬의 문자열 객체는 연결을 위해 +연산자를 쓰고, 복제를 위해 * 연산자를 쓴다. 많은 특수 메소드 이름이 파이썬 공식 웹페이지에 문서화 되어 있따. 그 외 일반적인 메서든느 [표 10-3]을 참조한다.(p.272 표 참조)

__init__() 외에도 __str__()을 사용하여 객체를 문자열로 출력하는 우리만의 메서드를 만들 수 있다. 5장에서 배운 문자열 포매터와 print(), str()을 사용하면 된다. 대화식 인터프리터는 변수 결과를 출력하기 위해 __repr__()함수를 사용한다. __str__() EHSMS __repr__()을 정의되어있지 않다면 객체의 기본 문자열을 출력한다. 


```python
first=word('ha')
first
```


```python
print(first)
```

__str__()과 __repr__()메서드를 추가하여 Word 클래스를 예쁘게 만들어보자


```python
class Word():
    def __init__ (self, text):
        self.text=text
    def __eq__ (self, word2):
        return self.text.lower()==word2.text.lower()
    def __str__ (self):
        return self.text
    def __repr__(self):
        return 'Word("'+ self.text+'")'
```


```python
first=Word('ha')
# __repr__() 호출
first 
```


```python
#__str__() 호출
print(first)
```

매직 메서드를 조금 더 알고 싶다면 파이썬 문서를 참조한다

### 10.9 에그리게이션과 콤퍼지션

자식 클래스가 부모 클래스처럼 행동하고 싶을 때, 상속은 좋은 기숙이다(자식 is-a 부모). 개발자는 정교한 상속 계층구조에 유혹될 수 있지만, **콤퍼지션** 혹은 **애그리게이션(X has-a Y)** 의 사용이 더 적절한 경우가 있다. 오리는 조류이지만(오리 is-a 조류ㅡ 상속), 꼬리를 갖고 있다(오리 has- a 꼬리, 콤퍼지션), 꼬리는 오리에 속하지 않지만 오리의 일부다. 다음예제는 부리(bill) 과 꼬리(tail) 객체를 만들어서 새로운 오리(Duck)객체에 부여해보자.


```python
class Bill():
    def __init__(self, description):
        self.description=description
        
class Tail():
    def __init__(self, length):
        self.length=length
        
class Duck():
    def __init__(self, bill, tail):
        self.bill=bill
        self.tail=tail
    def about(self):
        print('This duck has a', self.bill.description, 'bill and a', self.tail.length, 'tail')
        
        
```


```python
a_tail=Tail('long')
a_bill=Bill('wide orange')
duck=Duck(a_bill, a_tail)
duck.about()
```

에그리게이션은 관계를 표현하지만 조금 더 느슨해진다. 한 객체는 다른 객체를 사용하지만, 둘 다 독립적으로 존재한다. 오리는 어느 한 호수에 있지만, 다른 호수에는 오리가 없다(호수는 오리의 일부가 아니다).

### 10.10 객체는 언제 사용할까?

클래스, 모듈(11장 참조)의 사용 지침은 다음과 같다

 * 비슷한 행동(메서드)을 하지만 내부 상태(속성)가 다른 개별 인스턴스가 필요할 떄, 객체는 매우 유용하다.
 
 * 클래스는 상속을 지원하지만, 모듈은 상속을 지원하지 않는다.
 
 * 어떤 한 가지 일만 수향한다면 모듈이 가장 좋은 선택일 것이다. 프로그램에서 파이썬 모듈이 참조된 횟수에 상관없이 단 하나의 복사본만 불러온다(자바와 C++개발자는 파이썬 모듈을 싱클톤처럼 쓸 수 있다)
 
 * 여러 함수에 인수로 전달하는 여러 변수가 있다면, 클래스를 정의한느 것이 더 좋다. 예를 들어 화상 이미지를 나타내기 위해 size나 color를 딕셔너리의 키로 사용한다고 가정해보자. 프로그램에서 각 이미지에 대한 딕셔너리를 생성하고, scale()과 transform()같은 함수에 인수를 전달할 수 있다. 키와 함수를 추가하면 코드가 지저분해질 수도 있다. size와 color를 속성으로 하고 scale()과 transform()을 메서드로 하는 이미지 클래스를 정의하는것이 더 일관성이 있다. 색상 이미지에 대한 모든 데이터와 메서드를 한 곳에 정의할 수 있기 때문이다. 
 
 * 가장 간단한 문제 해결법을 사용한다. 딕셔너리, 리스트, 튜플은 모듈보다 더 작고 간단하며 빠르다. 그리고 일반적으로 모듈은 클래스보다 더 간단하다.
 
 * 새로운 대안은 데이터클래스이다(10.12절 참조)

### 10.11 네임드 튜플

이전 절에서 귀도가 **네임드 튜플**을 언급했기 때문에 네임드 튜플을 설명할 것이다. 네임드 튜플은 튜플의 서브클래스이다. 이룸(.name)과 위치([offset])로 값에 접근할 수 있다. 

이전 절의 예제를 활용하자. Duck클래스를 네임드 튜플로, bill과 tail을 간단한 문자열 속성으로 변환한다. 그리고 두 인수를 취하는 namedtuple함수를 호출한다.

 * 이름
 * 스페이스로 구분된 필드 이름 문자열
 
네임드 튜플을 쓰기 전에 모듈을 불러와야한다. 다음 예제의 첫 번째 줄에서 namedtuple을 불러오고 있다.


```python
from collections import namedtuple
Duck= namedtuple('Duck', 'bill tail')
duck=Duck('wide orange', 'long')
duck
```


```python
duck.bill
```


```python
duck.tail
```


```python
#또한 딕셔너리에서 네임드 튜플을 만들 수 있다

parts={'bill':'wide orange', 'tail':'long'}
duck2=Duck(**parts)
duck2
```

**parts는 **키워드인수**이다 parts 딕셔너리에서 키와 값을 추출하여 Duck()의 인수로 제공한다. 다음예제와 효과가 같다


```python
duck2=Duck(bill='wide orange', tail='long')
```

네임드 튜플은 불변이다. 하지만 필드를 바꿔서 또 다른 네임드 튜플을 반환할 수 있다


```python
duck3= duck2._replace(tail='magnificent', bill='crushing')
duck3
```

duck을 딕셔너리로 정의한다


```python
duck_dict={'bill':'wide orange', 'tail':'long'}
duck_dict
```

딕셔너리에 필드를 추가한다


```python
duck_dict['color']='green'
duck_dict
```

딕셔너리는 네임드 튜플이 아니다


```python
duck.color='green' #오류
```

네임드 튜플의 특징을 정리하면 다음과 같다
 * 불변객체처럼 행동한다
 * 객체보다 공간 효율성과 시간 효율성이 더 좋다
 * 딕셔너리 형식의 대괄호([])대신, 온점(.)표기법으로 속성을 접근할 수 있다.
 * 네임드 튜플을 딕셔너리의 키처럼 쓸 수 있다

### 10.12 데이터 클래스

많은 개발자는 행동(메서드)가 아니라 주로 데이터(속성)을 저장하기 위해 객체를 생성하는것을 선호한다. 이전 절에서 이를 대체할 수 있는 네임드 듀플을 살펴봤다. 파이썬 3.7부터는 데이터 클래스를 지원한다.

name속성을 가진 보통 객체는 다음과 같다


```python
class TeenyClass():
    def __init__(self, name):
        self.name=name
        
teeny=TeenyClass('itsy')
teeny.name
```

데이터 클래스를 사용하여 같은 작업을 한다면 조금 다르게 보인다.


```python
from dataclasses import dataclass
@dataclass
class TeenyDataClass:
    name:str
        
teeny=TeenyDataClass('bitsy')
teeny.name
```

@dataclass 데커레이터 외에 name:type(이름:타입), 예를 들면 color:str 또는 color:str="red"와 같은 형식의 변수 어노테이션을 사용하여 클래스 속성을 정의한다. 타입은 str 또는 int와 같은 내장 클래스 뿐만 아니라 사용자가 생성한 클래스를 포함한 모든 파이썬 객체 타입일 수 있다

데이터 클래스 객체를 생성할 때, 클래스에 지정된 순서대로 인수를 제공하거나 이름이 지정된 인수를 임의의 순서로 제공한다

from dataclasses import dataclass
@dataclass
class AnimalClass:
    name:str
    habitat:str
    teeth:int=0
        
snowman=AnimalClass('yeti', 'Himalayas', 46)
duck=AnimalClass(habitat='lake', name='duck')
snowman


```python
duck
```

AnimalClass 클래스에서 teeth속성의 기본 값을 정의해서 객체를 생성할 때 teeth속성을 제공하지 않아도 된다. 

일반 객체와 같이 객체 속성을 참조할 수 있다



```python
duck.habitat
```


```python
snowman.teeth
```

### 10.13 attrs

클래스를 생성하고 여기에 속성을 추가하는 법을 배웠다. 그리고 던더가 있는 __init__(), __str__() 등의 매직 메서드와 self매개변수를 살펴보았다. 네임드튜플 및 데이터 클래스는 표준 라이브러리의 대안으로 데이터 컬렉션을 만들 때 더 쉽게 접근할 수 있다. 

### 10.14 다음 장에서는

코드 구조를 위한 파이썬 모듈 및 패키지에 대해서 살펴본다


```python

```
