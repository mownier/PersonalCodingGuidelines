# Coding Convention (Objective-C)
This coding convention is inspired by the [official raywenderlich.com Objective-C style guide](https://github.com/raywenderlich/objective-c-style-guide/blob/master/README.md#literals).

##Table of Contents
[1. Code Organization](#code-orgnization) <br>
&nbsp;&nbsp;&nbsp;&nbsp;
[1.1. Using **`#pragma mark`**](#using-pragma-mark) <br>
&nbsp;&nbsp;&nbsp;&nbsp;
[1.2 .Project Structure](#project-structure)
<br>
[2. Spacing](#spacing) <br>
&nbsp;&nbsp;&nbsp;&nbsp;
[2.1. Indentation](#indentation) <br>
&nbsp;&nbsp;&nbsp;&nbsp;
[2.2. Braces](#braces) <br>
&nbsp;&nbsp;&nbsp;&nbsp;
[2.3. Scope's First Line](#first-line)<br>
&nbsp;&nbsp;&nbsp;&nbsp;
[2.4. If-Else and Loops](#if-else-and-loop) <br>
&nbsp;&nbsp;&nbsp;&nbsp;
[2.5. Case Statements](#case-statements) <br>
[3. Naming](#naming) <br>
&nbsp;&nbsp;&nbsp;&nbsp;
[3.1. Variables](#variables)<br>
&nbsp;&nbsp;&nbsp;&nbsp;
[3.2. Methods](#methods) <br>
&nbsp;&nbsp;&nbsp;&nbsp;
[3.3. Classes](#classes)<br>
[4. Declaration](#declration)<br>
&nbsp;&nbsp;&nbsp;&nbsp;
[4.1. Properties](#properties)<br>
&nbsp;&nbsp;&nbsp;&nbsp;
[4.2. Enumerated Types](#enumerated-types)<br>
&nbsp;&nbsp;&nbsp;&nbsp;
[4.3. Custom Constructor](#custom-constructor)<br>
&nbsp;&nbsp;&nbsp;&nbsp;
[4.4. Literals](#literals)<br>
&nbsp;&nbsp;&nbsp;&nbsp;
[4.5. Constants](#constants)<br>
&nbsp;&nbsp;&nbsp;&nbsp;
[4.6. Singleton](#singleton)<br>
&nbsp;&nbsp;&nbsp;&nbsp;
[4.7. Private Methods and Variables](#private-methods-and-variables) <br>
[5. Custom Views](#custom-views)


<a id="code-orgnization"></a>
##1. Code Organization

<a id="using-pragma-mark"></a>
###1.1 Using `#pragma mark`

Use this for method categorization. First letter of the word should be in upper case. Every custom delegate and data source should be organized by using `#pragma mark`. Every method involving in the loading of view should be under `#pragma mark - View Life Cycle`.

**Preferred**

```objective-c
@implementation MYViewController

#pragma mark -
#pragma mark - View Life Cycle

- (void)viewDidLoad {
    [super viewDidLoad]
    ...
}

- (void)viewWillAppear:(BOOL)animated {
    [super viewWillAppear:animated]
    ...
}

#pragma mark -
#pragma mark - Table View Data Source

- (NSInteger)tableView:(UITableView *)tableView numberOfRowsInSection:(NSInteger)section {
    return 0;
}

#pragma mark -
#pragma mark - Table View Delegate

- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath {
    UITableViewCell *cell = [tableView dequeueReusableCellWithIdentifier:@"cellIdentifier"];
    ...
    return cell;
}
@end

```

**Not Preferred**

```objective-c
#pragma mark -
#pragma mark - table view delegate

...

#pragma mark -
#pragma mark - table View DaTa SouRce
```

<a id="project-structure"></a>
###1.2 Project Structure
This would be the typical structure of an Xcode project. All items in `Externals`, `Categories`, `Helpers`, and `Experiment` should have a specific folder group.

```
|__ProjectName
|    |__Source
|    |    |__App Delegate
|    |    |__Categories
|    |    |__Controllers
|    |    |__Experiment
|    |    |__Externals
|    |    |__Helpers
|    |    |__Models
|    |    |__Resources
|    |    |    |__Storyboards
|    |    |    |__Database
|    |    |    |__HTMLs
|    |    |    |__Images
|    |    |    |__JSONFiles
|    |    |    |__Xibs
|    |    |    |__Image.xcassets
|    |    |__Views
|    |__Supporting Files
|__ProjectNameTests
|__Frameworks
|__Pods
|__Products
```

<a id="spacing"></a>
##2. Spacing

<a id="indentation"></a>
###2.1 Indentation
Just indent 4 spaces.

**Preferred**

```objective-c
- (void)foo {
----if (!bar) {
--------for (int i = 0; i < 5; i++) {
------------NSString *bar = [NSString stringWithFormat:@"%d", i];
------------...
--------}    
----} else {
--------...
----}
}
```

###2.2 Braces <a id="braces"></a>
Put the open brace 1 space inline with the method and other control statements. 

**Preferred**

```objective-c
- (void)foo {
    if (!bar) {
        while (woo) {
            ...
        }
    } else {
        ...
    }
}
```
**Not Preferred**

```objective-c
- (void)foo{
    if (!bar) 
    {
        while (woo){
            ...
        }
    } else {
    	...
    }
}
```

<a id="first-line"></a>
###2.3 Scope's First Line
Avoid putting new line space above the first line of a scope.

**Preferred**

```objective-c
- (void)viewDidLoad {
    [super viewDidLoad];
    
    if (foo) {
    	int bar = 0;
    	...
    }
    ...
}
```

**Not Preferred**

```objective-c
- (void)viewDidLoad {
    
    [super viewDidLoad];
    
    if (foo) {
        
        int bar = 0;
    }
    
}
```

<a id="if-else-and-loop"></a>
###2.4 If-Else and Loops

**Preferred**

```objective-c
for (int i = 0; i < 10; i++) {
    if (!foo) {
        ...	
    } else if (bar) {
        ...	
    } else {
        ...	
    }     	
}
```

**Not Preferred**

```objective-c
for(int i =0; i< 10;i++) {
    if(!foo) {
        ...	
    }else if (bar) {
        ...	
    }else{
        ...	
    }     	
}
```

<a id="case-statements"></a>
###2.5 Case Statements

**Preferred**

```objective-c
switch (foo) {
    case 1: {
        // Multi-line using braces
        ...
    }
        break;
    case 2:
        // Single-line
        ...
        break;
    default:
        ...
        break;     
}
```
**Not Preferred**

```objective-c
switch(foo){
    case 1: 
    {
        // Multi-line using braces
        ...
    }
    break;
    case 2:
        // Single-line
        ...
        break;
    default:
        ...
        break;     
}
```


<a id="naming"></a>
##3. Naming

<a id="variables"></a>
###3.1 Variables
Naming of variables should be as descriptive as possible. Single letter variable should be avoided except in `for ()` loops. Variables must be a noun (except for `BOOL`; an adjective would be appropriate). The first letter should be in lower case. Avoid abbreviation. Camel-case style must be followed. The asterisk indicating a pointer should go along with the variable name.

In case of naming a variable for any views such as `UIView`, `UILabel`, `UIButton`, etc, the format would be `<variable name><name of the view>`

**Preferred**

```objective-c
NSString *firstName = @"Juan";
NSInteger numberOfRows = 10;
NSDictionary *response = @{};
BOOL editable = NO;
UILabel *usernameLabel = [UILabel new];
UIButton *confirmButton = [UIButton new];
```

**Not Preferred**

```objective-c
NSString* FirstName = @"Juan";
NSInteger numRows = 10;
NSDictionary *query_rsesponse = @{};
UILabel *lblUsername = [UILabel new];
UIButton *confirmBtn = [UIButton new];
```

<a id="methods"></a>
###3.2 Methods
There should be a space after the method type sign `(-/+)`. There should be no space between the return type and the first letter, which should be in lower case, of the method. Methods must be a verb.  A space should be observed between method segments. There should be a keyword before the argument. Avoid using `and` as part of the keyword because it is reserved.
Put the asterisk one space away from the parameter type.

**Preferred**

```objective-c
- (void)setText:(NSString *)text label:(UILabel *)label;
- (CGFloat)convertFromCelsius:(CGFloat)celsius toFahrenheit:(CGFloat)fahrenheit;
- (instancetype)initWithRow:(NSInteger)row column:(NSInteger)column;
```

**Not Preferred**

```objective-c
-(void)setText:(NSString *)text label:(UILabel *)label;
- (CGFloat) celsius:(CGFloat)celsius toFahrenheit:(CGFloat)fahrenheit;
- (instancetype)initWithRow:(NSInteger)row andColumn:(NSInteger)column;
```

<a id="classes"></a>
###3.3 Classes
Classes must be a noun and the first letter must be in upper case. Camel-case style should be followed.

**Preferred**

```objective-c
@interface MYPerson : NSObject
...
@end
```

**Not Preferred**

```objective-c
@interface mYPerson_Upper : NSObject
...
@end
```

<a id="declaration"></a>
##4. Declaration

<a id="properties"></a>
###4.1 Properties
The attributes of a property should be in this order: _type of storage_, _atomicity_, _custom setter method_, _custom getter method_. There is a space after the `@property` keyword and the declaration of the its attributes. Each attribute must be separated by a comma and a space. If the name of a `BOOL` property is an adjective, the property can omit the word 'is' prefix but must specify the get accessor method.

**Preferred**

```objective-c
@property (strong, nonatomic) NSString *name;
@property (readwrite, nonatomic) NSInteger age;
@property (assign, getter=isValid) BOOL valid;
```

**Not Preferred**

```objective-c
@property(nonatomic, strong) NSString *name;
@property (readwrite,strong)NSInteger age;
```

<a id="enumerated-types"></a>
###4.2 Enumerated Types

**Preferred**

```objective-c
typedef NS_ENUM(NSInteger, MYFinger) {
    MYFingerThumb,
    MYFingerIndex,
    MYFingerMiddle,
    MYFingerRing,
    MyFingerPinky
};
```

**Not Preferred**

```objective-c
typedef enum {
    MYFingerThumb,
    MYFingerIndex,
    MYFingerMiddle,
    MYFingerRing,
    MyFingerPinky
} MyFinger;
```

<a id="custom-constructors"></a>
###4.3 Custom Constructors

**Preferred**

```objective-c
- (instancetype)initWithType:(NSString *)type;
+ (instancetype)sharedManager;
```

**Not Preferred**

```objective-c
- (id)initWithType:(NSString *)type;
+ (id)sharedManager;
```

<a id="literals"></a>
###4.4 Literals
Since `NSString`, `NSDictionary`, `NSArray`, and `NSNumber` are immutable, use `@""`, `@{}`, `@[]`, and `@()` respectively when declaring a new instance;

**Preferred**

```objective-c
NSString *lastName = @"Dela Cruz";
NSDictionary *grades = @{"English":  @90, @"Math": @90, @"Science": @90};
NSArray *smartphoneBrands = @[@"Apple", @"Samsung", @"Lenovo", @"LG"];
NSNumber *hidden = @YES;
NSNumber *year = @2014;
```

**Not Preferred**

```objective-c
NSDictionary *grades = [NSDictionary dictionaryWithObjectsAndKeys:@90, @"English", @90, @"Math", @90, @"Science", nil];
NSArray *smartphoneBrands = [NSArray arrayWithObjects:@"Apple", @"Samsung", @"Lenovo", @"LG"];
NSNumber *hidden = [NSNumber numberWithBool:YES];
NSNumber *year = [NSNumber numberWithInteger:2014];
```

<a id="constants"></a>
###4.5 Constants
Constants should be declared as `static` constants and not `#define` unless explicitly being used as macros. The start of the letter should be letter `k`

**Preferred**

```objective-c
static NSString * const kCompanyName = @"Ekek";
static CGFloat const kViewHeight = 100.0f;
```

**Not Preferred**

```objective-c
#define kCompanyName @"Ekek"
#define kViewHeight 100.0f
static CGFloat const ViewWidth = 19.0f;
```

<a id="singleton"></a>
###4.6 Singleton
Singleton objects should use a thread-safe pattern for creating their shared instance.

**Preferred**

```objective-c
+ (instancetype)sharedInstance {
    static id sharedInstance = nil;

    static dispatch_once_t onceToken;
    dispatch_once(&onceToken, ^{
        sharedInstance = [[self alloc] init];
    });
    return sharedInstance;
}
```

<a id="private-methods-and-variables"></a>
###4.7 Private Methods and Variables 
All private methods and variables should be declared in the implementation file under a class extension. Private variables must be treated as properties.

**Preferred**

```objective-c
// header file
@interface MYPerson : NSObject
...
@end

// implementation file
@interface MYPerson ()

@property (strong, nonatomic) NSString *foo;
@property (readwrite, nonatomic) CGFloat bar;

- (void)hibernate;
- (void)clap;

@end

@implementation MYPerson 
...
@end
```

**Not Preferred**

```objective-c
// header file
@interface MYPerson : NSObject
...
@end

// implementation file
@interface MYPerson () {
	NSString *_foo;
	CGFloat _bar;
}

- (void)hibernate;
- (void)clap;

@end

@implementation MYPerson 
...
@end
```
<a id="custom-views"></a>
###5. Custom Views
When creating custom views like a subclass of `UITableViewCell`, do not expose publicly a subview such as `UILabel` if only the property `text` is being modified unless that subview requires heavy modification such as the `backgroundColor`, `font`, `textColor`, etc.

Instead of putting the property in the `.h` file, create a class extension in the `.m` file and declare the property. Create a `nonatomic` property in the `.h` file for the default setters and getters, which are implemented in the `.m` file, for the attribute to be modified.

**Preferred**

```objective-c
// MYTableViewCell.h
@interface MYTableViewCell : UITableViewCell

@property (nonatomic) NSString *username;

@end

// MYTableViewCell.m
@interface MYTableViewCell ()

@property (strong, nonatomic) UILabel *usernameLabel;

@end

@implementation MYTableViewCell ()

- (NSString *)username {
    return self.usernameLabel.text;
}

- (void)setUsername:(NSString *)username {
    self.usernameLabel.text = username;
}

@end
```
