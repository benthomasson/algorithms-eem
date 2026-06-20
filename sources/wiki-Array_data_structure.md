---
source: https://en.wikipedia.org/wiki/Array_(data_structure)
fetched: 2026-06-19
---

Type of data structure This article is about the byte-layout-level structure. For the abstract data type, see [Array (data type)](./Array_(data_type)). 

 
|  | This articleneeds additional citations forverification.Please helpimprove this articlebyadding citations to reliable sources. Unsourced material may be challenged and removed.Find sources:"Array"data structure–news·newspapers·books·scholar·JSTOR(September 2008)(Learn how and when to remove this message) |
| --- | --- |

 

In [computer science](./Computer_science), an **array** is a [data structure](./Data_structure) consisting of a collection of *elements* ([values](./Value_(computer_science)) or [variables](./Variable_(programming))), of the same memory size, each identified by at least one *array index* or *key*, the collection of which may be a [tuple](./Tuple), known as an index tuple. In general, an array is a mutable and linear collection of elements with the same data type. An array is stored such that the position (memory address) of each element can be computed from its index tuple by a mathematical formula.[[1]](./Array_(data_structure)#cite_note-1)[[2]](./Array_(data_structure)#cite_note-andres-2)[[3]](./Array_(data_structure)#cite_note-garcia-3) The simplest type of data structure is a linear array, also called a one-dimensional array.

 

For example, an array of ten [32-bit](./32-bit) (4-byte) integer variables, with indices 0 through 9, may be stored as ten [words](./Word_(data_type)) at memory addresses 2000, 2004, 2008, ..., 2036, (in [hexadecimal](./Hexadecimal): `0x7D0`, `0x7D4`, `0x7D8`, ..., `0x7F4`) so that the element with index *i* has the address 2000 + (*i* × 4).[[4]](./Array_(data_structure)#cite_note-4)
The memory address of the first element of an array is called first address, foundation address, or base address.

 

Because the mathematical concept of a [matrix](./Matrix_(mathematics)) can be represented as a two-dimensional grid, two-dimensional arrays are also sometimes called "matrices". In some cases the term "vector" is used in computing to refer to an array, although [tuples](./Tuple) rather than [vectors](./Vector_space) are the more mathematically correct equivalent. [Tables](./Table_(information)) are often implemented in the form of arrays, especially [lookup tables](./Lookup_table); the word "table" is sometimes used as a synonym of array.

 

Arrays are among the oldest and most important data structures, and are used by almost every program. They are also used to implement many other data structures, such as [lists](./List_(computing)) and [strings](./String_(computer_science)). They effectively exploit the addressing logic of computers. In most modern computers and many [external storage](./External_storage) devices, the memory is a one-dimensional array of words, whose indices are their addresses. [Processors](./Central_processing_unit), especially [vector processors](./Vector_processor), are often optimized for array operations.

 

Arrays are useful mostly because the element indices can be computed at [run time](./Run_time_(program_lifecycle_phase)). Among other things, this feature allows a single iterative [statement](./Statement_(programming)) to process arbitrarily many elements of an array. For that reason, the elements of an array data structure are required to have the same size and should use the same data representation. The set of valid index tuples and the addresses of the elements (and hence the element addressing formula) are usually,[[3]](./Array_(data_structure)#cite_note-garcia-3)[[5]](./Array_(data_structure)#cite_note-veldhuizen-5) but not always,[[2]](./Array_(data_structure)#cite_note-andres-2) fixed while the array is in use.

 

The term "array" may also refer to an [array data type](./Array_data_type), a kind of [data type](./Data_type) provided by most [high-level programming languages](./High-level_programming_language) that consists of a collection of values or variables that can be selected by one or more indices computed at run-time. Array types are often implemented by array structures; however, in some languages they may be implemented by [hash tables](./Hash_table), [linked lists](./Linked_list), [search trees](./Search_tree), or other data structures.

 

The term is also used, especially in the description of [algorithms](./Algorithm), to mean [associative array](./Associative_array) or "abstract array", a [theoretical computer science](./Theoretical_computer_science) model (an [abstract data type](./Abstract_data_type) or ADT) intended to capture the essential properties of arrays.

 

## History

 

The first digital computers used machine-language programming to set up and access array structures for data tables, vector and matrix computations, and for many other purposes. [John von Neumann](./John_von_Neumann) wrote the first array-sorting program ([merge sort](./Merge_sort)) in 1945, during the building of the [first stored-program computer](./EDVAC).[[6]](./Array_(data_structure)#cite_note-6) Array indexing was originally done by [self-modifying code](./Self-modifying_code), and later using [index registers](./Index_register) and [indirect addressing](./Addressing_mode). Some mainframes designed in the 1960s, such as the [Burroughs B5000](./Burroughs_Large_Systems) and its successors, used [memory segmentation](./Memory_segmentation) to perform index-bounds checking in hardware.[[7]](./Array_(data_structure)#cite_note-7)

 

Assembly languages generally have no special support for arrays, other than what the machine itself provides. The earliest high-level programming languages, including [FORTRAN](./Fortran) (1957), [Lisp](./Lisp_(programming_language)) (1958), [COBOL](./COBOL) (1960), and [ALGOL 60](./ALGOL) (1960), had support for multi-dimensional arrays, and so has [C](./C_(programming_language)) (1972). In [C++](./C++) (1983), class templates exist for multi-dimensional arrays whose dimension is fixed at runtime[[3]](./Array_(data_structure)#cite_note-garcia-3)[[5]](./Array_(data_structure)#cite_note-veldhuizen-5) as well as for runtime-flexible arrays.[[2]](./Array_(data_structure)#cite_note-andres-2)

 

## Applications

 

Arrays are used to implement mathematical [vectors](./Coordinate_vector) and [matrices](./Matrix_(mathematics)), as well as other kinds of rectangular tables. Many [databases](./Database), small and large, consist of (or include) one-dimensional arrays whose elements are [records](./Record_(computer_science)).

 

Arrays are used to implement other data structures, such as lists, [heaps](./Heap_(data_structure)), [hash tables](./Hash_table), [deques](./Double-ended_queue), [queues](./Queue_(abstract_data_type)), [stacks](./Stack_(data_structure)), [strings](./String_(computer_science)), and VLists. Array-based implementations of other data structures are frequently simple and space-efficient ([implicit data structures](./Implicit_data_structure)), requiring little space [overhead](./Overhead_(computing)), but may have poor space complexity, particularly when modified, compared to tree-based data structures (compare a [sorted array](./Sorted_array) to a [search tree](./Search_tree)).

 

One or more large arrays are sometimes used to emulate in-program [dynamic memory allocation](./Dynamic_memory_allocation), particularly [memory pool](./Memory_pool) allocation. Historically, this has sometimes been the only way to allocate "dynamic memory" portably.

 

Arrays can be used to determine partial or complete [control flow](./Control_flow) in programs, as a compact alternative to (otherwise repetitive) multiple `IF` statements. In this context, they are known as [control tables](./Control_table) and are used in conjunction with a purpose-built interpreter whose [control flow](./Control_flow) is altered according to values contained in the array. The array may contain [subroutine](./Subroutine) [pointers](./Pointer_(computer_programming)) (or relative subroutine numbers that can be acted upon by [SWITCH](./Switch_statement) statements) that direct the path of the execution of the program.

 

## Element identifier and addressing formulas

 

When data objects are stored in an array, individual objects are selected by an index that is usually a non-negative [scalar](./Scalar_(computing)) [integer](./Integer). Indexes are also called subscripts. An index *maps* the array value to a stored object.

 

There are three ways in which the elements of an array can be indexed:

 0 (*[zero-based indexing](./Zero-based_numbering)*)The first element of the array is indexed by subscript of 0.[[8]](./Array_(data_structure)#cite_note-8) 1 (*one-based indexing*)The first element of the array is indexed by subscript of 1. n (*n-based indexing*)The base index of an array can be freely chosen. Usually programming languages allowing *n-based indexing* also allow negative index values and other [scalar](./Scalar_(computing)) data types like [enumerations](./Enumerated_type), or [characters](./Character_(computing)) may be used as an array index. 

Using zero based indexing is the design choice of many influential programming languages, including [C](./C_(programming_language)), [Java](./Java_(programming_language)) and [Lisp](./Lisp_(programming_language)). This leads to simpler implementation where the subscript refers to an offset from the starting position of an array, so the first element has an offset of zero.

 

Arrays can have multiple dimensions, thus it is not uncommon to access an array using multiple indices. For example, a two-dimensional array `A` with three rows and four columns might provide access to the element at the 2nd row and 4th column by the expression `A[1][3]` in the case of a zero-based indexing system. Thus two indices are used for a two-dimensional array, three for a three-dimensional array, and *n* for an *n*-dimensional array.

 

The number of indices needed to specify an element is called the dimension, dimensionality, or [rank](./Rank_(computer_programming)) of the array.

 

In standard arrays, each index is restricted to a certain range of consecutive integers (or consecutive values of some [enumerated type](./Enumerated_type)), and the address of an element is computed by a "linear" formula on the indices.

 

### One-dimensional arrays

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/4/40/1D_array_diagram.svg/250px-1D_array_diagram.svg.png)](./File:1D_array_diagram.svg)Diagram of a typical 1D array 

A one-dimensional array (or single dimension array) is a type of linear array. Accessing its elements involves a single subscript which can either represent a row or column index.

 

As an example consider the C declaration `int a[10];` which declares a one-dimensional array named `a` of ten integers. Here, the array can store ten elements of type `int` . This array has indices starting from zero through nine. For example, the expressions `a[0]` and `a[9]` are the first and last elements respectively.

 

For a vector with linear addressing, the element with index *i* is located at the address *B* + *c* · *i*, where *B* is a fixed *base address* and *c* a fixed constant, sometimes called the *address increment* or *stride*.

 

If the valid element indices begin at 0, the constant *B* is simply the address of the first element of the array. For this reason, the [C programming language](./C_(programming_language)) specifies that array indices always begin at 0; and many programmers will call that element "[zeroth](./Zero-based_numbering)" rather than "first".

 

However, one can choose the index of the first element by an appropriate choice of the base address *B*. For example, if the array has five elements, indexed 1 through 5, and the base address *B* is replaced by *B* + 30*c*, then the indices of those same elements will be 31 to 35. If the numbering does not start at 0, the constant *B* may not be the address of any element.

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/f/f3/2D_array_diagram.svg/250px-2D_array_diagram.svg.png)](./File:2D_array_diagram.svg)Diagram of a typical 2D array 

### Multidimensional arrays

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/9/97/3D_array_diagram.svg/250px-3D_array_diagram.svg.png)](./File:3D_array_diagram.svg)Diagram of a typical 3D array 

