# 目录
1. [单例模式](#单例模式)
2. [工厂模式](#工厂模式)
3. [装饰模式](#装饰模式)

## 1. 单例模式 <a name="单例模式"></a>
 - 饿汉模式 
 ```
 class Singleton(object):
 
   _instance = None
   
   def __new__(cls, *args, **kwargs):
     if not hasattr(Singleton,'_instance'):
       cls._instance = super(Singleton, cls).__new__(cls)
     return cls._instance
 ```
 优点:
1. 线程安全
2. 在类实例化前已经创建好一个静态对象，调用时反应速度快
3. 直接执行其他方法或静态方法时，单例实例不会被初始化  

缺点:
1. 不管使用与否，实例化前就初始化静态对象，有点资源浪费  

 - 懒汉模式
 ```
 class Singleton(object):

    _instance = None
 
    def __init__(self):
        if not hasattr(Singleton, '_instance'):
            print("__init__ method called, but no instance created")
        else:
            print("instance already created:", self._instance)
 
    @classmethod
    def get_instance(cls):
        if not cls._instance:
            cls._instance = Singleton()
        return cls._instance
 ```
  优点:
1. 资源利用合理，不调用 get_instance 方法不创建单例对象  

缺点:
1. 线程不安全，多线程时可能会获取到不同单例对象的情况。解决办法是加互斥锁，但会降低效率
 
 - 多线程实现(线程安全)
 ```
 import threading
  
  
def synchronized(func):
    func.__lock__ = threading.Lock()
  
    def lock_func(*args, **kwargs):
        with func.__lock__:
            return func(*args, **kwargs)
  
    return lock_func
  
  
class Singleton(object):
    instance = None
  
    @synchronized
    def __new__(cls, *args, **kwargs):
        """
        :type kwargs: object
        """
        if cls.instance is None:
            cls.instance = super().__new__(cls)
        return cls.instance

 ```
