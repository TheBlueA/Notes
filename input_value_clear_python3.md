### Clear default value of input (python selenuim)


from selenium.webdriver.common.keys import Keys

* method 1
```
public static void setElementValue(WebElement element,String value){
        element.sendKeys(Keys.chord(Keys.CONTROL, "a"), value);//method1
    }
```

* method 2
```
public static void setElementValue(WebElement element,String value){
        element.sendKeys(Keys.HOME,Keys.chord(Keys.SHIFT,Keys.END),value);//method2
    }
```
* method 3
```
public static void setElementValue(WebElement element,String value){
        element.sendKeys(Keys.CONTROL + "a");//method3
        element.sendKeys(value);//method3
    }
 ```   

* method 4
```
public static void setElementValue(WebElement element,String value){
        element.click(); 
        element.clear(); 
        element.sendKeys(Keys.BACK_SPACE ); 
        element.sendKeys(Keys.chord(Keys.CONTROL, "a")); 
        element.sendKeys(Keys.DELETE); 
        element.sendKeys(value); 
        element.click(); 
}
```

本文转载自：https://www.cnblogs.com/xinxin1994/p/10822730.html
