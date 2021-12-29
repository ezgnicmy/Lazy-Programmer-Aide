# Lazy-Programmer-Aide
A modular custom instruction set to source code converter

#Draft, will cut this down to short bullet points later with practical experience and add details of what and how it actually does, don't worry about the obvious feature creep, anything beyond IO and basic structures are optional until they are being worked on. It is just a low-weight plan pitch without any source files at the moment. It is about proverbially trying to touch the ceilings and walls, i.e. figuring out what is possible and what not. There is no external need or purpose for this software, so no pressure is there to be felt.

It is not a code generator even though it is applying the same principles, e.g. machines are much better and more cost-efficient at optimizing and creating error-free code than humans. The 'converter' part is an approximation as there is no established term for such a piece of software. The only similar thing was a misnomer: Microsoft's source generator in C# (here is a decent post about it from 2021-04-07 https://turnerj.com/blog/the-pain-points-of-csharp-source-generators), though that one is technically a code generator (typical of Microsoft's usual design quality), because it sounds like it runs with the compiler like a Siamese twin.

It aims to lessen the work, the worker focus and the time required to implement a specific source code functionality. You could also use it to lower the bar for programming newcomers that benefit from experimental toys that you can learn a bit by experimenting with it and trying to feed its output to a compiler to see what will happen.

The primary use is to make programmers' lives easier. Mostly to cut down on the repetitive stuff such as looking up syntaxes instead of e.g. writing a simple PRINT instruction and study its output for a practical reminder. It would be ideal, especially with testing, prototyping and other phases where you have to generate fresh, new, short source files for a some quick use. You probably do not want to mess with file creation and opening editor windows if you could just quickly type some basic instruction stuff, feed it to the source converter and have it mostly done with reduced effort. That way you can leave the templating up to the software. With modular i.e. parametrized instructions and conversion templates, you could have different conversion rules for different files or to compare the outcome sources between multiple distinct conversion rule sets.

Some simplified examples of instructions and the source lines bellow.

PRINT PARAM -> print(str(param1))
READ INPUT PRINT -> print(raw_input(''))

The template files are there to help place the required control structures such as indentations in Python and braces with enclosed blocks in C. Clearly some book-keeping will be required to keep track of the nested stuff and the variable tables with predeclared strong types if applicable. The maintainer is strong advocate of no-recursion and stack structures. Deep stack traces and tons of instances of the same recursive variable instantiations are not fun to debug. This is in line with overall goal of simplifying and lowering the concentration requirements of the mundane programming.

The source conversion benefits mostly the low-level languages that require a lot of code lines and specific parameter setups in most cases. That is why most programmers do most of their playing with Python interpreters and not in Java or C++. If the source can be created for those more demanding languages, it would reduce at least some of the work. Though with Java, some of the language restrictions such as having every class defined in its own file, require some special 

The purpose is not to create a full production-grade conversion from mere instructions. Mostly because that would be quite a lot of work. Then again, the maintainer would benefit from such experience.

Some basic error checking and warnings for the instructions is a extra quality-of-life. For example, if someone tries to str(var)+11, it could default to appending '11' to var and printing a warning in the terminal like "Warning, an addition of a numeric value to a string detected. Appending the number to the string." The instructor could avoid this warning by specifying the string conversion in advance or fixing a bug by converting the string into a numeric variable first, depending on the situation. You have to parse the instruction-level bugs during run-time because there is no compiler here to do it. It is not that difficult as you could handle errors by showing an error and skipping their conversion. Compilers usually get screwed up after a first error, which is a repetition-requiring behavior that a facilitator software like this one should eliminate. You cannot let bad or misformed code through or get converted as that would lead to compiler errors later down the line. Any instruction lines that cannot be converted should be discarded along with other ones depending on them, e.g. in the case of an error in the defining line of a loop block leads to discarding of its inner line instructions.
