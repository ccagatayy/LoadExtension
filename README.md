LoadExtensionDictionary[![](http://img.shields.io/badge/OS%20X-10.10%2B-lightgrey.svg)]() [![](http://img.shields.io/badge/iOS-8.0%2B-lightgrey.svg)]()
=============

Simple Extension for load any files (Plist, JSON) Into Dictionary type Dictionary<String, AnyObject>?

By Yannickstephan.com

Version : 2.0

**Begin** Import LoadExtensionDictionary in your project

**Create function for import data :**
=====
```swift
/**
  Example function for load Files JSON
  
  :param: Name File JSON
*/
func loadJSON(filename: String) -> ExampleClass? {
    if let dictionary = Dictionary<String, AnyObject>.loadPlistFromProject(filename) {
        let stringValue = (dictionary["name"] as NSString)
        let intergerValue = (dictionary["score"] as NSString).integerValue
        let doubleValue = (dictionary["maxDurationTransition"] as NSString).doubleValue
        
        return ExampleClass(stringValue: stringValue, intergerValue: intergerValue, doubleValue: doubleValue)
    }
    return nil
}

/**
  Example function for load Files Plist
  
  :param: Name File Plist
*/
func loadJSON(filename: String) -> ExampleClass? {
    if let dictionary = Dictionary<String, AnyObject>.loadPlistFromProject(filename) {
        let stringValue = (dictionary["name"] as NSString)
        let intergerValue = (dictionary["score"] as NSString).integerValue
        let doubleValue = (dictionary["maxDurationTransition"] as NSString).doubleValue
        
        return ExampleClass(stringValue: stringValue, intergerValue: intergerValue, doubleValue: doubleValue)
    }
    return nil
}
```
