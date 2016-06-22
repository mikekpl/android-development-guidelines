Android Coding Standards
========================

This is a quick reference for our set coding standards for Android Development (Mobile / Native Java)

Field Naming Convention
-----------------------
* Non-public, non-static field names start with __m__.
* Non-public widgets always start with their acronym in lower camel case format.
* Static field names start with __s__.
* Other fields start with a lower case letter.
* Public static final fields (constants) are ALL_CAPS_WITH_UNDERSCORES.

```java
public class MyClass {
    public static final int SOME_CONSTANT = 42;
    public int publicField;
    private static MyClass sSingleton;
    int mPackagePrivate;
    private int mPrivate;
    private TextView tvText;
    protected int mProtected;
}
```

Standard Brace Style
--------------------
Braces do not go on their own line; they go on the same line as the code before them:

```java
class MyClass {
    int func() {
        if (something) {
            // ...
        } else if (somethingElse) {
            // ...
        } else {
            // ...
        }
    }
}
```
We require braces around the statements for a conditional. Exception: If the entire conditional (the condition and the body) fit on one line, you may (but are not obligated to) put it all on one line. For example, this is acceptable:

```java
if (condition) {
    body();
}
```
and this is acceptable:

```java
if (condition) body();
```
but this is not acceptable:

```java
if (condition)
    body();  // bad!
```

Use Standard Java Annotations
-----------------------------
* @Deprecated: The @Deprecated annotation must be used whenever the use of the annotated element is discouraged. If you use the @Deprecated annotation, you must also have a @deprecated Javadoc tag and it should name an alternate implementation. In addition, remember that a @Deprecated method is still supposed to work. If you see old code that has a @deprecated Javadoc tag, please add the @Deprecated annotation.
* @Override: The @Override annotation must be used whenever a method overrides the declaration or implementation from a super-class. For example, if you use the @inheritdocs Javadoc tag, and derive from a class (not an interface), you must also annotate that the method @Overrides the parent class's method.
* @SuppressWarnings: The @SuppressWarnings annotation should be used only under circumstances where it is impossible to eliminate a warning. If a warning passes this "impossible to eliminate" test, the @SuppressWarnings annotation must be used, so as to ensure that all warnings reflect actual problems in the code.

Annotations Practice
--------------------
__Classes, Methods and Constructors__

When annotations are applied to a class, method, or constructor, they are listed after the documentation block and should appear as __one annotation per line__ .

```java
/* This is the documentation block about the class */
@AnnotationA
@AnnotationB
public class MyAnnotatedClass { }
```

__Fields__

Annotations applying to fields should be listed __on the same line__, unless the line reaches the maximum line length.

```java
@Nullable @Mock DataManager mDataManager;
```

File Naming
-----------

### Packages

The main package name should always be named as such:
`com.<company or entity name>.<project name>` e.g. com.sample.projecta

| Package Name         | Description                                        |
| -------------------- |--------------------------------------------------- |
| `activities`         | Contains all activities                            |
| `adapters`           | Contains all classes for custom adapters           |
| `animations`         | Contains all custom animations                     |
| `database`           | Contains all database related stuff                |
| `dialogs`            | Contains all custom dialogs or dialog fragments    |
| `fragments`          | Contains all the usual fragments                   |
| `http`               | Contains all Network adapters or configs           |
| `preferences`        | Contains all classes for custom preferences        |
| `services`           | Contains all interfaces not related to network     |
| `utils`              | Contains all classes for helping and utilities     |
| `widgets`            | Contains all classes for custom views              |

#### Database Package

Under the Database Package we can have these:

| Package Name         | Description                                        |
| -------------------- |--------------------------------------------------- |
| `crud`               | Contains all crud operations (SQLite, Realm, ORM)  |
| `models`             | Contains all POJOs                                 |

#### HTTP Package

Under the HTTP Package we can have these:

| Package Name         | Description                                        |
| -------------------- |--------------------------------------------------- |
| `services`           | Contains all interfaces for network                |
| `models`             | Contains all POJOs                                 |


