LeakCanary介绍
LeakCanary 是一个开源的在debug版本中检测内存泄漏的java库。

[地址](https://github.com/square/leakcanary)

一个cait的例子：

class Cat {
}
class Box {
  Cat hiddenCat;
}
class Docker {
  static Box container;
}

// ...

Box box = new Box();
Cat schrodingerCat = new Cat();
box.hiddenCat = schrodingerCat;
Docker.container = box;

创建一个RefWatcher实例，然后给它一个对象让它观察：

// We expect schrodingerCat to be gone soon (or not), let's watch it.
refWatcher.watch(schrodingerCat);
当检测出泄漏的时候，你会自动得到一个漂亮的泄漏线索：

* GC ROOT static Docker.container
* references Box.hiddenCat
* leaks Cat instance


设置 只需几行代码，LeakCanary就能自动检测Activity的泄漏：

public class ExampleApplication extends Application {
  @Override public void onCreate() {
    super.onCreate();
    LeakCanary.install(this);
  }
}
