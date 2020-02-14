# Build notes:

This is a supplemental to the instructions in README.SRC.txt.  Please read that before this file.  In order to build this application you need a Java 11 JDK installed and configured.  The easiest way to do this is to first instal jEnv if you are on Linux or OSX, or Jabba if you are on Windows.

## Installing JEnv

[JEnv homepage](https://www.jenv.be/)

For Linux, you use the following according to the JEnv website:

```
git clone https://github.com/gcuisinier/jenv.git ~/.jenv
echo 'export PATH="$HOME/.jenv/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(jenv init -)"' >> ~/.bash_profile
```

After that you need to restart your shell (or logout/login) to take effect.

For OSX you can simply use `brew install jenv`

After installing the Java 11 JDK, use `jenv add PATH` where PATH is the root path of the installation folder for Java JDK 11.

## Installing Jabba

[Jabba](https://github.com/shyiko/jabba#installation) can be installed from the Windows PowerShell environment.  You might first [have to enable scripts](https://stackoverflow.com/questions/16460163/ps1-cannot-be-loaded-because-the-execution-of-scripts-is-disabled-on-this-syste) and answer the security confirmation prompt:  `Set-ExecutionPolicy Unrestricted` and then use the following to download and install Jabba:
```
Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
Invoke-Expression (
  Invoke-WebRequest https://github.com/shyiko/jabba/raw/master/install.ps1 -UseBasicParsing
).Content
```
After that you can type `jabba install openjdk@1.11.0` to install JDK 11.

## Building

You need Apache Ant in your path.  For more information see the Apache Ant homepage for your operating system.

You should only need to type `ant build` to generate the build/jedit.jar.

If you would like to build from IntelliJ, you must first add the JSR305 annotations library to Project Settings > Modules > Dependencies and select + (add) and finally choose Maven and search for JSR305.

## Executing

From the build folder and Java 11 in your path, invoke via `java -jar jedit.jar` -- If you get errors that it cannot find files in build/doc you can work around this by copying the doc folder from the root folder into the build folder.  In a more ideal world this would be a maven project and the doc folder would be under src/resources and things would happen automatically, but this is an Ant/Ivy project and therefore unless you run with `ant run` expect a few surprises.
