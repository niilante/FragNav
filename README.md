# FragNav
Android library for managing multiple stacks of fragments (e.g., [Bottom Navigation ](https://www.google.com/design/spec/components/bottom-navigation.html), [Navigation Drawer](https://www.google.com/design/spec/patterns/navigation-drawer.html)).  This library does NOT include the UI for bottom tab bar layout.  For that, I recommend either [BottomBar](https://github.com/roughike/BottomBar) (which is the library shown in the demo) or [AHBottomNavigation](https://github.com/aurelhubert/ahbottomnavigation). This library helps maintain order after pushing onto and popping from multiple stacks(tabs). It also helps with switching between desired tabs and clearnig the stacks.

<img src="https://raw.githubusercontent.com/ncapdevi/FragNav/master/FragNavDemo.gif" width="30%" />

## Sample
With [Material Design Bottom Navigation pattern](https://www.google.com/design/spec/components/bottom-navigation.html), and other tabbed navigation, managing multiple stacks of fragments can be a real headache.  The example file shows best practice for navigating deep within a tab stack.

## Gradle

```groovy
compile 'com.ncapdevi:frag-nav:1.0.3'
```

## How do I implement it?

### Initialize

```java
List<Fragment> fragments = new ArrayList<>(5);

fragments.add(RecentsFragment.newInstance());
fragments.add(FavoritesFragment.newInstance());
fragments.add(NearbyFragment.newInstance());
fragments.add(FriendsFragment.newInstance());
fragments.add(FoodFragment.newInstance());

FragNavController fragNavController = new FragNavController(getSupportFragmentManager(),R.id.container,fragments);
```

Send in  the supportFragment Manager, a list of base fragments, the container that you'll be using to display fragments.
After that, you have four main functions that you can use

### Switch tabs
Tab switching is indexed to try to prevent you from sending in wrong indices. It also will throw an error if you try to switch to a tab you haven't defined a base fragment for.

```java
fragNavController.switchTab(NavController.TAB1);
fragNavController.switchTab(NavController.TAB2);
fragNavController.switchTab(NavController.TAB3);
fragNavController.switchTab(NavController.TAB4);
fragNavController.switchTab(NavController.TAB5);
```

### Push a fragment
You can only push onto the currently selected index
        fragNavController.push(FoodFragment.newInstance())

### Popping a fragment only happens on the same index as well
        fragNavController.pop();

### You can also clear the stack to bring you back to the base fragment
    fragNavController.clearStack();


A sample application is in the repo if you need to see how it works.


## Apps Using FragNav
Feel free to send me a pull request with your app and I'll link you here:

## Contributions
If you have any problems, feel free to create an issue or pull request.

The sample app in the repository uses [BottomBar](https://github.com/roughike/BottomBar) library.

## License

```
FragNav Android Fragment Navigation Library
Copyright (c) 2016 Nic Capdevila (http://github.com/ncapdevi).

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
