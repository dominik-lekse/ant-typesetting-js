#ant-typesetting-js

## Introduction
*ant-typesetting-js* extends the Apache Ant system to support compiling (La)TeX documents.

* Light-weight
* Easy integratation
* Plain JavaScript
* Single task between an Ant build definition and a TeX compiler
* No need for extending the class path by additional JARs

## Features
The features can be inferred from the list of parameters of the primary task `<typeset />` or take a look at the example `build.xml` in this repository.

## Requirements
*ant-typesetting-js* has been tested in the following environment.

* Apache Ant 1.9.4
* Java 1.7

## Usage
1. Copy the library script `ant-typesetting-js.xml` into your document or project folder.
2. Include the library file in your custom `build.xml`.
 
	```
	\<!-- ant-typesetting-js library -->
	<import file="${basedir}/ant-typesetting-js.xml" />
	```
3. Use the `<typeset />` task to compile a TeX document.

	```
	<typeset document="documents/test.tex" documentclass="article" documentattributes="12pt" inputpathref="resources.inputpath" cache="true" cachedir="cache" outputdir="build" outputname="test-document" documentcompiler="lualatex" externalizecompiler="lualatex" verbose="false" />
	```

## FAQ

There are no questions so far in this section. Feel free to ask.

## Tasks
In this section, a description of available tasks as well as an explanation of  their parameters is provided.

### \<typeset />

Parameter | Description | Required | Default
--- | --- | :---: | ---
*document* | Provides the path to the TeX document to compile. | Yes | 
*documentclass* | Specifies the document class which replaces the document class given in the first line of the TeX document. This replacement is useful, e.g. if you need to compile the same TeX source against multiple document classes. The task always overrides the document class of document such that this parameter is mandatory. | Yes |
*documentattributes* | Provides a list of attributes which is passed to the document class. | No | ""
*basedir* | Specifies the directory in which the TeX compiler is executed. | No | ${basedir}
*inputpathref* | References a [path-like structure](http://ant.apache.org/manual/using.html#path) which is used as *TEXINPUTS* during the TeX run. This feature is like a class path, but for TeX. Usually, this helps to keep images, tables, figures, etc. in separate directories in your project folder. | No | 
*outputname*  | Defines the name of the output document, which corresponds to the `-jobname` parameter of the TeX compiler. By default, the name of the TeX document is used.  | No | 
*outputdir*  | Specifies the directory which the TeX compiler uses for its output. | No | 
*cache* | If true, the externalize functionality provided by the PGF/TikZ package is enabled. If you intend to use this feature enable set this attribute *true* ensure compatibility. Otherwise, externalizing PGF or TikZ pictures will fail. | No | false
*cachedir* | Specifies the directory which is used for caching PGF or TikZ pictures. | No | 
*locale* | Allows to pass a locale parameter to the document, which is useful in case of multi-language documents. A language abbreviation such as "en" or "de" is provided by the LaTeX macro `\locale` in the document. | No | 
*draft* | If true, the TeX compiler is invoked with the `-draftmode` argument. | No | false
*verbose* | If true, the tasks passes through the output of the TeX compiler. If false, only errors are passed through. | No | false
*documentcompiler*  | The executable of the TeX compiler to be used for the document. | No | lualatex
*externalizecompiler* | The executable of the TeX compiler to be used for PGF/TikZ externalize passes. | No | lualatex
