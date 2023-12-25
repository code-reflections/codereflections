+++
title = "Bootstrapping Perl without a compiler."
date = 2023-12-24
slug = "bootstrapping-perl-without-a-compiler"
path = "/2023/12/24/bootstrapping-perl-without-a-compiler/"

[taxonomies]
categories = ["Story"]
tags = ["Perl", "GCC", "cross-compiling"]
+++

Back in March of 1991, I started a new job as a software developer for a very
small company.  From day one, I knew that Perl was an essential tool which I
needed for the job.  However, I needed Perl to run on an [Altos
Unix](https://en.wikipedia.org/wiki/Altos_Computer_Systems) system which was
missing the C compiler, so this was easier said than done!  It turned out to be
an interesting bootstrapping challenge to solve using free software, though it
did require jumping through a few hoops.

<!-- more -->

Of course, there **was** a standard system C compiler for Altos Unix, but it
was not included with the base operating system and had to be purchased as a
rather expensive add-on feature.  If I remember correctly, the price was
something like $3,000!  (Keep in mind that Linux didn't even **exist** yet.)
My new boss didn't want to incur that cost, so I had to try to bootstrap Perl
from scratch using only free software.

More to the point, I needed to bootstrap GCC to replace the missing system C
compiler.  Once that was done, compiling Perl would be straightforward.  (At
that time, Perl was at version 3.044, and GCC was at version 1.39.)

As it turned out, even though there was no C compiler on the Altos Unix system,
other essential runtime components **were** included with the base system.
There was a linker, an assembler, a system C library, system C include files,
and the [crt0.o](https://en.wikipedia.org/wiki/Crt0) C runtime startup object
file.

Luckily, I had access to a Digital Unix system (with a C compiler) that I could
use for this.  On that system, I started with the normal GCC bootstrapping
procedure to build a native GCC for Digital Unix:

* First, I compiled GCC using the Digital Unix system C compiler, creating a
  native GCC binary compiled by the system C compiler.  This is a "stage 1"
  build of GCC.

* Next, I used that stage 1 GCC binary to compile GCC again from scratch,
  creating a fully-optimized native GCC binary compiled by GCC itself.  This is
  a "stage 2" build of GCC.

* Finally, I used the stage 2 GCC binary to compile GCC again from scratch.
  This is a "stage 3" build of GCC, which should be identical to the "stage 2"
  build.  This build is compared with the stage 2 build to validate that the
  GCC compiler is working correctly.

Once I had a native GCC build for Digital Unix, I then reconfigured the GCC
build process to build a cross-compiler, to run on Digital Unix (using VAX
hardware) while generating code for the Altos Unix system (using 80386
hardware).  This is a strange configuration, to say the least.

I ran through the GCC build for this cross-compiler, creating a native GCC
binary for Digital Unix, compiled by the native GCC build, generating 80386
code that couldn't run on the Digital Unix system.  Of course, since this was a
cross-compiler, there was no 3-stage build process here.

Next, I reconfigured the GCC build process yet again.  This time, I configured
it as a native compiler for the Altos Unix system, using the Altos Unix system
C include files that I had transferred to the Digital Unix system.  Of course,
was impossible to fully build this configuration on the Digital Unix system
because the native Digital Unix assembler couldn't create native Altos Unix
object files, and the native Digital Unix linker couldn't create a native Altos
Unix binary.

However, I could still use the Digital Unix binary of the GCC cross-compiler
configuration to perform the key step of compiling each of GCC's C source code
files, which I couldn't do on the Altos Unix system itself because of the
missing C compiler.  Since the Digital Unix assembler couldn't create native
Altos Unix object files, I had to compile each of the C source code files into
`*.s` assembly-language files instead of `*.o` object files.

At this point, I transferred all the files from the Digital Unix system to the
Altos Unix system, and used the native Altos Unix `as` assembler to assemble
each of the `*.s` assembly-language files (compiled from GCC's C source code
files) into native Altos Unix `*.o` object files.  I was then able to use the
native Altos Unix `ld` linker to link the native Altos Unix `crt0.o` C runtime
startup code with all of the `*.o` object files for the GCC compiler and the
`libc.a` system C library, finally creating a native Altos Unix binary of the
GCC compiler, configured as a native compiler for the Altos Unix system.

Once I had this native binary on the Altos Unix system, I pretended that it was
the system C compiler and used it to perform a full 3-stage GCC build from
scratch, installing the final GCC binary on the Altos Unix system as
`/usr/local/bin/gcc`.  Now I had a fully-bootstrapped native GCC compiler for
the Altos Unix system, despite the lack of a system C compiler to start the
process.

From that point forward, it was like working with any other Unix system.  After
building the GNU assembler and linker, I compiled Perl 3.044 and other GNU
software of interest.  Then I was finally able to start writing Perl code for
my new job!
