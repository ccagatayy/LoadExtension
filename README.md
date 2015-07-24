#Extension load (Plist, JSON) Into Dictionary#
[![](http://img.shields.io/badge/OS%20X-10.10%2B-lightgrey.svg)]() 
[![](http://img.shields.io/badge/iOS-8.0%2B-lightgrey.svg)]()
####By Yannickstephan.com####




###Begin Import LoadExtensionDictionary.swift in your project###

```swift
extension Dictionary {
    
    /**
        Loads a JSON file from the app bundle into a new dictionary
    
        :param: File name
        :return: Dictionary<String, AnyObject>?
    */
    static func loadJSONFromProject(filename: String) -> Dictionary<String, AnyObject>? {
        if let path = NSBundle.mainBundle().pathForResource(filename, ofType: "json") {
            
            var error: NSError?
            let data: NSData? = NSData(contentsOfFile: path, options: NSDataReadingOptions(), error: &error)
            if let data = data {
                
                let dictionary: AnyObject? = NSJSONSerialization.JSONObjectWithData(data, options: NSJSONReadingOptions(), error: &error)
                if let dictionary = dictionary as? Dictionary<String, AnyObject> {
                    return dictionary
                } else {
                    println("File '\(filename)' is not valid JSON: \(error!)")
                    return nil
                }
            } else {
                println("Could not load file: \(filename), error: \(error!)")
                return nil
            }
        }
        println("Could not find file: \(filename)")
        return nil
        
    }
    
    /**
        Load a Plist file from the app bundle into a new dictionary
    
        :param: File name
        :return: Dictionary<String, AnyObject>?
    */
    static func loadPlistFromProject(filename: String) -> Dictionary<String, AnyObject>? {

        if let path = NSBundle.mainBundle().pathForResource(filename, ofType: "plist") {
            return NSDictionary(contentsOfFile: path) as? Dictionary<String, AnyObject>
        }
        println("Could not find file: \(filename)")
        return nil
    }
}
```
