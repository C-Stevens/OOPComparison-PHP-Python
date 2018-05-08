[<-- Return to index](../README.md)
# Multithreading

### How is multitasking accomplished?
#### PHP
By extending the [`Thread`](https://secure.php.net/manual/en/class.thread.php) class in the [pthreads API](https://secure.php.net/manual/en/intro.pthreads.php). It should be noted that by most defaults, PHP will be compiled as thread-safe and without pthreads. It requires a non-negligible amount of work to both recompile or obtain a version of PHP will threading enabled, and the pthreads API installed.
#### Python
By subclassing the [`Thread`](https://docs.python.org/3.6/library/threading.html#thread-objects) class from the [threading library](https://docs.python.org/3.6/library/threading.html#), which is native to Python.

### How do threads or thread-like abilities work?
#### PHP
Parallel threading in PHP is less elegant than in Python, but ultimately just as functional. A parallel threading system in a basic form can look something like this:
```php
<?php
    class myThread extends Thread {
        private $id;
        public function __construct($id) {
            $this->id = $id;
        }
        public function run() {
            $sleepTime = mt_rand(1, 5);
            print "Thread with id ".$id."sleeping for ".$sleepTime." seconds";
            sleep($sleepTime);
            print "Thread with id ".$id." is ending";
        }
    }
    
    $threads = array();
    foreach(range(0, 10) as $i) {
        $threads[] = new myThread($i);
    }
    
    foreach($threads as $t) {
        $t->run();
    }
?>
```

#### Python
Python's threading capabilities are dense and very well documented. A basic parallel threading system can look something like this:
```python
import time
import random
from threading import Thread

def myThreadedMethod(id):
    sleepTime = random.randint(1, 5)
    print("Thread with id %d is sleeping for %d seconds"%(id, sleepTime))
    time.sleep(sleepTime)
    print("Thread with id %d is ending"%(id))

for i in range(0, 10):
    t = Thread(target=myThreadedMethod, args=(i,))
    t.start()
```
Which will output:
```
Thread with id 0 is sleeping for 2 seconds
Thread with id 1 is sleeping for 3 seconds
Thread with id 2 is sleeping for 5 seconds
Thread with id 3 is sleeping for 5 seconds
Thread with id 4 is sleeping for 3 seconds
Thread with id 5 is sleeping for 2 seconds
Thread with id 6 is sleeping for 5 seconds
Thread with id 7 is sleeping for 2 seconds
Thread with id 8 is sleeping for 2 seconds
Thread with id 9 is sleeping for 1 seconds

Thread with id 9 is ending
Thread with id 0 is ending
Thread with id 5 is ending
Thread with id 8 is ending
Thread with id 7 is ending
Thread with id 1 is ending
Thread with id 4 is ending
Thread with id 2 is ending
Thread with id 3 is ending
Thread with id 6 is ending
```
Note how the threads end at the end of their execution, not necessarily in the same order they were spawned. This demonstrates how all threads were running in parallel.
