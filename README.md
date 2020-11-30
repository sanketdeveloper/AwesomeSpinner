# Awesome Android Spinner
[![](https://jitpack.io/v/amlashi-sadra/AwesomeSpinner.svg)](https://jitpack.io/#amlashi-sadra/AwesomeSpinner)
[![License](https://img.shields.io/badge/licence-MIT-lightgrey.svg?style=flat)](https://github.com/amlashi-sadra/AwesomeSpinner/blob/master/LICENSE)
[![Dependencies](https://img.shields.io/badge/dependencies-non-yellow.svg?style=flat)](#)
[![Gitter](https://img.shields.io/badge/gitter-join%20chat-%23E91E63.svg?style=flat)](https://gitter.im/AwesomeSpinner)
[![Minimum Android SDK Version](https://img.shields.io/badge/Minimum%20Android%20SDK-14-blue.svg)](#)

With **Awesome Spinner** you can implement a material spinner with access to define **direction layout** and **hint text**.

![](https://github.com/amlashi-sadra/AwesomeSpinner/blob/master/art/awesome_spinner_rtl.gif)
![](https://github.com/amlashi-sadra/AwesomeSpinner/blob/master/art/awesome_spinner_ltr.gif)


## Including the library

**Step 1.** Add it in your root build.gradle at the end of repositories:
```groovy
allprojects {
	repositories {
		...
		maven { url 'https://jitpack.io' }
	}
}
```

**Step 2.** Add the dependency:
```groovy
implementation 'com.github.sadra:AwesomeSpinner:1.5.2'
```

## How To Use

**Step 1.** From very first, you should add the **Awsome Spinner** component inside of your layout:
```xml
    <com.isapanah.awesomespinner.AwesomeSpinner
        android:id="@+id/my_spinner"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>
```

- If you want to add a default value for hint just add the `spinnerHint` into your component
- The default spinner has `RTL` direction, if you want to declare the direction of spinner just add the `spinnerDirection` to **RTL** or **LTR**
so the complete example with **LTR** direction and hint text to **Select a category** is:
```xml
    <com.isapanah.awesomespinner.AwesomeSpinner
        android:id="@+id/my_spinner"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:spinnerDirection="ltr"
        app:spinnerHint="Select a category" />
```

**Step 2.** Define the component class into your activity:
```java
AwesomeSpinner my_spinner = (AwesomeSpinner) findViewById(R.id.my_spinner);
```
Then Create your adapter. For now, there is two way to define apadter:
- With String List, define a `List<String>` in your activity and the attach that with your adapter:
```java
List<String> categories = new ArrayList<String>();
categories.add("Automobile");
categories.add("Ariplane");

ArrayAdapter<String> categoriesAdapter = new ArrayAdapter<String>(this, android.R.layout.simple_spinner_item, categories);

my_spinner.setAdapter(categoriesAdapter);
```
- With String-Array, define a `string-array` in your `strings.xml` file and attach that with your adapter:
```java
ArrayAdapter<CharSequence> provincesAdapter = ArrayAdapter.createFromResource(this, R.array.iran_provinces, android.R.layout.simple_spinner_item);

spinnerRTL.setAdapter(provincesAdapter, 0);
```

**Step 3.** For final step, you can create a **Listener** for listening on item selection:
```java
my_spinner.setOnSpinnerItemClickListener(new AwesomeSpinner.onSpinnerItemClickListener<String>() {
    @Override
    public void onItemSelected(int position, String itemAtPosition) {
        //TODO YOUR ACTIONS
    }
});
```

### Additional controls
there is some controls for your spinner:

| Control | Requierement | Info |
| :------------- |:-------------:| :-----|
| getSelectedItem() | - | Result = `String`: Returns the selected item |
| getSelectedItemPosition() | - | Result = `int`: Returns the selected item position. If there were no selected item, it returns `-1`. |
| isSelected() | - | Result = `boolean`: Returns **true** if any item selected, and vice versa. |
| setSelection(`NUMBER`) | `int` position | You should pass the **position of item** to select the item programatically. |
| setSelection(`TEXT`) | `String` value | You should pass the **item value** to select the item programatically. |
| setSpinnerHint(`TEXT`) | `String` value | You should pass a `sting` value as the hint text for the spinner. |
| setSpinnerEnable(`BOOLEAN`); | `Boolean` value | If you want enable or disable the spinner, you should call this method. |
| isSpinnerEnable() | - | Result = `boolean`: Returns **true** if the spinner is enabled, and vice versa. |
| setHintTextColor() | `int` Color | If you need to change the **Spinner Hint Text** color, just call the method and pass you color, ex: `Color.BLUE`. |
| setSelectedItemHintColor() | `int` Color | If you need to change the **Selected Item Hint** color, just call the method and pass you color, ex: `Color.BLUE`. |
| setDownArrowTintColor() | `int` Color | If you need to change the **Down Arrow** hint color, just call the method and pass you color, ex: `Color.BLUE`. |
| setDropDownViewResource(`RESOURCE`) | `int` Resource | If you need to change the **Spinner Row stype**, just call the method and pass you resource, ex: `R.layout.my_sipnner_row_item`. |
| clearSelection() | - | It clears the spinner selection. |

You can see the [EXAMPLE PROJECT](https://github.com/amlashi-sadra/AwesomeSpinner/tree/master/app/src/main) for more infromation.

## License

The MIT License (MIT): [https://github.com/amlashi-sadra/AwesomeSpinner/blob/master/LICENSE](https://github.com/amlashi-sadra/AwesomeSpinner/blob/master/LICENSE)

Copyright (c) 2017 Sadra Isapanah Amlashi

Website: [isapanah.com](http://isapanah.com)

Twitter: [@sadra_amlashi](https://twitter.com/sadra_amlashi)
