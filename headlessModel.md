### java.awt.headless is a system mode of java in which the keyboard、 mouse、 display device is lacking.

```
// open headless mode
java -Djava.awt.headless=true
```
-----
### why use headless mode ?

Let's say that your application repeatedly generates a certain image, 
for example, a graphical authorization code that must be changed every time a user logs in to the system.
When creating an image, your application needs neither the display nor the keyboard.
Let's assume now that you have a mainframe or dedicated server on your project that has no display device, keyboard, or mouse. 
The ideal decision is to use this environment's substantial computing power for the visual as well as the nonvisual features.
An image that was generated in the headless mode system then can be passed to the headful system for further rendering.


-----

