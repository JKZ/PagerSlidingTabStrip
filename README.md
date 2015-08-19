# Android PagerSlidingTabStrip

Interactive paging indicator widget, compatible with the `ViewPager` from the 
Android Support Library. 

![PagerSlidingTabStrip Sample Screenshot 1](screenshots/blue.png)   ![PagerSlidingTabStrip Sample Screenshot 2](screenshots/green.png)

# Usage

*For a working implementation of this project see the `sample/` folder.*

  1. Include the library as local library project or add the dependency in your build.gradle.
        
        dependencies {
            compile 'com.astuetz:pagerslidingtabstrip:1.0.1'
        }

  2. Include the PagerSlidingTabStrip widget in your layout. This should usually be placed
     above the `ViewPager` it represents.

        <com.astuetz.PagerSlidingTabStrip
            android:id="@+id/tabs"
            android:layout_width="match_parent"
            android:layout_height="48dip" />

  3. In your `onCreate` method (or `onCreateView` for a fragment), bind the
     widget to the `ViewPager`.

         // Initialize the ViewPager and set an adapter
         ViewPager pager = (ViewPager) findViewById(R.id.pager);
         pager.setAdapter(new TestAdapter(getSupportFragmentManager()));
         
         // Bind the tabs to the ViewPager
         PagerSlidingTabStrip tabs = (PagerSlidingTabStrip) findViewById(R.id.tabs);
         tabs.setViewPager(pager);

  4. *(Optional)* If you use an `OnPageChangeListener` with your view pager
     you should set it in the widget rather than on the pager directly.

         // continued from above
         tabs.setOnPageChangeListener(mPageChangeListener);

# Customization

To not just look like another Play Store styled app, go and adjust these values to match
your brand:

 * `pstsIndicatorColor` Color of the sliding indicator
 * `pstsUnderlineColor` Color of the full-width line on the bottom of the view
 * `pstsDividerColor` Color of the dividers between tabs
 * `pstsIndicatorHeight`Height of the sliding indicator
 * `pstsUnderlineHeight` Height of the full-width line on the bottom of the view
 * `pstsDividerPadding` Top and bottom padding of the dividers
 * `pstsTabPaddingLeftRight` Left and right padding of each tab
 * `pstsScrollOffset` Scroll offset of the selected tab
 * `pstsTabBackground` Background drawable of each tab, should be a StateListDrawable
 * `pstsShouldExpand` If set to true, each tab is given the same weight, default false
 * `pstsTextAllCaps` If true, all tab titles will be upper case, default true

*All attributes have their respective getters and setters to change them at runtime*

# Customization of Text color (New)

  1. New file drawable/tab_text_colors.xml

        <?xml version="1.0" encoding="utf-8"?>
        <selector xmlns:android="http://schemas.android.com/apk/res/android">
            <item android:color="@color/tab_text_selected" android:state_pressed="true" />
            <item android:color="@color/tab_text_selected" android:state_selected="true" />
            <item android:color="@color/tab_text_default" />
        </selector>

  1. Set the color selector in layout XML.

        <com.astuetz.PagerSlidingTabStrip
            android:id="@+id/tabs"
            android:layout_width="match_parent"
            android:layout_height="48dip"
            android:background="@drawable/background_tabs"
            android:textColor="@drawable/tab_text_colors" />

    *OR set in Java code.*

        tabs.setTextColorResource(R.drawable.tab_text_colors);


# Changelog

### 1.0.2

 * Material design riple effect support in Android 5.0+.
 * Tab's text color can be set as state list.

### [1.0.1](https://github.com/astuetz/PagerSlidingTabStrip/tree/v1.0.1)

 * Upgraded gradle build files
 * Changed package name to `com.astuetz.PagerSlidingTabStrip`
 * [#37](https://github.com/astuetz/PagerSlidingTabStrip/pull/37), [#41](https://github.com/astuetz/PagerSlidingTabStrip/pull/41) Added `psts` prefix to all attributes in `attrs.xml`
 * [#46](https://github.com/astuetz/PagerSlidingTabStrip/pull/46) Changed the shouldExpand behavior to set the layout at the time the tab is added


# Developed By

 * Andreas Stuetz - <andreas.stuetz@gmail.com>
 * Kevin - <Kevin.D.Zhong@gmail.com>

### Credits

 * [Kirill Grouchnikov](https://plus.google.com/108761828584265913206/posts) - Author of [an explanation post on Google+](https://plus.google.com/108761828584265913206/posts/Cwk7joBV3AC)


# License

    Copyright 2013 Andreas Stuetz

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
