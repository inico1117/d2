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
