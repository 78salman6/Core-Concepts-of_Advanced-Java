# Keys to ease pain in Intellij:

1. Enter **Shift key 2 times** to search everywhere
2. **Alt + 1** to **show directory structure** of project
3. If you click anywhere in Editor window then press **F1 that will take you to online help available** for F1
4. If you click anywhere in Project directory window and then press F1 that will take to online help of Project Tool Window
5. CTRL + q
6. For search and replace - **CTRL + r**
7. Put cursor on variable then - Refactor then rename to rename it in all place ( Shift + F6 )
8. For going to line having error - press **F2**
9. View -> Tool Windows -> TODO ( it will allow to add todo ) and you will be able to access it from today bar
10. F11 to bookmark any code of any class
11. Alt + 2 ( Opens favorite window ) -> You will find all your bookmarks here
12. For making any window to floating window -> Setting -> View Mode -> Float

# Keyboard short cut for speeding up coding

1. To delete a line - Ctrl + y on that line
2. Alt + Shift + Down arrow to place code at bottom
3. To navigate to the beginng or end of a code block - Ctrl + { -> start, Ctrl + } -> end
4. For getting all shortcuts -> Help -> Keymap shortcuts

> Reference - https://resources.jetbrains.com/storage/products/intellij-idea/docs/IntelliJIDEA_ReferenceCard.pdf

# Create new Java classes and interface:

Structure of template can be modified. To change template -> Settings -> Editor -> File and Code Templates
For implementing an interface from a class hover over the error then click on implement method ( Or Alt + Enter )- V.V.I

# Live templates:

Intellij IDEA has a feature named Live Templates that lets you associate and abbreviate with a block of code. When you type in the abbreviation and press tab or enter or return, that abbreviation expands to the complete block.

## Some standard live templates that are already defined in Intellij IDEA:

    1. sout -> System.out.println("");
    2. souf -> System.out.printf("");
    3. psf -> public static final
    4. psfi -> public static final int
    5. psfs -> public static final String
    6. fori -> for (int i = 0; i < ; i++) { }
    7. foreach

## For creating your own Live templates

Settings -> Live Editor

**Reformat code** -> Unindent code ( in which whitespace can be in any form ) -> Select code block which you want to reformat -> Code -> Reformat Code

## Configuring custom Reformat code

File -> Settings -> Editor
**Change style of comment in Intellij**
File -> Settings -> Editor -> Code Generation tab -> Uncheck "Line comment at first column"

**Deletes all unused import statements** ----> Code -> Optimize Imports

# Navigate code and find Files:

See the home page when you opens a project
For search in all -> Double shift
For search for file -> CTRL + SHIFT + N
Search Class -> CTRL + n

# Search throughout your entire project

**For finding out all places where particular method or classes are being used** with a tool called Find Usages -> Put cursor on the method then press -> ALT + F7

**For finding where class is being used** -> Close all files -> Then select class for which you want to search the usage -> ALT + F7

Galat code likho list ya koi collection ka -> hover on that line CTRL + Shift + ALT + T -> Generify -> Refactor

**For moving code block in a method** -> Select all lines which you want to move
Refactor -> Extract/Introduce -> Method

**For changing into constant**
Refactor -> Extract/Introduce -> Constant
**Extract local variable field**

## Breakpoints:

1. CTRL + F8 on line on which you want to put breakpoints
2. Evaluate Expression by clicking right on variable ( Powerful tool )
3. You Can add any valid variable operation in debug window by clicking + icon
4. You can select a variable and then right click and then Add to watches

# JavaDoc:

JovaDoc is a tool which is included with JDK. It knows how to parse your source code and extract specially formatted comments and then use them to build HTML based documentation. Before generating your application's documentation, you can add Javadoc comments before class and interface and other type declarations before field declarations and before methods.
