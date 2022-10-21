# typedarray.h
A C 'template' header file to create array types of any C type, including functionality for reading and manipulating of the array.

I typically use this code in the following fashion
(with a vector type used as an example):

1) Create a file vectorarray.h, with in it:

    #ifndef _VECTORARRAY_H_
    #define _VECTORARRAY_H_
    
    typedef struct {
      void* ptr;
      unsigned size;
    }
    vec_t;
    
    #include <typedarray.h>
    
    MAKE_ARRAY_HEADER(vec_t, vec_array_)
    
    #endif



2) Create a file vectorarray.c, with in it:

#include <vectorarray.h>

MAKE_ARRAY_CODE(vec_t, vec_array_)



3) Pull vectorarray.o into your Makefile.
