# HPSC Lab 7
2019-10-11

Click to [make your own repo](TO DO).

The goals for this lab are:
* Use a node of Summit.
* Gain exposure to the interface of a parallel dense linear algebra library.
* Measure scaling properties of said library.

-----

The lectures have mentioned the [Elemental](https://github.com/elemental/Elemental) library, which was created by Jack Poulson for parallel dense linear algebra.  Elemental itself is no longer maintained, but hopefully this exposure will at least give you a sense of one reasonable way that an HPC library can be interfaced in case you ever find yourself building one.

### Accessing Elemental

Camden's attempts to install Elemental on CSEL were only 99% successful.  Luckily, Jed has a pre-installed version for us to use on Summit.  Hopefully you've already requested an account and set up Duo two-factor authentication.  One you are in, remember to switch to a compile node.  **Remember:** compile nodes say **no heavy computation**.
```ssh [identikey]@login.rc.colorado.edu
ssh scompile```

Load appropriate environmental variables:
```source /projects/jeka2967/profile.bash
export EASYCODE=/projects/jeka2967/src/Elemental/examples/lapack_like/
export EASYEXEC=export EASYEXEC=/projects/jeka2967/src/Elemental/ompi-gcc8/bin/examples/lapack_like```

Run (something small) on a compile node:
```mpiexec -n 2 $EASYEXEC/LinearSolve --size 1024```

Peek at the code at `$EASYCODE/LinearSolve.cpp`.  In this code, you "Perform the LU factorization and simultaneous solve."

-----

Let's do some profiling as we change the matrix size and number of processes.  Keep in mind that Summit has 20 processing units per node.

How does this compare to the lecture code?

-----

Looking for more to do?  Check out some of the other examples codes that relate to problems with which you are familiar!