### Classes
Class names are written in [UpperCamelCase](http://en.wikipedia.org/wiki/CamelCase).

For classes that extend an Android component, the name of the class should end with the name of the component; for example: `SignInActivity`, `SignInFragment`, `ImageUploaderService`, `ChangePasswordDialog`.

### Resource Files
Resources file names are written in __lowercase_underscore__.

#### Drawable Files

Naming conventions for drawables:

| Asset Type   | Prefix            |		Example              |
|--------------| ------------------|-----------------------------|
| Action bar   | `ab_`             | `ab_stacked.9.png`          |
| Button       | `btn_`	           | `btn_send_pressed.9.png`    |
| Dialog       | `dialog_`         | `dialog_top.9.png`          |
| Divider      | `divider_`        | `divider_horizontal.9.png`  |
| Icon         | `ic_`	           | `ic_star.png`               |
| Menu         | `menu_	`          | `menu_submenu_bg.9.png`     |
| Notification | `notification_`   | `notification_bg.9.png`     |
| Tabs         | `tab_`            | `tab_pressed.9.png`         |

Naming conventions for icons (taken from [Android iconography guidelines](http://developer.android.com/design/style/iconography.html)):

| Asset Type                      | Prefix             | Example                      |
| --------------------------------| ----------------   | ---------------------------- |
| Icons                           | `ic_`              | `ic_star.png`                |
| Launcher icons                  | `ic_launcher`      | `ic_launcher_calendar.png`   |
| Menu icons and Action Bar icons | `ic_menu`          | `ic_menu_archive.png`        |
| Status bar icons                | `ic_stat_notify`   | `ic_stat_notify_msg.png`     |
| Tab icons                       | `ic_tab`           | `ic_tab_recent.png`          |
| Dialog icons                    | `ic_dialog`        | `ic_dialog_info.png`         |

Naming conventions for selector states:

| State	       | Suffix          | Example                     |
|--------------|-----------------|-----------------------------|
| Normal       | `_normal`       | `btn_order_normal.9.png`    |
| Pressed      | `_pressed`      | `btn_order_pressed.9.png`   |
| Focused      | `_focused`      | `btn_order_focused.9.png`   |
| Disabled     | `_disabled`     | `btn_order_disabled.9.png`  |
| Selected     | `_selected`     | `btn_order_selected.9.png`  |

#### Layout Files

Layout files should match the name of the Android components that they are intended for but moving the top level component name to the beginning. For example, if we are creating a layout for the `SignInActivity`, the name of the layout file should be `activity_sign_in.xml`.

| Component        | Class Name             | Layout Name                   |
| ---------------- | ---------------------- | ----------------------------- |
| Activity         | `UserProfileActivity`  | `activity_user_profile.xml`   |
| Fragment         | `SignUpFragment`       | `fragment_sign_up.xml`        |
| Dialog           | `ChangePasswordDialog` | `dialog_change_password.xml`  |
| AdapterView item | ---                    | `item_person.xml`             |
| Partial layout   | ---                    | `partial_stats_bar.xml`       |

A slightly different case is when we are creating a layout that is going to be inflated by an `Adapter`, e.g to populate a `ListView`. In this case, the name of the layout should start with `item_`.

Note that there are cases where these rules will not be possible to apply. For example, when creating layout files that are intended to be part of other layouts. In this case you should use the prefix `partial_`.

#### Menu Files

Similar to layout files, menu files should match the name of the component. For example, if we are defining a menu file that is going to be used in the `UserActivity`, then the name of the file should be `activity_user.xml`

A good practice is to not include the word `menu` as part of the name because these files are already located in the `menu` directory.

#### Values Files

Resource files in the values folder should be __plural__, 
e.g. 
`arrays.xml` - Arrays. Contains references to strings.xml
`strings.xml` - Localizable strings
`styles.xml` - Contains all Themes, Layout Styles
`colors.xml` - List of colors
`dimens.xml` - Dimensions used for layouts (e.g. padding, margins)
`attrs.xml` - Attributes used by classes / files in the app.
`config.xml` - Stores information to configure our project (e.g. urls, API Keys)
`plurals.xml` - Plurals. Contains references to strings.xml

Coding Guidelines
-----------------

#### Don't Ignore Exceptions

You must never do the following:

```java
void setServerPort(String value) {
    try {
        serverPort = Integer.parseInt(value);
    } catch (NumberFormatException e) { }
}
```

_While you may think that your code will never encounter this error condition or that it is not important to handle it, ignoring exceptions like above creates mines in your code for someone else to trip over some day. You must handle every Exception in your code in some principled way. The specific handling varies depending on the case.

#### Don't catch generic exception

You should not do this:

```java
try {
    someComplicatedIOFunction();        // may throw IOException
    someComplicatedParsingFunction();   // may throw ParsingException
    someComplicatedSecurityFunction();  // may throw SecurityException
    // phew, made it all the way
} catch (Exception e) {                 // I'll just catch all exceptions
    handleError();                      // with one generic handler!
}
```

See the reason why and some alternatives [here](https://source.android.com/source/code-style.html#dont-catch-generic-exception)

#### Don't use finalizers

_We don't use finalizers. There are no guarantees as to when a finalizer will be called, or even that it will be called at all. In most cases, you can do what you need from a finalizer with good exception handling. If you absolutely need it, define a `close()` method (or the like) and document exactly when that method needs to be called. See `InputStream` for an example. In this case it is appropriate but not required to print a short log message from the finalizer, as long as it is not expected to flood the logs._ - ([Android code style guidelines](https://source.android.com/source/code-style.html#dont-use-finalizers))

#### Fully Qualify Imports

This is bad: `import foo.*;`
This is good: `import foo.Bar;`

#### Treat Acronyms as Words

| Good           | Bad            |
| -------------- | -------------- |
| `XmlHttpRequest` | `XMLHTTPRequest` |
| `getCustomerId`  | `getCustomerID`  |
| `String url`     | `String URL`     |
| `long id`        | `long ID`        |

#### Use spaces for indentation

Use __4 space__ indents for blocks:

```java
if (x == 1) {
    x++;
}
```

Use __8 space__ indents for line wraps:

```java
Instrument i =
        someLongExpression(that, wouldNotFit, on, one, line);
```

### String Constants, Naming, and Values

Many elements of the Android SDK such as `SharedPreferences`, `Bundle`, or `Intent` use a key-value pair approach so it's very likely that even for a small app you end up having to write a lot of String constants.

When using one of these components, you __must__ define the keys as a `static final` fields and they should be prefixed as indicated below.

| Element            | Field Name Prefix |
| -----------------  | ----------------- |
| SharedPreferences  | `PREF_`             |
| Bundle             | `BUNDLE_`           |
| Fragment Arguments | `ARGUMENT_`         |
| Intent Extra       | `EXTRA_`            |
| Intent Action      | `ACTION_`           |

Note that the arguments of a Fragment - `Fragment.getArguments()` - are also a Bundle. However, because this is a quite common use of Bundles, we define a different prefix for them.

Example:

```java
// Note the value of the field is the same as the name to avoid duplication issues
static final String PREF_EMAIL = "PREF_EMAIL";
static final String BUNDLE_AGE = "BUNDLE_AGE";
static final String ARGUMENT_USER_ID = "ARGUMENT_USER_ID";

// Intent-related items use full package name as value
static final String EXTRA_SURNAME = "com.myapp.extras.EXTRA_SURNAME";
static final String ACTION_OPEN_USER = "com.myapp.action.ACTION_OPEN_USER";
```

### Self Closing Tags

When an XML element doesn't have any contents, you __must__ use self closing tags.

This is good:

```xml
<TextView
	android:id="@+id/text_view_profile"
	android:layout_width="wrap_content"
	android:layout_height="wrap_content" />
```

This is __bad__ :

```xml
<!-- Don\'t do this! -->
<TextView
    android:id="@+id/text_view_profile"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" >
</TextView>
```

### Layout XML ID Naming / Java Class Widget Declaration Variable

Always take the acronym for the view for example TextView = tv and make it lower camel case with the name.

| Element          | Prefix    | Example           |
| ---------------- | --------- | ----------------- |
| `TextView`       | `tv`      | `tvText`          |
| `ImageView`      | `iv`      | `ivImage`         |
| `Button`         | `btn`     | `btnSubmit`       |
| `RadioButton`    | `rb`      | `rbSelect`        |
| `EditText`       | `et`      | `etWords`         |
| `Spinner`        | `spinner` | `spinnerSelect`   |
| `ListView`       | `lv`      | `lvList`          |

### strings.xml

String names start with a prefix that identifies the section they belong to. For example `registration_email_hint` or `registration_name_hint`. If a string __doesn't belong__ to any section, then you should follow the rules below:

| Prefix             | Description                           |
| -----------------  | --------------------------------------|
| `app_`               | A general app text or message         |
| `error_`             | An error message                      |
| `success_`           | An success message                    |
| `caps_`              | An all caps message or text           |
| `required_`          | Indicates a requirement for a field   |
| `info_`              | A regular information message         |
| `title_`             | A title, i.e. a dialog title          |
| `action_`            | An action such as "Save" or "Create"  |

Git Ignore
----------

This is the base gitignore file for android. These files are the ones to be ignored once you are code sharing / having version control for your applications.

```gitignore
 # built application files
 *.apk
 *.ap_
 
 # files for the dex VM
 *.dex
 
 # java class files
 *.class
 
 # generated files
 bin/
 gen/
 
 # Eclipse project files
	
 .metadata
 .classpath
 .project
 .externalToolBuilders/
 .settings/
 lint.xml
 project.properties
 
 .gradle
 .idea/
 /build
 **/build
 **/production
 
 # Local Configuration file (sdk path, etc.)
 local.properties
 
 # Android Studio
 import-summary.txt
 *.iml
 *.iws
 *.ipr
 *.swp
 
 # others
 *.o
 *.so
 *.log
 .DS_Store
 Thumbs.db
```


List of Recommended Libraries / Third Party
-------------------------------------------

#### [Android Support Library](https://developer.android.com/topic/libraries/support-library/features.html)
Features from layout, to supporting compatibilities up to designs and widgets.

#### [Retrofit](http://square.github.io/retrofit/)

```xml
compile 'com.squareup.retrofit2:retrofit:2.0.2'
```
A type-safe HTTP client for Android and Java.

#### [OkHTTP](http://square.github.io/okhttp/)

```xml
compile 'com.squareup.okhttp3:okhttp:3.3.1'
```
An HTTP & HTTP/2 client for Android and Java applications.

#### [Picasso](http://square.github.io/picasso/)

```xml
compile 'com.squareup.picasso:picasso:2.5.2'
```
A powerful image downloading and caching library for Android.

#### [Glide](https://github.com/bumptech/glide/)

```xml
compile 'com.github.bumptech.glide:glide:3.7.0'
```
An image loading and caching library for Android focused on smooth scrolling.

#### [Universal Image Loader](https://github.com/nostra13/Android-Universal-Image-Loader/)

Powerful and flexible library for loading, caching and displaying images on Android.

#### [Otto](http://square.github.io/otto/)

```xml
compile 'com.squareup:otto:1.3.8'
```
An enhanced event bus with emphasis on Android support.

#### [Event Bus](https://github.com/greenrobot/EventBus/)

```xml
compile 'org.greenrobot:eventbus:3.0.0'
```
Android optimized event bus that simplifies communication between Activities, Fragments, Threads, Services, etc. Less code, better quality.

#### [Flurry Analytics](https://developer.yahoo.com/flurry/docs/analytics/gettingstarted/android/)

```xml
compile 'com.flurry.android:analytics:6.3.1'
```
Gain deep insight into your customer’s behavior very quickly and with little effort using Flurry’s Analytics service.

#### [Espresso](https://developer.android.com/training/testing/ui-testing/espresso-testing.html/)

```xml
dependencies {
    ...
    androidTestCompile 'com.android.support.test.espresso:espresso-core:2.2.1'
}
```
Testing user interactions within a single app helps to ensure that users do not encounter unexpected results or have a poor experience when interacting with your app. You should get into the habit of creating user interface (UI) tests if you need to verify that the UI of your app is functioning correctly.

#### [Robolectric](http://robolectric.org/)

Handles inflation of views, resource loading, and lots of other stuff that's implemented in native C code on Android devices. This allows tests to do most things you could do on a real device. It's easy to provide our own implementation for specific SDK methods too, so you could simulate error conditions or real-world sensor behavior.

#### [RxJava](https://github.com/ReactiveX/RxJava/)

A library for composing asynchronous and event-based programs using observable sequences for the Java VM.

#### [Retrolambda](https://github.com/orfjackal/retrolambda/)

Backport of Java 8's lambda expressions to Java 7, 6 and 5.

Other Sources
-------------

#### General Sources

[Android Arsenal](https://android-arsenal.com/)

[Code Path](https://github.com/codepath/android_guides/wiki/Must-Have-Libraries/)

[Android Libs](https://www.android-libs.com/)'

[Coursera Android](https://github.com/aporter/coursera-android/)

[Zserge Blog](http://zserge.com/blog.html/)

#### UI / UX

[Wasabeef Awesome Android UI](https://github.com/wasabeef/awesome-android-ui/)

[Snowdream Awesome Android](https://github.com/snowdream/awesome-android/)

[Code For Android](https://codeforandroid.wordpress.com/2015/02/09/android-sample-code/)

[Mockable.io](https://www.mockable.io/)

[InvisionApp](https://www.invisionapp.com/)

[Json Server](https://github.com/typicode/json-server/)

[Jorge Castillo Prz Awesome Android UI](https://github.com/jorgecastilloprz/awesome-android-ui/)

[Android Asset Studio](http://romannurik.github.io/AndroidAssetStudio/)

[Device Art Generator](https://developer.android.com/distribute/tools/promote/device-art.html/)

#### Proguard

[Android Common Proguard Snippets](https://github.com/krschultz/android-proguard-snippets/)

#### Emulators

[Genymotion](https://www.genymotion.com/)

[Bluestacks](http://www.bluestacks.com/)

#### Decompiler

[JADX](https://github.com/skylot/jadx/)
