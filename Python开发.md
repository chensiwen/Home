1. 如果在开发程序时，不希望立刻编写分支内部的程序，可以使用 ***pass*** 关键字表示一个占位符，保证程序的代码结构正常。在程序运行时pass关键字不会执行任何操作。
```python
action_str = input("Input an number: ")
print("The number is %s" % action_str)
if action_str in ['1', '2', '3']:
    pass
elif action_str == '0':
    pass
else:
    print('The number is error!')
```
