[<-- Return to index](../README.md)
# Listeners and Event Handlers

### How are listeners/event handlers implemented?
#### PHP
There is no specific internal event handling mechanism, but one can be approximated by implementing one yourself. For example, a basic implementation of an [observer model](https://en.wikipedia.org/wiki/Observer_pattern) event handling system:
```php
<?php
	abstract class SubjectBase {
    	abstract public function handleEvent();
    }

	class Observer {
    	private $subjects = array();
        public function registerSubject($subject) {
        	array_push($this->subjects, $subject);
        }
        public function notifySubjects() {
            foreach($this->subjects as $s) {
            	$s->handleEvent();
            }
        }
    }
    class Subject extends SubjectBase {
    	private $name;
        public function __construct($name) {
        	$this->name = $name;
        }
    	public function handleEvent($event) { // In this example, events are just Strings. However more a more sophisticated Event object could be constructed and utilized to increase usefulness
        	print "Subject name: ".$this->name." is handling this event: ".$event;
        }
    }
    
    $a = new Subject("foo");
    $b = new Subject("bar");
    $c = new Subject("baz");
    
    $observer = new Observer();
    $observer->registerSubject($a);
    $observer->registerSubject($b);
    $observer->registerSubject($c);
    
    $observer->notifySubjects("myEvent");
?>
```
Will output:
```
Subject name: foo is handling this event: myEvent
Subject name: bar is handling this event: myEvent
Subject name: baz is handling this event: myEvent
```
#### Python
Much like PHP, there exists no native library functions specifically for event handling. Yet, just like PHP, event-based architectures can be created. A basic observer model pattern can be approximated in a way similar to which follows:
```python
class Subject:
	def __init__(self, name):
    	self.name = name
   def handleEvent(self, event):
   		print("Subject name: %s is handling this event: %s"%(self.name, event))
        
class Observer:
	subjects = []
	def registerSubject(self, subject):
    	self.subjects.append(subject)
    def notifySubjects(self, event):
    	for s in self.subjects:
        	s.handleEvent(event)
            
a = Subject("foo")
b = Subject("bar")
c = Subject("baz")

observer = Observer()
observer.registerSubject(a)
observer.registerSubject(b)
observer.registerSubject(c)

observer.notifySubjects("myEvent")
```
Will output:
```
Subject name: foo is handling this event: myEvent
Subject name: bar is handling this event: myEvent
Subject name: baz is handling this event: myEvent
```
