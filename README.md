# iOSCustomPageControl
Android style page control

![      ](\pageControl.gif "")       


* Easy to modify 
* Lazy loading for smoother performance
* Customizable component color

<em>This UI control can be used on all iPhones, iPods & iPads running iOS 5.0 and above.</em>

---
---

### Adding to your project


* Add Follwing 5 control files to your project from ADPageControl directory

```
'ADPageControl.h'
'ADPageControl.m'
'ADPageModel.h'
'ADPageModel.h'
'ADPageControl.xib'
```

---
---

### How to use

#### Sample Code

```obj-c

//1. IMPORT
  "#import "ADPageControl.h"
```

```obj-c
//2. DECLARE
  ADPageControl *_pageControl; //Declare
  
//3. SETUP PAGE MODEL USING CLASS "ADPageModel"

    //page 0
    ADPageModel *pageModel0 = [[ADPageModel alloc] init];
    PageItemController *page0 = [self.storyboard instantiateViewControllerWithIdentifier:@"PAGE"];
    page0.view.backgroundColor = [UIColor colorWithRed:1 green:204.0/255 blue:204.0/255.0 alpha:1.0];
    pageModel0.strPageTitle = @"Reeed";
    pageModel0.iPageNumber = 0;
    pageModel0.viewController = page0;//You can provide view control in prior OR use flag "bShouldLazyLoad" to load only when required

    //page 1
    ADPageModel *pageModel1 = [[ADPageModel alloc] init];
    pageModel1.strPageTitle = @"Greeeeeeeen";
    pageModel1.iPageNumber = 1;
    pageModel1.bShouldLazyLoad = YES;
    
    //page 2
    ADPageModel *pageModel2 = [[ADPageModel alloc] init];
    pageModel2.strPageTitle = @"Blueeee";
    pageModel2.iPageNumber = 2;
    pageModel2.bShouldLazyLoad = YES;
    
    //page 3
    ADPageModel *pageModel3 = [[ADPageModel alloc] init];
    pageModel3.strPageTitle = @"Yeeellow";
    pageModel3.iPageNumber = 3;
    pageModel3.bShouldLazyLoad = YES;  
    
//4. INITIALIZE PAGE CONTROL
    _pageControl = [[ADPageControl alloc] init];
    _pageControl.iFirstVisiblePageNumber = 1;
    _pageControl.delegateADPageControl = self;
    _pageControl.arrPageModel = [[NSMutableArray alloc] initWithObjects:pageModel0,pageModel1,pageModel2,pageModel3, nil];

//5. SET THEME COLORS
    _pageControl.colorTabText = [UIColor whiteColor];
    _pageControl.colorTitleBarBackground = [UIColor purpleColor];
    _pageControl.colorPageIndicator = [UIColor whiteColor];
    _pageControl.colorPageOverscrollBackground = [UIColor darkGrayColor];

//6. ADD AS SUBVIEW
    _pageControl.view.frame = CGRectMake(0, 20, self.view.bounds.size.width, self.view.bounds.size.height - 20);
    [self.view addSubview:_pageControl.view];

//7. CONFORM TO DELEGATE & HANDLE LAZY LOADING BY PROVIDING VIEW CONTROLLERS

//Conform <ADPageControlDelegate>

-(UIViewController *)getViewControllerForPageModel:(ADPageModel *) pageModel
{
    if(pageModel.iPageNumber == 1)
    {
        PageItemController *page1 = [self.storyboard instantiateViewControllerWithIdentifier:@"PAGE"];
        page1.view.backgroundColor = [UIColor colorWithRed:204.0/255 green:1 blue:204.0/255 alpha:1.0];

        return page1;
    }
    else if(pageModel.iPageNumber == 2)
    {
        PageItemController *page2 = [self.storyboard instantiateViewControllerWithIdentifier:@"PAGE"];
        page2.view.backgroundColor = [UIColor colorWithRed:204.0/255 green:204.0/255 blue:1 alpha:1.0];
        
        return page2;
    }
    else if(pageModel.iPageNumber == 3)
    {
        PageItemController *page3 = [self.storyboard instantiateViewControllerWithIdentifier:@"PAGE"];
        page3.view.backgroundColor = [UIColor colorWithRed:1 green:1 blue:204.0/255 alpha:1.0];
        
        return page3;
    }
    
    return nil;
}

```


---
---

### Requirements

ADPageControl works on iOS 5.0 & above versions and is compatible with ARC projects. There is no need of other frameworks/libraries

---
---

### Other details

* XCode : Developed using 6.1
* Base sdk used while development : 8.1
* Compatible devices : iPhone, iPad, iPod

---
---

### TODO

* Component polishing
* More generalizations
* Page indicator movement along with page scrolling

---
---