For a multidimensional array, the element with indices *i*,*j* would have address *B* + *c* · *i* + *d* · *j*, where the coefficients *c* and *d* are the *row* and *column address increments*, respectively.

 

More generally, in a *k*-dimensional array, the address of an element with indices *i*1, *i*2, ..., *i**k* is

 *B* + *c*1 · *i*1 + *c*2 · *i*2 + … + *c**k* · *i**k*. 

For example: int a[2][3];

 

This means that array a has 2 rows and 3 columns, and the array is of integer type. Here we can store 6 elements they will be stored linearly but starting from first row linear then continuing with second row. The above array will be stored as a11, a12, a13, a21, a22, a23.

 

This formula requires only *k* multiplications and *k* additions, for any array that can fit in memory. Moreover, if any coefficient is a fixed power of 2, the multiplication can be replaced by [bit shifting](./Bitwise_operation).

 

The coefficients *c**k* must be chosen so that every valid index tuple maps to the address of a distinct element.

 

If the minimum legal value for every index is 0, then *B* is the address of the element whose indices are all zero. As in the one-dimensional case, the element indices may be changed by changing the base address *B*. Thus, if a two-dimensional array has rows and columns indexed from 1 to 10 and 1 to 20, respectively, then replacing *B* by *B* + *c*1 − 3*c*2 will cause them to be renumbered from 0 through 9 and 4 through 23, respectively. Taking advantage of this feature, some languages (like FORTRAN 77) specify that array indices begin at 1, as in mathematical tradition while other languages (like Fortran 90, Pascal and Algol) let the user choose the minimum value for each index.

 

