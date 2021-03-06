# Overview

This is the follow up work of my accepted paper **Hierarchical Learning of Cross-Language Mappings through Distributed Vector Representations for Code** at <a href="https://www.icse2018.org/">the 40st International Conference in Software Engineering (ICSE'2018). </a>

We proposed a novel approach to learn the mappings across programming languages (Java & C#). Our result shows that we can mine 400 more mappings of the SDK library, which outperformed the state-of-the-art approaches. In this repo, we add such mappings into the configuration file, thus making the tool to be able to cover more translation cases. In short, our contributions in this repo are:

- Adding massive number of mappings and dependency jars into the core module, thus making the tool to be able to cover more translation cases.
- Fixing some minor bugs in the core module, adding more descriptive information on how to run the tool.

You can find the paper here: https://arxiv.org/abs/1803.04715.

For the original source code and more information, please refer to : https://github.com/mono/sharpen

# Sharpen - Automated Java->C# coversion

Sharpen is a library and command-line tool for automating Java to C# code conversion. You can provide configuration classes to control a wide range of class and functionality mapping.

Sharpen doesn’t provide a compatibility runtime (i.e, an implementation of all java functionality on top of .NET), but it does provide some utility classes to meet the most common needs. 

It’s likely that you will need to create a configuration class to customize and perfect your conversion, and you may need to apply patches to the result as well.

Sharpen was originally created by db40 [svn source here](https://source.db4o.com/db4o/trunk) in the format of an Eclipse plugin, but it has since been refactored to work from the command line and on build servers.


### Building and testing sharpen itself

1. Clone this repository
2. Install Java 7 and maven. Java 6 and 8 aren’t supported.
3. Run ‘mvn clean install -DskipTests’ to build the project and generate .jar files in /sharpen.core/target . Most of the test case taken from the original source code will fail if you don't add the parameter "-DskipTests".

### Running sharpen

1. `mvn install` should have created a file named `sharpencore-0.0.1-SNAPSHOT-jar-with-dependencies.jar`. This is a self-contained copy of sharpen that can be run anywhere.
2. Run `java -jar sharpencore-0.0.1-SNAPSHOT-jar-with-dependencies.jar SOURCEPATH -cp JAR_DEPENDENCY_A JAR_DEPENDENCY_B`  
    Each dependecy needed by the java source should be specified as a full path to the jar file. SOURCEPATH should also be a full path.
3. Run -help for syntax

### Tips

If you want to add more mappings, go to <a href="https://github.com/bdqnghi/sharpen-java2csharp/blob/master/src/main/sharpen/core/DefaultConfiguration.java">DefaultConfiguration</a> to add more mappings and rebuild the package. Trying to use an external configuration file will lead you to some configuration trouble, which is not worthwhile.
