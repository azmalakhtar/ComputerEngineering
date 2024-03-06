# Android Navigation Patterns

# Navigation Terms

# Fragments

# Fragment Basics

# Creating and Adding a Fragment

# Navigation Component

# Principles of Navigation

# Conditional Navigation

# Back Stack Manipulation

# Adding Support for the Up Button

# Android Navigation - Up vs Back

# Adding A Menu

![Menu](https://lh3.googleusercontent.com/kyUjfdA4kbCLZTJCQY0gqPCCVdTr74WMzCScfyuZkFGx8GQXU6uVvcSExckK28csQqWAdLXvLiQpD1a_DpJlX2c15GD4bLYrNu4c_W7-AOE6og=s0)

## Steps
1. Add a menu resource file.
2. In your activity/fragment call `setHasOptionsMenu` and pass true as the argument.
3. Inflate the menu resource in the `onCreateOptionsMenu` callback.
4. Define what happens on selecting a particular menu option in `onOptionsItemSelected`.

## Using the `NavigationUI` class
- It helps in tying menu item to navigation destinations.
- Helper method `onNavDestinationSelected` takes in the menu item and `NavContoller` as arguments. If the id of the menu item matches the id of the destination, the  `NavController` can then navigate to that destination
# Matching Menu Attributes

# Adding Safe Arguments

- Used for passing arguments to a destination.
## Implementation
1. Add the safe args dependencies in `gradle` files.
2. In nav garph define what arguments a destination requires.
3. Then while navigating use `Directions` class instead of action id.
4. Pass the required arguments in the constructor of the directions class.
```kt
view.findNavController().navigate(
	                            GameFragmentDirections.actionGameFragmentToGameWonFragment(
                                numQuestions,
                                questionIndex
                            )
    )
```

# Why do we have Safe Arguments?

- **Type Safety** -> Navigation generates the action and the argument class from the navigation graph.
- **Argument Enforcement** -> Non-default arguments are required parameters in the action.

# Intents and Sharing

- Intents represent intention.
- Two Types
	- Explicit -> Intent that navigate to a **specific activity**.
	- Implicit -> Intent that describes **what needs to be done** without mentioning any explicit activity.
- To allow activities to be opened by an intent
	- explicit intent -> just registering the activity in the manifest file is enough
	- implicit intent -> need to provide correct **intent filter**.
	- 
# Explicit vs Implicit Intent

# Adding Sharing with an Intent
1. Create an `Intent`.
2. Call `startActivity()` method and pass the intent as argument.
- If the intent doesn't resolve to any activity, the app will crash due to the activity not found exception.
- You can check if an intent will resolve to any activity using the following `intent.resolveActivity(activity!!.packageManager)` . If this returns null, then that means there is no activity that will be able to handle the intent.
# Adding the Navigation Drawer
1. Include the material ui library.
2. Add the menu resource file for navigation drawer.
3. In the layout file, in which you want to show the drawer, surround the ui code with `androidx.drawerlayout.widget.DrawerLayout` tag.
4. Add the `com.google.android.material.navigation.NavigationView` at the end of the ui code. In this you assign the menu to display using `app:menu` attribute.
5. Pass `drawerLayout` in the `NavigationUI.setupActionBarWithNavController`
6. `NavigationUI.setupWithNavController(binding.navView, navController)`
7. In `onSupportNavigateUp` use `NavigationUI.navigateUp(drawerLayout, navController)`.

# Summary of Navigation

# Using Navigation Listeners
```kt
navController.addOnDestinationChangedListener { nc: NavController, nd: NavDestination, args: Bundle? ->
   if (nd.id == nc.graph.startDestination) {
       drawerLayout.setDrawerLockMode(DrawerLayout.LOCK_MODE_UNLOCKED)
   } else {
       drawerLayout.setDrawerLockMode(DrawerLayout.LOCK_MODE_LOCKED_CLOSED)
   }
}
```

# Animation with Navigation
- Animations are described using xml files.
## 1. Create Animation Resource
- The resource type is Animation.
- There are different type of animations
### Alpha Animation
- For fading in or out because it changes the transperanecy of the view group.
```xml
<set xmlns:android="http://schemas.android.com/apk/res/android"> 
	<alpha 
	   android:duration="@android:integer/config_mediumAnimTime" 
	   android:fromAlpha="0.0" 
	   android:toAlpha="1.0" /> 
</set>
```

### Translate Animation
- For sliding in or out because it controls the x & y position of the view group.
```xml
<set xmlns:android="http://schemas.android.com/apk/res/android"> 
	<translate 
		   android:fromXDelta="-100%" 
		   android:toXDelta="0%" 
		   android:fromYDelta="0%" 
		   android:toYDelta="0%" 
		   android:duration="@android:integer/config_shortAnimTime" /> </set>
``` 
## 2. Assign Animations to Navigation Actions
- There the two types
	- Enter -> animation to play when the view group enters.
	- Exit -> animation to play when the view group exits.

When | Transition
-- | --
Played for the destination to be navigated to when another destination replaces the current one. | Exit Transition
Played for the destination to be navigated to when it is entered. | Enter Transition
Played when the current destination is popped off the back stack. | Pop Exit Transition
Played when the destination is returned to view from the back stack. | Pop Enter Transition

# Animation Attributes