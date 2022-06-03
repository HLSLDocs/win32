# Preprocessor Directives

## \#define directive (constant)

Preprocessor directive that assigns a meaningful name to a constant in your application.



| \#define *identifiertoken-string* |
|-----------------------------------|



 

### Parameters



| Item                                                                                                                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|----------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span id="identifier"></span><span id="IDENTIFIER"></span>*identifier*<br/>                                          | Identifier of the constant. <br/>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| <span id="token-string__optional_"></span><span id="TOKEN-STRING__OPTIONAL_"></span>*token-string* \[optional\]<br/> | Value of the constant. This parameter consists of a series of tokens, such as keywords, constants, or complete statements. One or more white-space characters must separate this parameter from the *identifier* parameter; this white space is not considered part of the substituted text, nor is any white space following the last token of the text. <br/> If you exclude this parameter, all instances of the *identifier* parameter are removed from the source file. The identifier remains defined, and can be tested using the [\#if defined](dx-graphics-hlsl-appendix-pre-ifdef.md), \#ifdef, and \#ifndef directives. <br/> |



 

### Remarks

All instances of the *identifier* parameter that occur after the [\#define](dx-graphics-hlsl-appendix-pre-define.md) directive in the source file will be replaced by the value of the *token-string* parameter. The identifier is replaced only when it forms a token; for example, the identifier is not replaced if it appears in a comment, within a string, or as part of a longer identifier.

The [\#undef](dx-graphics-hlsl-appendix-pre-undef.md) directive instructs the preprocessor to forget the definition of an identifier; for more information, see \#undef Directive (DirectX HLSL).

Defining constants with the /D compiler option has the same effect as using the [\#define](dx-graphics-hlsl-appendix-pre-define.md) directive at the beginning of your file. Up to 30 constants can be defined with the /D option. For an example of how this can be used, see the Examples section of [\#ifdef and )](dx-graphics-hlsl-appendix-pre-ifdef.md).

### Examples

The following example defines the identifier WIDTH as the integer constant 80 and then defines LENGTH in terms of WIDTH and the integer constant 10.


```
#define WIDTH       80
#define LENGTH      ( WIDTH + 10 )
```



Every subsequent instance of LENGTH is replaced by (WIDTH + 10), and every subsequent instance of WIDTH + 10 is replaced by the expression (80 + 10). The parentheses around WIDTH + 10 are important because they control the interpretation in statements such as the following.


```
var = LENGTH * 20;
```



After the preprocessing stage the statement becomes the following, which evaluates to 1,800.


```
var = ( 80 + 10 ) * 20;
```



Without parentheses, the result would be the following, which evaluates to 280.


```
var = 80 + 10 * 20;
```

## \#define directive (macro)

Preprocessor directive that creates a function-like macro.



| \#define *identifier*( *argument0*, ... , *argumentN-1* ) *token-string* |
|--------------------------------------------------------------------------|



 

### Parameters



| Item                                                                                                                                                                                                                                                          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span id="identifier"></span><span id="IDENTIFIER"></span>*identifier*<br/>                                                                                                                                                                             | Identifier of the macro. <br/> A second [\#define](dx-graphics-hlsl-appendix-pre-define.md) for a macro with an identifier that already exists in the current context generates an error unless the second token sequence is identical to the first. <br/>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <span id="___________argument0___...___argumentN-1_________"></span><span id="___________argument0___...___argumentn-1_________"></span><span id="___________ARGUMENT0___...___ARGUMENTN-1_________"></span> ( *argument0*, ... , *argumentN-1* ) <br/> | List of arguments to the macro. The argument list is comma-delimited, can be of any length, and must be enclosed in parentheses. Each argument name in the list must be unique. No white space can separate the *identifier* parameter and the opening parenthesis. <br/> Use line concatenation place a backslash (\\) immediately before the newline character to split long directives onto multiple source lines. <br/>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <span id="token-string__optional________"></span><span id="TOKEN-STRING__OPTIONAL________"></span>*token-string* \[optional\] <br/>                                                                                                                     | Value of the macro. This parameter consists of a series of tokens, such as keywords, constants, or complete statements. One or more white-space characters must separate this parameter from the *identifier* parameter; this white space is not considered part of the substituted text, nor is any white space following the last token of the text. Make liberal use of parentheses to ensure that complicated arguments are interpreted correctly. <br/> If the value of the *identifier* parameter occurs within the *token-string* parameter (even as a result of another macro expansion), it is not expanded. <br/> If you exclude this parameter, all instances of the *identifier* parameter are removed from the source file. The identifier remains defined, and can be tested using the [\#if defined](dx-graphics-hlsl-appendix-pre-ifdef.md), \#ifdef, and \#ifndef directives. <br/> |



 

### Remarks

All instances of the *identifier* parameter that occur after the [\#define](dx-graphics-hlsl-appendix-pre-define.md) directive in the source file constitute a macro call, and the identifier will be replaced by a version of the *token-string* parameter that has actual arguments substituted for formal parameters. The number of parameters in the call must match the number of parameters in the macro definition. The identifier is replaced only when it forms a token; for example, the identifier is not replaced if it appears in a comment, within a string, or as part of a longer identifier.

The [\#undef](dx-graphics-hlsl-appendix-pre-undef.md) directive instructs the preprocessor to forget the definition of an identifier; for more information, see \#undef Directive (DirectX HLSL).

Defining constants with the /D compiler option has the same effect as using the [\#define](dx-graphics-hlsl-appendix-pre-define.md) directive at the beginning of your file. Up to 30 macros can be defined with the /D option.

The actual arguments in the macro call are matched to the corresponding formal arguments in the macro definition. Each formal argument in the token string is replaced by the corresponding actual argument, unless the argument is preceded by a stringizing (\#), charizing (\#@), or token-pasting (\#\#) operator, or is followed by a \#\# operator. Any macros in the actual argument are expanded before the directive replaces the formal parameter.

Token pasting in the HLSL compiler is slightly different from token pasting in the C compiler, in that the pasted tokens must be valid tokens on their own. For example, consider the following macro definition:


```
#define MERGE(a, b) a##b
MERGE(float, 4x4) test;
```



In the C compiler, this results in the following:


```
float4x4 test
```



In the HLSL compiler however, this results in the following:


```
float4 x4 test
```



You can work around this behavior by using the following macro definition instead.


```
MERGE(MERGE(float, 4), x4) test;
```



### Examples

The following example uses a macro to define cursor lines.


```
#define CURSOR(top, bottom) (((top) << 8) | (bottom))
```



The following example defines a macro that retrieves a pseudorandom integer in the specified range.


```
#define getrandom(min, max) \
((rand()%(int)(((max) + 1)-(min)))+ (min))
```

## \#error Directive

Preprocessor directive that produces compiler-time error messages.



| \#error *token-string* |
|------------------------|



 

### Parameters



| Item                                                                                    | Description                                                                                                                                                                    |
|-----------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span id="token-string"></span><span id="TOKEN-STRING"></span>*token-string*<br/> | Error message. This parameter consists of a series of tokens, such as keywords, constants, or complete statements. The token string is subject to macro expansion. <br/> |



 

### Remarks

\#error directives are most useful for detecting programmer inconsistencies and violation of constraints during preprocessing. When an \#error directive is encountered, compilation terminates.

### Examples

The following example demonstrates error processing during preprocessing.


```
#if !defined(__cplusplus)
  #error C++ compiler required.
#endif
```

## \#if, \#elif, \#else, and \#endif Directives

Preprocessor directives that control compilation of portions of a source file.



| \#if *ifCondition* ...         |
|--------------------------------|
| \[\#elif *elifCondition* ...\] |
| \[\#else ...\]                 |
| \#endif                        |



 

### Parameters



| Item                                                                                                                                                                                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span id="ifCondition"></span><span id="ifcondition"></span><span id="IFCONDITION"></span>*ifCondition*<br/>                                                                                   | Primary condition to evaluate. If this parameter evaluates to a nonzero value, all text between this \#if directive and the next instance of the \#elif, \#else, or \#endif directive is retained in the translation unit; otherwise, the subsequent source code is not retained. <br/> The condition can use the preprocessor operator defined to determine whether a specific preprocessor constant or macro is defined; this usage is equivalent to the use of the [\#ifdef](dx-graphics-hlsl-appendix-pre-ifdef.md) directive. <br/> See the Remarks section for restrictions on the value of the *ifCondition* parameter. <br/>                                                                                        |
| <span id="elifCondition__optional__________"></span><span id="elifcondition__optional__________"></span><span id="ELIFCONDITION__OPTIONAL__________"></span>*elifCondition* \[optional\] <br/> | Other condition to evaluate. If the *ifCondition* parameter and all previous \#elif directives evaluate to zero, and this parameter evaluates to a nonzero value, all text between this \#elif directive and the next instance of the \#elif, \#else, or \#endif directive is retained in the translation unit; otherwise, the subsequent source code is not retained. <br/> The condition can use the preprocessor operator defined to determine whether a specific preprocessor constant or macro is defined; this usage is equivalent to the use of the [\#ifdef](dx-graphics-hlsl-appendix-pre-ifdef.md) directive. <br/> See the Remarks section for restrictions on the value of the *elifCondition* parameter. <br/> |



 

### Remarks

Each \#if directive in a source file must be matched by a closing \#endif directive. Any number of \#elif directives can appear between the \#if and \#endif directives, but at most one \#else directive is allowed. The \#else directive, if present, must be the last directive before \#endif. Conditional-compilation directives contained in include files must satisfy the same conditions.

The \#if, \#elif, \#else, and \#endif directives can nest in the text portions of other \#if directives. Each nested \#else, \#elif, or \#endif directive belongs to the closest preceding \#if directive.

If no conditions evaluate to a nonzero value, the preprocessor selects the text block after the \#else directive. If the \#else clause is omitted and no conditions evaluate to a nonzero value, no text block is selected.

The *ifCondition* and *elifCondition* parameters much meet the following requirements:

-   Conditional compilation expressions are treated as [**signed long**](https://msdn.microsoft.com/library/cc953fe1(v=VS.71).aspx) values, and these expressions are evaluated using the same rules as expressions in C++.
-   Expressions must have integral type and can include only integer constants, character constants, and the defined operator.
-   Expressions cannot use **sizeof** or a type-cast operator.
-   The target environment may not be able to represent all ranges of integers.
-   The translation represents type [**int**](/windows/desktop/WinProg/windows-data-types) the same as type **long**, and [**unsigned int**](https://msdn.microsoft.com/library/cc953fe1(v=VS.71).aspx) the same as **unsigned long**.
-   The translator can translate character constants to a set of code values different from the set for the target environment. To determine the properties of the target environment, check values of macros from LIMITS.H in an application built for the target environment.
-   The expression must not perform any environmental inquiries and must remain insulated from implementation details on the target computer.

### Examples

This section contains examples that demonstrate how to use conditional compilation preprocessor directives.

#### Use of the defined operator

The following example shows the use of the defined operator. If the identifier CREDIT is defined, the call to the **credit** function is compiled. If the identifier DEBIT is defined, the call to the **debit** function is compiled. If neither identifier is defined, the call to the **printerror** function is compiled. Note that "CREDIT" and "credit" are distinct identifiers in C and C++ because their cases are different.


```
#if defined(CREDIT)
    credit();
#elif defined(DEBIT)
    debit();
#else
    printerror();
#endif
```



#### Use of nested \#if directives

The following example shows how to nest \#if directives. This example assumes that a symbolic constant named DLEVEL has been previously defined. The \#elif and \#else directives are used to make one of four choices, based on the value of DLEVEL. The constant STACK is set to 0, 100, or 200, depending on the definition of DLEVEL. If DLEVEL is greater than 5, then STACK is not defined.


```
#if DLEVEL > 5
    #define SIGNAL  1
    #if STACKUSE == 1
        #define STACK   200
    #else
        #define STACK   100
    #endif
#else
    #define SIGNAL  0
    #if STACKUSE == 1
        #define STACK   100
    #else
        #define STACK   50
    #endif
#endif
#if DLEVEL == 0
    #define STACK 0
#elif DLEVEL == 1
    #define STACK 100
#elif DLEVEL > 5
    display( debugptr );
#else
    #define STACK 200
#endif
```



#### Use for including header files

A common use for conditional compilation is to prevent multiple inclusions of the same header file. In C++, where classes are often defined in header files, conditional compilation constructs can be used to prevent multiple definitions. The following example determines whether the symbolic constant EXAMPLE\_H is defined. If so, the file has already been included and does not need to be reprocessed; if not, the constant EXAMPLE\_H is defined to indicate that EXAMPLE.H has already been processed.


```
#if !defined( EXAMPLE_H )
#define EXAMPLE_H

class Example
{
...
};

#endif // !defined( EXAMPLE_H )
```

## \#ifdef and \#ifndef Directives

Preprocessor directives that determine whether a specific preprocessor constant or macro is defined.



| \#ifdef *identifier* ...  |
|---------------------------|
| \#endif                   |
| \#ifndef *identifier* ... |
| \#endif                   |



 

### Parameters



| Item                                                                              | Description                                               |
|-----------------------------------------------------------------------------------|-----------------------------------------------------------|
| <span id="identifier"></span><span id="IDENTIFIER"></span>*identifier*<br/> | Identifier of the constant or macro to check. <br/> |



 

### Remarks

You can use the \#ifdef and \#ifndef directives anywhere that the [\#if](dx-graphics-hlsl-appendix-pre-if.md) can be used. The \#ifdef statement is equivalent to ) directive. These directives check only for the presence or absence of identifiers defined using the [\#define](dx-graphics-hlsl-appendix-pre-define.md) directive, not for identifiers declared in the C or C++ source code.

These directives are provided only for compatibility with previous versions of the language. The use of the [defined](dx-graphics-hlsl-appendix-pre-if.md) operator with the \#if directive is preferred.

The \#ifndef directive checks for the opposite of the condition checked by \#ifdef. If the identifier is not defined, the condition is true (nonzero); otherwise, the condition is false (zero).

### Examples

The identifier can be passed from the command line using the /D option. Up to 30 macros can be specified with /D. This is useful for checking whether a definition exists, because a definition can be passed from the command line. The following example uses this behavior to determine whether to run an application in test mode.


```
// PROG.CPP
#ifndef test
  #define final
#endif
int main()
{
}
```



When compiled using the following command, prog.cpp will compile in test mode; otherwise, it will compile in final mode.


```
CL.EXE /Dtest prog.cpp
```

## \#include Directive

Preprocessor directive that inserts the contents of the specified file into the source program at the point where the directive appears.


| \#include "*filename*"       |
|------------------------------|
| \#include <*filename*> |

### Parameters

| Item | Description |
|------|-------------|
| *filename* | Filename of the file to include, optionally preceded by a directory specification. The filename must specify an existing file. |

### Remarks

The \#include directive causes replacement of the directive by the entire contents of the specified file. The preprocessor stops searching as soon as it finds a file with the specified name; if you specify a complete, unambiguous path specification for the file, the preprocessor searches only the specified path.

> [!NOTE]
> The [Effect-Compiler Tool](/windows/desktop/direct3dtools/fxc) has a built-in include handler using the /I switch. However, when executing the compiler from the API, you can provide a customized include handler by implementing the ID3DXInclude interface.

The difference between the two syntax forms is the order in which the preprocessor searches for header files when the path is incompletely specified, as shown in the following table.

<table>
<colgroup>
<col  />
<col  />
</colgroup>
<thead>
<tr class="header">
<th>Syntax form</th>
<th>Preprocessor search pattern</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>#include <b>&quot;</b><em>filename</em><b>&quot;</b></td>
<td>Searches for the include file:
<ol>
<li>in the same directory as the file that contains the #include directive.</li>
<li>in the directories of any files that contain a #include directive for the file that contains the #include directive.</li>
<li>in paths specified by the /I compiler option, in the order in which they are listed.</li>
<li><p>in paths specified by the INCLUDE environment variable, in the order in which they are listed.</p>
<blockquote>
[!NOTE]<br />
The INCLUDE environment variable is ignored in an development environment. Refer to your development environment's documentation for information about how to set the include paths for your project.
</blockquote>
<p><br/></p></li>
</ol></td>
</tr>
<tr class="even">
<td>#include <b><</b><em>filename</em><b>></b></td>
<td>Searches for the include file:
<ol>
<li>in paths specified by the /I compiler option, in the order in which they are listed.</li>
<li><p>in paths specified by the INCLUDE environment variable, in the order in which they are listed.</p>
<blockquote>
[!NOTE]<br />
The INCLUDE environment variable is ignored in an development environment. Refer to your development environment's documentation for information about how to set the include paths for your project.
</blockquote>
<p><br/></p></li>
</ol></td>
</tr>
</tbody>
</table>

### Examples

The following example causes the preprocessor to replace the \#include directive with the contents of stdio.h. Because the example uses the angle bracket format, the preprocessor will search for the file only in the directories listed by the /I compiler option and the INCLUDE environment variable.

```cpp
#include <stdio.h>
```

## \#line Directive

Preprocessor directive that sets the compiler's internally-stored line number and filename to the specified values.



| \#line *lineNumber* "*filename*" |
|----------------------------------|



 

### Parameters



| Item                                                                                                                              | Description                                                                                                                                                                                                  |
|-----------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span id="lineNumber"></span><span id="linenumber"></span><span id="LINENUMBER"></span>*lineNumber*<br/>                    | Line number to set. This can be any integer constant. Macro replacement can be performed on the preprocessing tokens, as long as the result evaluates to the correct syntax. <br/>                     |
| <span id="filename__optional__________"></span><span id="FILENAME__OPTIONAL__________"></span>*filename* \[optional\] <br/> | Filename to set. The filename can be any combination of characters, and must be enclosed in double quotation marks (" "). If this parameter is omitted, the previous filename remains unchanged. <br/> |



 

### Remarks

The compiler uses the line number and filename to refer to errors that it finds during compilation. The line number usually refers to the current input line, and the filename refers to the current input file. The line number is incremented after each line is processed. If you change the line number and filename, the compiler ignores the previous values and continues processing with the new values. The \#line directive is typically used by program generators to cause error messages to refer to the original source file instead of to the generated program.

The translator uses the line number and filename to determine the values of the predefined macros \_\_FILE\_\_ and \_\_LINE\_\_. You can use these macros to insert self-descriptive error messages into the program text. The \_\_FILE\_\_ macro expands to a string whose contents are the filename, surrounded by double quotation marks (" ").

### Examples

The following example sets the line number to 151 and the filename to "copy.c".


```
#line 151 "copy.c"
```



In the following example, the macro ASSERT uses the predefined macros \_\_LINE\_\_ and \_\_FILE\_\_ to print an error message about the source file if the specified assertion is not true.


```
#define ASSERT(cond)

if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## \#pragma Directive

Preprocessor directive that provides machine-specific or operating system-specific features while retaining overall compatibility with the C and C++ languages.



| \#pragma *token-string* |
|-------------------------|



 

### Parameters



| Item                                                                                    | Description                                                                                                                              |
|-----------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| <span id="token-string"></span><span id="TOKEN-STRING"></span>*token-string*<br/> | Series of characters that gives a specific compiler instruction and arguments. This parameter is subject to macro expansion. <br/> |



 

### Remarks

If the compiler finds a pragma it does not recognize, it issues a warning, but compilation continues.

The HLSL compiler recognizes the following pragmas:

-   [def](dx-graphics-hlsl-appendix-pre-pragma-def.md)
-   [message](message-pragma-directive--directx-hlsl-.md)
-   [pack\_matrix](dx-graphics-hlsl-appendix-pre-pragma-pack-matrix.md)
-   [warning](dx-graphics-hlsl-appendix-pre-pragma-warning.md)

## warning pragma Directive

Pragma directive that modifies the behavior of compiler warning messages.



| \#pragma warning( *warning-specifier* : *warning-number-list* \[; *warning-specifier* : *warning-number-list*...\] ) |
|----------------------------------------------------------------------------------------------------------------------|



 

### Parameters



<table>
<colgroup>
<col  />
<col  />
</colgroup>
<thead>
<tr class="header">
<th>Item</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="warning-specifier"></span><span id="WARNING-SPECIFIER"></span><em>warning-specifier</em><br/></td>
<td>Behavior to set for the specified warnings. This parameter can take one of the values listed in the following table. <br/> 
<table>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>once</td>
<td>Display the message of the warnings with the specified numbers only once.</td>
</tr>
<tr class="even">
<td>default</td>
<td>Reset the behavior of the warnings with the specified numbers to their default value. This also has the effect of turning a warning on that is off by default. The warning will be generated at its default level.</td>
</tr>
<tr class="odd">
<td>1, 2, 3, 4</td>
<td>Apply the specified level to the warnings with the specified numbers. This also has the effect of turning a warning on that is off by default.</td>
</tr>
<tr class="even">
<td>disable</td>
<td>Do not issue the warnings with the specified numbers.</td>
</tr>
<tr class="odd">
<td>error</td>
<td>Report the warnings with the specified numbers as errors.</td>
</tr>
</tbody>
</table>

<p> </p></td>
</tr>
<tr class="even">
<td><p><span id="warning-number-list"></span><span id="WARNING-NUMBER-LIST"></span><em>warning-number-list</em></p></td>
<td><p>White space-delimited list of the numbers of the warnings to modify the behavior of.</p></td>
</tr>
</tbody>
</table>



 

### Remarks

You can specify any number of distinct warning behavior changes within the same warning pragma by separating the changes with semicolons.

The compiler will add 4000 to any warning number that is between 0 and 999. For warning numbers greater than 4699, (those associated with code generation) the warning pragma has effect only when placed outside function definitions. The pragma is ignored if it specifies a number greater than 4699 and is used inside a function.

The HLSL warning pragma does not support the **push** and **pop** functionality of the warning pragma included in the C++ compiler.

### Examples

The following example disables warnings 4507 and 4034, displays warning 4385 once, and reports warning 4164 as an error.


```
#pragma warning( disable : 4507 34; once : 4385; error : 164 )
```



The preceding example is functionally equivalent to the following:


```
#pragma warning( disable : 4507 34 )
#pragma warning( once : 4385 )
#pragma warning( error : 164 )
```

## def pragma Directive

Pragma directive that manually allocates a floating-point shader register.



| \#pragma def( *target*, *register*, *val1*, *val2*,*val3*, *val4* ) |
|---------------------------------------------------------------------|



 

### Parameters



| Item                                                                        | Description                                                                 |
|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| <span id="target"></span><span id="TARGET"></span>*target*<br/>       | Target that contains the register to allocate. <br/>                  |
| <span id="register"></span><span id="REGISTER"></span>*register*<br/> | Floating-point shader register to allocate. <br/>                     |
| <span id="val0"></span><span id="VAL0"></span>*val0*<br/>             | First byte of the value to allocate to the specified register. <br/>  |
| <span id="val1"></span><span id="VAL1"></span>*val1*<br/>             | Second byte of the value to allocate to the specified register. <br/> |
| <span id="val2"></span><span id="VAL2"></span>*val2*<br/>             | Third byte of the value to allocate to the specified register. <br/>  |
| <span id="val3"></span><span id="VAL3"></span>*val3*<br/>             | Fourth byte of the value to allocate to the specified register. <br/> |



 

### Remarks

The def pragma allows a developer to prefill a floating-point shader register with the specified value. This pragma is infrequently used.

## pack\_matrix pragma Directive

Pragma directive that specifies packing alignment for matrices.



| \#pragma pack\_matrix( *alignment* ) |
|--------------------------------------|



 

### Parameters



<table>
<colgroup>
<col  />
<col  />
</colgroup>
<thead>
<tr class="header">
<th>Item</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="alignment"></span><span id="ALIGNMENT"></span><em>alignment</em><br/></td>
<td>Alignment to set for matrices. This parameter can take one of the values listed in the following table. <br/> 
<table>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>column_major</td>
<td>Default. Sets the matrix packing alignment to column major.</td>
</tr>
<tr class="even">
<td>row_major</td>
<td>Sets the matrix packing alignment to row major.</td>
</tr>
</tbody>
</table>

<p> </p></td>
</tr>
</tbody>
</table>



 

### Examples

The following example sets the matrix packing alignment to row major.


```
#pragma pack_matrix( row_major )
```

## \#undef Directive

Preprocessor directive that removes the current definition of a constant or macro that was previously defined using the [\#define](dx-graphics-hlsl-appendix-pre-define.md) directive.



| \#undef *identifier* |
|----------------------|



 

### Parameters



| Item                                                                              | Description                                                                                                                                                      |
|-----------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span id="identifier"></span><span id="IDENTIFIER"></span>*identifier*<br/> | Identifier of the constant or macro to remove the definition of. If you are undefining a macro, provide only the identifier, not the parameter list. <br/> |



 

### Remarks

You can apply the \#undef directive to an identifier that has no previous definition; this ensures that the identifier is undefined. Macro replacement is not performed within \#undef statements.

The \#undef directive is typically paired with a [\#define](dx-graphics-hlsl-appendix-pre-define.md) directive to create a region in a source program in which an identifier has a special meaning. For example, a specific function of the source program can use manifest constants to define environment-specific values that do not affect the rest of the program. The \#undef directive also works with the [) directive to control conditional compilation of the source program.

Constants and macros can be undefined from the command line using the /U option, followed by the identifiers to be undefined. This is equivalent to adding a sequence of \#undef directives at the beginning of the source file.

### Examples

The following example shows how to use the \#undef directive to remove definitions of a symbolic constant and a macro.


```
#define WIDTH           80
#define ADD( X, Y )     (X) + (Y)

#undef WIDTH
#undef ADD
```