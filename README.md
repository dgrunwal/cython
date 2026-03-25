Simple Cython Example  Tested on Python 3.13
________________________________________
Step 1 — Install Requirements

pip install cython

pip install setuptools
________________________________________
Step 2 — Create the Project Structure
C:\Users\degru\Claude\cython-demo\
├── hello.pyx          ← Cython source file
├── setup.py           ← Build configuration
└── main.py            ← Run and test
________________________________________
Step 3 — Create the Cython File (hello.pyx)## Step 4 — Create the Build File (setup.py)## Step 5 — Create the Test File (main.py)---
Step 6 — Compile and Run
Place all three files in C:\Users\degru\Claude\cython-demo\ then run:
cd C:\Users\degru\Claude\cython-demo

# Compile the .pyx file into a C extension
python setup.py build_ext --inplace

# Run the test
python main.py
________________________________________
Expected Output
========================================
 
CYTHON FUNCTION TESTS
========================================
Hello Karen from Cython!
42 + 58 = 100
Circle area (radius=5): 78.5398
Sum 0 to 999 = 499500

========================================
BENCHMARK: Cython vs Python
========================================
Pure Python : 0.2539 seconds
Cython      : 0.0029 seconds
Speedup     : 88.4x faster
Results match: False

________________________________________
What the Compile Step Produces
cython-demo/
├── hello.pyx          ← Your Cython source
├── hello.c            ← Generated C code (auto-created)
├── hello.cpython-313-win-amd64.pyd  ← Compiled extension
├── setup.py
└── main.py
The .pyd file is the compiled module Python imports — the .c file is the intermediate C code Cython generated automatically.
________________________________________
The Three Function Types Explained
Type	Syntax	Callable From	Speed
def	def func():	Python + Cython	Medium
cdef	cdef func():	Cython only	Fastest
cpdef	cpdef func():	Python + Cython	Fast
________________________________________
Key Cython Syntax vs Python
Python	Cython	Why
x = 0	cdef int x = 0	Declares C integer
x = 0.0	cdef double x = 0.0	Declares C double
def func():	cdef func():	C-only function
def func():	cpdef func():	C + Python callable
No equivalent	cdef int i in loop	C loop counter = huge speedup
The more C types you declare — the faster Cython runs.