### Dope vectors

 Main article: [Dope vector](./Dope_vector) 

The addressing formula is completely defined by the dimension *d*, the base address *B*, and the increments *c*1, *c*2, ..., *c**k*. It is often useful to pack these parameters into a record called the array's descriptor, stride vector, or [dope vector](./Dope_vector).[[2]](./Array_(data_structure)#cite_note-andres-2)[[3]](./Array_(data_structure)#cite_note-garcia-3) The size of each element, and the minimum and maximum values allowed for each index may also be included in the dope vector. The dope vector is a complete [handle](./Handle_(computing)) for the array, and is a convenient way to pass arrays as arguments to [procedures](./Subroutine). Many useful [array slicing](./Array_slicing) operations (such as selecting a sub-array, swapping indices, or reversing the direction of the indices) can be performed very efficiently by manipulating the dope vector.[[2]](./Array_(data_structure)#cite_note-andres-2)

 

### Compact layouts

 Main article: [Row- and column-major order](./Row-_and_column-major_order) 

Often the coefficients are chosen so that the elements occupy a contiguous area of memory. However, that is not necessary. Even if arrays are always created with contiguous elements, some array slicing operations may create non-contiguous sub-arrays from them.

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/4/4d/Row_and_column_major_order.svg/250px-Row_and_column_major_order.svg.png)](./File:Row_and_column_major_order.svg)Illustration of row- and column-major order 

