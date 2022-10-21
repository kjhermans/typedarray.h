# typedarray.h
A C 'template' header file to create array types of any C type, including functionality for reading and manipulating of the array.

I typically use this code in the following fashion
(with a vector type used as an example):

1) Create a file vectorarray.h, with in it:
```
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
```


2) Create a file vectorarray.c, with in it:
```
    #include <vectorarray.h>
    
    MAKE_ARRAY_CODE(vec_t, vec_array_)
```


3) Compile vectorarray.c into your project,
   and the following functions will be available:
```
    void     vec_array_init(vec_array_t* list);
    void     vec_array_free(vec_array_t* list);
    void     vec_array_push(vec_array_t* list, vec_t elt);
    vec_t    vec_array_get (vec_array_t* list, unsigned index, vec* elt);
    void     vec_array_set (vec_array_t* list, unsigned index, vec_t elt);
    vec_t    vec_array_rem (vec_array_t* list, unsigned index, vec* elt);
    void     vec_array_ins (vec_array_t* list, unsigned index, vec_t elt);
    vec_t    vec_array_pop (vec_array_t* list, vec* elt);
    vec_t    vec_array_peek(vec_array_t* list, vec* elt);
    unsigned vec_array_size(vec_array_t* list);
```
