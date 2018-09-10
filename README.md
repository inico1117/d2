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