There are two systematic compact layouts for a two-dimensional array. For example, consider the matrix

     A =   [    1   2   3     4   5   6     7   8   9    ]   .   {\displaystyle A={\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}}.}  ![{\displaystyle A={\begin{bmatrix}1&2&3\\4&5&6\\7&8&9\end{bmatrix}}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/e5ce1bbaec43174abf6887a29b8f3a3612d0b1f5) 

In the row-major order layout (adopted by C for statically declared arrays), the elements in each row are stored in consecutive positions and all of the elements of a row have a lower address than any of the elements of a consecutive row:

 
| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |

 

In column-major order (traditionally used by Fortran), the elements in each column are consecutive in memory and all of the elements of a column have a lower address than any of the elements of a consecutive column:

 
| 1 | 4 | 7 | 2 | 5 | 8 | 3 | 6 | 9 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |

 

For arrays with three or more indices, "row major order" puts in consecutive positions any two elements whose index tuples differ only by one in the *last* index. "Column major order" is analogous with respect to the *first* index.

 

In systems which use [processor cache](./Processor_cache) or [virtual memory](./Virtual_memory), scanning an array is much faster if successive elements are stored in consecutive positions in memory, rather than sparsely scattered. This is known as spatial locality, which is a type of [locality of reference](./Locality_of_reference). Many algorithms that use multidimensional arrays will scan them in a predictable order. A programmer (or a sophisticated compiler) may use this information to choose between row- or column-major layout for each array. For example, when computing the product *A*·*B* of two matrices, it would be best to have *A* stored in row-major order, and *B* in column-major order.

 

### Resizing

 Main article: [Dynamic array](./Dynamic_array) 

Static arrays have a size that is fixed when they are created and consequently do not allow elements to be inserted or removed. However, by allocating a new array and copying the contents of the old array to it, it is possible to effectively implement a *dynamic* version of an array; see [dynamic array](./Dynamic_array). If this operation is done infrequently, insertions at the end of the array require only amortized constant time.

 

Some array data structures do not reallocate storage, but do store a count of the number of elements of the array in use, called the count or size. This effectively makes the array a [dynamic array](./Dynamic_array) with a fixed maximum size or capacity; [Pascal strings](./Pascal_string) are examples of this.

 

### Non-linear formulas

 

More complicated (non-linear) formulas are occasionally used. For a compact two-dimensional [triangular array](./Triangular_array), for instance, the addressing formula is a polynomial of degree 2.

 

## Efficiency

 

Both *store* and *select* take (deterministic worst case) [constant time](./Constant_time). Arrays take linear ([O](./Big-O_notation)(*n*)) space in the number of elements *n* that they hold.

 

In an array with element size *k* and on a machine with a cache line size of B bytes, iterating through an array of *n* elements requires the minimum of ceiling(*nk*/B) cache misses, because its elements occupy contiguous memory locations. This is roughly a factor of B/*k* better than the number of cache misses needed to access *n* elements at random memory locations. As a consequence, sequential iteration over an array is noticeably faster in practice than iteration over many other data structures, a property called [locality of reference](./Locality_of_reference) (this does *not* mean however, that using a [perfect hash](./Perfect_hash_function) or [trivial hash](./Hash_function#Trivial_hash_function) within the same (local) array, will not be even faster - and achievable in [constant time](./Constant_time)). Libraries provide low-level optimized facilities for copying ranges of memory (such as [memcpy](./String.h)) which can be used to move [contiguous](./Contiguous_data_storage) blocks of array elements significantly faster than can be achieved through individual element access. The speedup of such optimized routines varies by array element size, architecture, and implementation.

 

Memory-wise, arrays are compact data structures with no per-element [overhead](./Computational_overhead). There may be a per-array overhead (e.g., to store index bounds) but this is language-dependent. It can also happen that elements stored in an array require *less* memory than the same elements stored in individual variables, because several array elements can be stored in a single [word](./Word_(data_type)); such arrays are often called *packed* arrays. An extreme (but commonly used) case is the [bit array](./Bit_array), where every bit represents a single element. A single [octet](./Octet_(computing)) can thus hold up to 256 different combinations of up to 8 different conditions, in the most compact form.

 

Array accesses with statically predictable access patterns are a major source of [data parallelism](./Data_parallelism).

 

### Comparison with other data structures

 
|  | Peek(index) | Mutate (insert or delete) at … | Excess space,average |
| --- | --- | --- | --- |
| Beginning | End | Middle |
| Linked list | Θ(n) | Θ(1) | Θ(1), known end element;Θ(n), unknown end element | Θ(n) | Θ(n) |
| Array | Θ(1) | —N/a | —N/a | —N/a | 0 |
| Dynamic array | Θ(1) | Θ(n) | Θ(1)amortized | Θ(n) | Θ(n)[9] |
| Balanced tree | Θ(log n) | Θ(log n) | Θ(logn) | Θ(logn) | Θ(n) |
| Random-access list | Θ(log n)[10] | Θ(1) | —N/a[10] | —N/a[10] | Θ(n) |
| Hashed array tree | Θ(1) | Θ(n) | Θ(1)amortized | Θ(n) | Θ(√n) |

 

[Dynamic arrays](./Dynamic_array) or growable arrays are similar to arrays but add the ability to insert and delete elements; adding and deleting at the end is particularly efficient. However, they reserve linear ([Θ](./Big-O_notation#Family_of_Bachmann–Landau_notations)(*n*)) additional storage, whereas arrays do not reserve additional storage.

 

[Associative arrays](./Associative_array) provide a mechanism for array-like functionality without huge storage overheads when the index values are sparse. For example, an array that contains values only at indexes 1 and 2 billion may benefit from using such a structure. Specialized associative arrays with integer keys include [Patricia tries](./Radix_tree), [Judy arrays](./Judy_array), and [van Emde Boas trees](./Van_Emde_Boas_tree).

 

[Balanced trees](./Self-balancing_binary_search_tree) require O(log *n*) time for indexed access, but also permit inserting or deleting elements in O(log *n*) time,[[11]](./Array_(data_structure)#cite_note-11) whereas growable arrays require linear (Θ(*n*)) time to insert or delete elements at an arbitrary position.

 

[Linked lists](./Linked_list) allow constant time removal and insertion in the middle but take linear time for indexed access. Their memory use is typically worse than arrays, but is still linear.

 [![A two-dimensional array stored as a one-dimensional array of one-dimensional arrays (rows).](//upload.wikimedia.org/wikipedia/commons/thumb/0/01/Array_of_array_storage.svg/120px-Array_of_array_storage.svg.png)](./File:Array_of_array_storage.svg)A two-dimensional array stored as a one-dimensional array of one-dimensional arrays (rows). 

An [Iliffe vector](./Iliffe_vector) is an alternative to a multidimensional array structure. It uses a one-dimensional array of [references](./Reference_(computer_science)) to arrays of one dimension less. For two dimensions, in particular, this alternative structure would be a vector of pointers to vectors, one for each row(pointer on c or c++). Thus an element in row *i* and column *j* of an array *A* would be accessed by double indexing (*A*[*i*][*j*] in typical notation). This alternative structure allows [jagged arrays](./Jagged_array), where each row may have a different size—or, in general, where the valid range of each index depends on the values of all preceding indices. It also saves one multiplication (by the column address increment) replacing it by a bit shift (to index the vector of row pointers) and one extra memory access (fetching the row address), which may be worthwhile in some architectures.

 

## Dimension

 

The *dimension* of an array is the number of indices needed to select an element. Thus, if the array is seen as a function on a set of possible index combinations, it is the dimension of the space of which its domain is a discrete subset. Thus a one-dimensional array is a list of data, a two-dimensional array is a rectangle of data,[[12]](./Array_(data_structure)#cite_note-12) a three-dimensional array a block of data, etc.

 

This should not be confused with the dimension of the set of all matrices with a given domain, that is, the number of elements in the array. For example, an array with 5 rows and 4 columns is two-dimensional, but such matrices form a 20-dimensional space. Similarly, a three-dimensional vector can be represented by a one-dimensional array of size three.

 

## See also

 
- [![icon](//upload.wikimedia.org/wikipedia/commons/thumb/6/6f/Octicons-terminal.svg/40px-Octicons-terminal.svg.png)](./File:Octicons-terminal.svg)[Computer programming portal](./Portal:Computer_programming)

  
- [Dynamic array](./Dynamic_array)
- [Parallel array](./Parallel_array)
- [Variable-length array](./Variable-length_array)
- [Bit array](./Bit_array)
- [Array slicing](./Array_slicing)
- [Offset (computer science)](./Offset_(computer_science))
- [Row- and column-major order](./Row-_and_column-major_order)
- [Stride of an array](./Stride_of_an_array)

  

## References

  
1. [↑](./Array_(data_structure)#cite_ref-1) Black, Paul E. (13 November 2008). ["array"](https://xlinux.nist.gov/dads/HTML/array.html). *[Dictionary of Algorithms and Data Structures](./Dictionary_of_Algorithms_and_Data_Structures?action=edit&redlink=1)*. [National Institute of Standards and Technology](./National_Institute_of_Standards_and_Technology). Retrieved 22 August 2010.
2. [1](./Array_(data_structure)#cite_ref-andres_2-0) [2](./Array_(data_structure)#cite_ref-andres_2-1) [3](./Array_(data_structure)#cite_ref-andres_2-2) [4](./Array_(data_structure)#cite_ref-andres_2-3) [5](./Array_(data_structure)#cite_ref-andres_2-4) Bjoern Andres; Ullrich Koethe; Thorben Kroeger; Hamprecht (2010). "Runtime-Flexible Multi-dimensional Arrays and Views for C++98 and C++0x". [arXiv](./ArXiv_(identifier)):[1008.2909](https://arxiv.org/abs/1008.2909) [[cs.DS](https://arxiv.org/archive/cs.DS)].
3. [1](./Array_(data_structure)#cite_ref-garcia_3-0) [2](./Array_(data_structure)#cite_ref-garcia_3-1) [3](./Array_(data_structure)#cite_ref-garcia_3-2) [4](./Array_(data_structure)#cite_ref-garcia_3-3) Garcia, Ronald; Lumsdaine, Andrew (2005). "MultiArray: a C++ library for generic programming with arrays". *Software: Practice and Experience*. **35** (2): 159–188. [doi](./Doi_(identifier)):[10.1002/spe.630](https://doi.org/10.1002%2Fspe.630). [ISSN](./ISSN_(identifier)) [0038-0644](https://search.worldcat.org/issn/0038-0644). [S2CID](./S2CID_(identifier)) [10890293](https://api.semanticscholar.org/CorpusID:10890293).
4. [↑](./Array_(data_structure)#cite_ref-4) David R. Richardson (2002), The Book on Data Structures. iUniverse, 1112 pages. [ISBN](./ISBN_(identifier)) [0-595-24039-9](./Special:BookSources/0-595-24039-9), [ISBN](./ISBN_(identifier)) [978-0-595-24039-5](./Special:BookSources/978-0-595-24039-5).
5. [1](./Array_(data_structure)#cite_ref-veldhuizen_5-0) [2](./Array_(data_structure)#cite_ref-veldhuizen_5-1) Veldhuizen, Todd L. (December 1998). *Arrays in Blitz++*. Computing in Object-Oriented Parallel Environments. Lecture Notes in Computer Science. Vol. 1505. Berlin: Springer. pp. 223–230. [doi](./Doi_(identifier)):[10.1007/3-540-49372-7_24](https://doi.org/10.1007%2F3-540-49372-7_24). [ISBN](./ISBN_(identifier)) [978-3-540-65387-5](./Special:BookSources/978-3-540-65387-5).[*[dead link](./Wikipedia:Link_rot)*]
6. [↑](./Array_(data_structure)#cite_ref-6) [Knuth, Donald](./Donald_Knuth) (1998). *Sorting and Searching*. [The Art of Computer Programming](./The_Art_of_Computer_Programming). Vol. 3. Reading, MA: Addison-Wesley Professional. p. 159.
7. [↑](./Array_(data_structure)#cite_ref-7) Levy, Henry M. (1984), *Capability-based Computer Systems*, Digital Press, p. 22, [ISBN](./ISBN_(identifier)) [9780932376220](./Special:BookSources/9780932376220).
8. [↑](./Array_(data_structure)#cite_ref-8) ["Array Code Examples - PHP Array Functions - PHP code"](https://web.archive.org/web/20110413142103/http://www.configure-all.com/arrays.php). Computer Programming Web programming Tips. Archived from [the original](http://www.configure-all.com/arrays.php) on 13 April 2011. Retrieved 8 April 2011. In most computer languages array index (counting) starts from 0, not from 1. Index of the first element of the array is 0, index of the second element of the array is 1, and so on. In array of names below you can see indexes and values.
9. [↑](./Array_(data_structure)#cite_ref-9) Brodnik, Andrej; Carlsson, Svante; [Sedgewick, Robert](./Robert_Sedgewick_(computer_scientist)); Munro, JI; Demaine, ED (1999), [*Resizable Arrays in Optimal Time and Space (Technical Report CS-99-09)*](http://www.cs.uwaterloo.ca/research/tr/1999/09/CS-99-09.pdf) (PDF), Department of Computer Science, University of Waterloo
10. [1](./Array_(data_structure)#cite_ref-okasakiComparison_10-0) [2](./Array_(data_structure)#cite_ref-okasakiComparison_10-1) [3](./Array_(data_structure)#cite_ref-okasakiComparison_10-2) Chris Okasaki (1995). "Purely Functional Random-Access Lists". *Proceedings of the Seventh International Conference on Functional Programming Languages and Computer Architecture*: 86–95. [doi](./Doi_(identifier)):[10.1145/224164.224187](https://doi.org/10.1145%2F224164.224187).
11. [↑](./Array_(data_structure)#cite_ref-11) ["Counted B-Trees"](http://www.chiark.greenend.org.uk/~sgtatham/algorithms/cbtree.html).
12. [↑](./Array_(data_structure)#cite_ref-12) ["Two-Dimensional Arrays \ Processing.org"](https://processing.org/tutorials/2darray/). *processing.org*. Retrieved 1 May 2020.

 

## External links

   [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [Array data structure](https://commons.wikimedia.org/wiki/Category:Array%20data%20structure).    [![Wiktionary logo](//upload.wikimedia.org/wikipedia/commons/thumb/9/99/Wiktionary-logo-en-v2.svg/40px-Wiktionary-logo-en-v2.svg.png)](./File:Wiktionary-logo-en-v2.svg) Look up ***[array](https://en.wiktionary.org/wiki/array)*** in Wiktionary, the free dictionary.  
- [![Wikibooks logo](//upload.wikimedia.org/wikipedia/commons/thumb/f/fa/Wikibooks-logo.svg/20px-Wikibooks-logo.svg.png)](./File:Wikibooks-logo.svg) [Data Structures/Arrays](https://en.wikibooks.org/wiki/Data%20Structures/Arrays) at Wikibooks

  
| vteData structures |
| --- |
| Types | CollectionContainer |
| Abstract | Associative arrayMultimapRetrieval Data StructureListStackQueueDouble-ended queuePriority queueDouble-ended priority queueSetMultisetDisjoint-set |
| Arrays | Bit arrayCircular bufferDynamic arrayHash tableHashed array treeSparse matrix |
| Linked | Association listLinked listSkip listUnrolled linked listXOR linked list |
| Trees | B-treeBinary search treeAA treeAVL treeRed–black treeSelf-balancing treeSplay treeHeapBinary heapBinomial heapFibonacci heapR-treeR* treeR+ treeHilbert R-treeRopeTrieHash tree |
| Graphs | Binary decision diagramDirected acyclic graphDirected acyclic word graph |
| List of data structures |

 
| vteParallel computing |
| --- |
| General | Distributed computingParallel computingParallel algorithmMassively parallelCloud computingHigh-performance computingMultiprocessingManycore processorGPGPUComputer networkSystolic array |
| Levels | BitInstructionThreadTaskDataMemoryLoopPipeline |
| Multithreading | TemporalSimultaneous(SMT)Simultaneous and heterogenousSpeculative(SpMT)PreemptiveCooperativeClustered multi-thread(CMT)Hardware scout |
| Theory | PRAM modelPEM modelAnalysis of parallel algorithmsAmdahl's lawGustafson's lawCost efficiencyKarp–Flatt metricSlowdownSpeedup |
| Elements | ProcessThreadFiberInstruction windowArray |
| Coordination | MultiprocessingMemory coherenceCache coherenceCache invalidationBarrierSynchronizationApplication checkpointing |
| Programming | Stream processingDataflow programmingModelsImplicit parallelismExplicit parallelismConcurrencyNon-blocking algorithm |
| Hardware | Flynn's taxonomySISDSIMDArray processing(SIMT)Pipelined processingAssociative processingMISDMIMDDataflow architecturePipelined processorSuperscalar processorVector processorMultiprocessorsymmetricasymmetricMemoryshareddistributeddistributed sharedUMANUMACOMAMassively parallelcomputerComputer clusterBeowulf clusterGrid computerHardware acceleration |
| APIs | Ateji PXBoostChapelHPXCharm++CilkCoarray FortranCUDADryadC++ AMPGlobal ArraysGPUOpenMPIOpenMPOpenCLOpenHMPPOpenACCParallel ExtensionsPVMpthreadsRaftLibROCmUPCTBBZPL |
| Problems | Automatic parallelizationCache stampedeDeadlockDeterministic algorithmEmbarrassingly parallelParallel slowdownRace conditionSoftware lockoutScalabilityStarvation |
| Category: Parallel computing |

 
| Authority control databases | GND |
| --- | --- |