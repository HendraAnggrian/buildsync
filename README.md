BuildConfig
===========
Generate Android-like `BuildConfig` class on any JVM projects.
Currently only supported with <b>IntelliJ IDEA</b>.

```java
public final class BuildConfig {
    public static final String NAME = "My App";
    public static final String GROUP = "my.package";
    public static final String VERSION = "1.0";

    private BuildConfig() {
    }
}
```

Download
--------
Add plugin to buildscript:

```gradle
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath 'com.hendraanggrian:buildconfig:0.8'
    }
}
```

then apply it in your module, along with idea plugin:

```gradle
apply plugin: 'idea'
apply plugin: 'buildconfig'
```

that's it, `BuildConfig` are now automatically generated after compilation with default behavior.

Usage
-----
Modify `BuildConfig` fields generation with `buildconfig` closure.

```gradle
group = 'com.example' // project group
version = '1.0'       // project version

buildconfig {
    name 'My App'      // `BuildConfig.NAME` value, default is project name
    group 'my.example' // `BuildConfig.GROUP` value, default is project group
    version '2.0'      // `BuildConfig.VERSION` value, default is project version
    debug true         // `BuildConfig.DEBUG` value
    
    // add custom field specifying its type, name, and value
    field String.class, "myString", "Hello world!"
    field double.class, "myDecimal", 12.0
}
```

License
-------
    Copyright 2017 Hendra Anggrian

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
