# ClaiR - C Language Analysis in Rascal

ClaiR provides a mapping from the Eclipse CDT open C and C++ front-end to a Rascal M3 model for further processing.
It can work with and without working from inside the Eclipse IDE.

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.891122.svg)](https://doi.org/10.5281/zenodo.891122)

## Required software

You need Rascal, and Either Eclipse or VScode or the standalone Rascal jar:
* Eclipse 2019-06 or higher with our without the CDT tools  (see [here](https://www.eclipse.org/downloads/packages/release/2019-06/r/eclipse-ide-cc-developers)). With the CDT tools you have some more tools to access information from CPP projects (like include paths), but otherwise Clair functions the same.
   * In Eclipse install the Rascal plugin from the update site: <https://update.rascal-mpl.org/stable/>
* Or, VScode with the Rascal extension 
   * Use the extension view in VScode to install Rascal
* Or, Rascal commandline (see [here](https://www.rascal-mpl.org/start/))

## How to use ClaiR once you have Rascal installed:

* Create an empty project "myproject" in a folder named "myproject"
* In `META-INF/RASCAL.MF` add `Project-Name: myproject` `Source: src` and `Require-Libraries: |lib://clair|
* In `pom.xml` add:
```
<dependency>
    <groupId>org.rascalmpl</groupId>
    <artifactId>clair</artifactId>
    <version>0.3.0</version>
</dependency>
```

## How to run
* In Eclipse's Project Explorer, right click a project's folder and select *Rascal Console*. The console should open inside Eclipse's terminal window with the title "Rascal [**project: <Project Name>**, mode: debug]". If, instead, it shows "project: none", make sure you clicked the project and the project is actually open.
* Or in VScode start a Rascal terminal from the command pallette, or from the "Start Rascal Terminal" action in an Rascal editor.
* Import ClaiR into the console by running `import lang::cpp::AST;`.
* To parse a string containing source code, call the `parseString` function, e.g., `parseString("int foo() { return 0; }")`.
* To parse source files on disk, call the `parseCpp` function with a source location, e.g., `parseCpp(|file:///tmp/example.cpp|)`, `parseCpp(|project://clair/src/test/test.cpp|)`, `parseCpp(|home://myFile.cpp|)`, or `parseCpp(|file://C:/My%20Dir/main.cpp|)`.
