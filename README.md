# d2
#decorator()
import time, functools
def metric(fn):
    @functools.wraps(fn)
    def wrapper (*args,**kw):
        print('%s executed in %s ms' % (fn.__name__, 10.24))
        return fn(*args,**kw)
    return wrapper
    
#偏函数
def int2(x,base=2):
    return int(x,base)
int2('1000000')
int2('1010101')

#partial()
import functools
int2=functools.partial(int,base=2)
int2('1000000')
int2('1010101')

#sys模块
import sys
def test():
    args=sys.argv
    if len(args)==1:
        print('Hello,world!')
    elif len(args)==2:
        print('Hello,%s' %args[1])
    else:
        print('Too many arguments!')
if __name__=='__main__':
    test()

#private()
def __private1(name):
    print('Hello,%s!' %name)
def __private2(name):
    print('Hi,%s!' %name)
def greeting(name):
    if len(name)>3:
        return __private1(name)
    else:
        return __private2(name)
        
#class()
class Student(object):
    def __init__(self,name,score):
        self.name=name
        self.score=score
    def print_score(self):
        print('%s:%s' %(self.name,self.score))
        
 class Student(object):
    def __init__(self,name,score):
        self.name=name
        self.score=score
    def get_grade(self):
        if self.score>=90:
            return 'A'
        elif self.score>=60:
            return 'B'
        else:
            return 'C'
            
#protect_student()
  class Student(object):
      def __init__(self,name,gender):
          self.name=name
          self.__gender=gender
      def get_gender(self):
          return self.__gender
      def set__gender(self,gender):
          self.__gender=gender
          
#继承
class Animal(object):
    def run(self):
        print('Animal is running...')
class Dog(Animal):
    def run(self):
        print('Dog is running...')
    def eat(self):
        print('eating meat...')
        
#多态
class Animal(object):
    def run(self):
        print('Animal is running')
class Dog(Animal):
    def run(self):
        print('Dog is running...')
def run_twice(animal):
    animal.run()
    animal.run()
run_twice(Animal())
run_twice(Dog())
class Tortoise(Animal):
    def run(self):
        print('Tortoise is running slowly...')
run_twice(Tortoise())

#__len__()
class MyDog(object):
    def __len__(self):
        return 100
dog=MyDog()
len(dog)

#add_Student()
class Student(object):
    count=0
    def __init__(self,name):
        self.name=name
        Student.count+=1
        
#@property
class Screen(object):
    @property
    def width(self):
        return self._width
    @width.setter
    def width(self,value):
        self._width=value
    @property
    def height(self):
        return self._height
    @height.setter
    def height(self,value):
        self._height=value
    @property
    def resolution(self):
        return self.width*self.height

#多重继承
class Animal(object):
    pass
class Mammal(Animal):
    pass
class Bird(Animal):
    pass
class Runnable(object):
    def run(self):
        print('running...')
class Flyable(object):
    def fly(self):
        print('flying...')
class Dog(Mammal,Runnable):
    pass
class Bat(Mammal,Flyable):
    pass
class Parrot(Bird,Flyable):
    pass
class Ostrich(Bird,Runnable):
    pass
    
#__str__()
class Student(object):
    def __init__(self,name):
        self.name=name
    def __str__(self)
        return 'Student object(name=%s)' %self.name
    __repr__=__str__
    
#__iter__()
class Fib(object):
    def __init__(self)
        self.a,self.b=0,1
    def __iter__(self):
        return self
    def __next__(self):
        self.a,self.b=self.b,self.a+slef.b
        if self.a>100000:
            raise StopIteration
        return self.a
        
#__getitem__()
class Fib(object):
    def __getitem__(self,n):
        if isinstance(n,int):
            a,b=1,1
            for i in range(n):
                a,b=b,a+b
            return a
        if isinstance(n,slice):
            start=n.start
            stop=n.stop
            if start is None:
                start=0
            a,b=1,1
            L=[]
            for x in range(stop):
                if x>=start:
                    L.append(x)
                a,b=b,a+b
            return L
    
 #__call__()
 class Student(object):
     def __init__(self,name):
         self.name=name
     def __call__(self):
         print('My name is %s.' %self.name)
         
 #枚举
 from enum import Enum
 Month=Enum('Month',('Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'))
 for name,member in Month.__members__.items():
     print(name,'=>',member,',',member.value)
 from enum import Enum,unique
 @unique
 class Weekday(Enum):
     Sun=0
     Mon=1
     Tue=2
     Wed=3
     Thu=4
     Fri=5
     Sat=6
