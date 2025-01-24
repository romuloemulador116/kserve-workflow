def my_decorator(func):
    def wrapper():
        print("Something is happening before the function is called.")
        func()
        print("Something is happening after the function is called.")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
def repeat(num_times):
    def decorator_repeat(func):
        def wrapper(*args, **kwargs):
            for _ in range(num_times):
                func(*args, **kwargs)
        return wrapper
    return decorator_repeat

@repeat(num_times=3)
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")
def log_method_call(func):
    def wrapper(self, *args, **kwargs):
        print(f"Calling method {func.__name__} with arguments: {args} {kwargs}")
        result = func(self, *args, **kwargs)
        print(f"Method {func.__name__} returned: {result}")
        return result
    return wrapper

class MyClass:
    @log_method_call
    def add(self, x, y):
        return x + y

obj = MyClass()
obj.add(3, 5)
