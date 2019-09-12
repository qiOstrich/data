#python2、3差别

1. python2中仍然是有long类型的，在3中已经废弃。
2. python2中input()输入的内容要规定数据类型，如字符串需要加 "",如定义时一样；
3. python2中raw_input()也表示输入，用法等同于python3中的input()
4. python2默认不支持中文，但是可以转码，只要在首航加：#-*- conding：utf-8 -*-
5. python2中print语句可以不加括号，直接写输出内容
6. python2中可以用<>表示不等于，3中已经废弃
7. 在python2中字典键可以使用has_key查看，而python3已结不用。只能使用a.get(‘key’),a['key']
8. 经典类和新式类，在python2中存在经典类，可以不继承任何类。但是python3中默认继承object。

