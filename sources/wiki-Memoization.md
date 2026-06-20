---
source: https://en.wikipedia.org/wiki/Memoization
fetched: 2026-06-19
---

Software programming optimization technique Not to be confused with [Memorization](./Memorization). 

In [computing](./Computing), **memoization** or **memoisation** is an [optimization](./Optimization_(computer_science)) technique used primarily to speed up [computer programs](./Computer_programs). It works by storing the results of expensive [calls](./Subroutine) to [pure functions](./Pure_function), so that these results can be returned quickly should the same inputs occur again. It is a type of [caching](./Cache_(computing)), normally implemented using a [hash table](./Hash_table), and a typical example of a [space–time tradeoff](./Space–time_tradeoff), where the runtime of a program is reduced by increasing its memory usage. Memoization can be implemented in any programming language, though some languages have built-in support that make it easy for the programmer to memoize a function, and others memoize certain functions by default.

 

Memoization has also been used in other contexts (and for purposes other than speed gains), such as in simple [mutually recursive](./Mutual_recursion) descent parsing.[[1]](./Memoization#cite_note-Norvig1991-1) In the context of some [logic programming](./Logic_programming) languages, memoization is also known as [tabling](./Tabling).[[2]](./Memoization#cite_note-2)

 

## Etymology

 

The term *memoization* was coined by [Donald Michie](./Donald_Michie) in 1968[[3]](./Memoization#cite_note-Michie1968-3)[*[failed verification](./Wikipedia:Verifiability)*] and is derived from the [Latin](./Latin) word *[memorandum](./Memorandum)* ('to be remembered'), usually truncated as *memo* in American English, and thus carries the meaning of 'turning [the results of] a function into something to be remembered'. While *memoization* might be confused with *[memorization](./Memorization)* (because they are etymological [cognates](./Cognate)), *memoization* has a specialized meaning in computing.

 

## Overview

 

A memoized function, when called with a given set of inputs for the first time, stores the inputs along with the computed results. Upon subsequent calls with remembered inputs, the function returns the remembered results rather than recomputing them, thus eliminating the cost of a recomputation. The set of remembered associations may be a fixed-size set controlled by a replacement algorithm or a fixed set,[*[clarification needed](./Wikipedia:Please_clarify)*] depending on the nature of the function and its use.  A function can only be memoized if it is [referentially transparent](./Referential_transparency); that is, only if calling the function has exactly the same effect as replacing that function call with its return value. (Special case exceptions to this restriction exist, however.) While related to [lookup tables](./Lookup_table), since memoization often uses such tables in its implementation, memoization populates its cache of results transparently on the fly, rather than needing them to be supplied in advance.

 

Memoized functions are optimized for *speed* in exchange for a higher use of [computer memory](./Computer_memory) *space*. The time/space "cost" of [algorithms](./Algorithm) has a specific name in computing: *[computational complexity](./Computational_complexity_theory)*. All functions have a computational complexity in *time* (i.e. they take time to execute) and in *space*.

 

Although a [space–time tradeoff](./Space–time_tradeoff) occurs (i.e., space used is speed gained), this differs from some other optimizations that involve time-space trade-off, such as [strength reduction](./Strength_reduction), in that memoization is a [run-time](./Run_time_(program_lifecycle_phase)) rather than [compile-time](./Compile-time) optimization. Moreover, strength reduction potentially replaces a costly operation such as multiplication with a less costly operation such as addition, and the results in savings can be highly [machine-dependent](./Machine-dependent) (non-portable across machines), whereas memoization is a more machine-independent, [cross-platform](./Cross-platform) strategy.

 

Consider the following [pseudocode](./Pseudocode) function to calculate the [factorial](./Factorial) of *n*:

 
```
function factorial (n is a non-negative integer)
    if n is 0 then
        return 1 [by the convention that 0! = 1]
    else
        return factorial(n – 1) times n [recursively invoke factorial 
                                        with the parameter 1 less than n]
    end if
end function
```
 

For every [integer](./Integer) *n* such that `n ≥ 0`, the final result of the function `factorial` is [invariant](./Invariant_(computer_science)); if invoked as `x = factorial(3)`, the result is such that *x* will *always* be assigned the value 6. The non-memoized implementation above, given the nature of the [recursive](./Recursion) algorithm involved, would require *n + 1* invocations of `factorial` to arrive at a result, and each of these invocations, in turn, has an associated cost in the time it takes the function to return the value computed. Depending on the machine, this cost might be the sum of:

 
1. The cost to set up the functional call stack frame.
2. The cost to compare *n* to 0.
3. The cost to subtract 1 from *n*.
4. The cost to set up the recursive call stack frame. (As above.)
5. The cost to multiply the result of the recursive call to `factorial` by *n*.
6. The cost to store the return result so that it may be used by the calling context.

 

In a non-memoized implementation, *every* top-level call to `factorial` includes the cumulative cost of steps 2 through 6 proportional to the initial value of *n*.

 

A memoized version of the `factorial` function follows:

 
```
function factorial (n is a non-negative integer)
    if n is 0 then
        return 1 [by the convention that 0! = 1]
    else if n is in lookup-table then
        return lookup-table-value-for-n
    else
        let x = factorial(n – 1) times n [recursively invoke factorial
                                         with the parameter 1 less than n]
        store x in lookup-table in the nth slot [remember the result of n! for later]
        return x
    end if
end function
```
 

In this particular example, if `factorial` is first invoked with 5, and then invoked later with any value less than or equal to five, those return values will also have been memoized, since `factorial` will have been called recursively with the values 5, 4, 3, 2, 1, and 0, and the return values for *each* of those will have been stored. If it is then called with a number greater than 5, such as 7, only 2 recursive calls will be made (7 and 6), and the value for 5! will have been stored from the previous call. In this way, memoization allows a function to become more time-efficient the more often it is called, thus resulting in eventual overall speed-up.

 

An extreme example of memoization is the [Singleton pattern](./Singleton_pattern), specifically the implementation of its getter — a function that creates an object upon the first invocation, caches the instance, and returns the same object on all subsequent invocations.

 

## Other considerations

 

### Functional programming

 Main article: [Thunk § Functional programming](./Thunk#Functional_programming) 
|  | This sectionneeds expansion. You can help byadding missing information.(April 2014) |
| --- | --- |

 

Memoization is heavily used in compilers for [functional programming](./Functional_programming) languages, which often use [call by name](./Call_by_name) evaluation strategy. To avoid overhead with calculating argument values, compilers for these languages heavily use auxiliary functions called [thunks](./Thunk) to compute the argument values, and memoize these functions to avoid repeated calculations.

 

### Automatic memoization

 

While memoization may be added to functions *internally* and *explicitly* by a [computer programmer](./Computer_programmer) in much the same way the above memoized version of `factorial` is implemented, referentially transparent functions may also be automatically memoized *externally*.[[1]](./Memoization#cite_note-Norvig1991-1) The techniques employed by [Peter Norvig](./Peter_Norvig) have application not only in [Common Lisp](./Common_Lisp) (the language in which his paper demonstrated automatic memoization), but also in various other [programming languages](./Programming_language). Applications of automatic memoization have also been formally explored in the study of [term rewriting](./Term_rewriting)[[4]](./Memoization#cite_note-Hoffman1992-4) and [artificial intelligence](./Artificial_intelligence).[[5]](./Memoization#cite_note-MayfieldEtAl1995-5)

 

In programming languages where functions are [first-class objects](./First-class_object) (such as [Lua](./Lua_(programming_language)), [Python](./Python_(programming_language)), or [Perl](./Perl)[[6]](./Memoization#cite_note-perl-firstclass-6)), automatic memoization can be implemented by replacing (at run-time) a function with its calculated value once a value has been calculated for a given set of parameters. The function that does this value-for-function-object replacement can generically wrap any referentially transparent function. Consider the following pseudocode (where it is assumed that functions are first-class values):

  don't remove trailing whitespace from blank lines within the block  
```
function memoized-call (F is a function object parameter)
    if F has no attached array values then
        allocate an associative array called values;
        attach values to F;
    end if;

    if F.values[arguments] is empty then
        F.values[arguments] = F(arguments);
    end if;

    return F.values[arguments];
end function
```
  don't remove trailing whitespace from blank lines within the block  

In order to call an automatically memoized version of `factorial` using the above strategy, rather than calling `factorial` directly, code invokes `memoized-call(factorial)(n)`. Each such call first checks to see if a holder array has been allocated to store results, and if not, attaches that array. If no entry exists at the position `values[arguments]` (where `arguments` are used as the key of the associative array), a *real* call is made to `factorial` with the supplied arguments. Finally, the entry in the array at the key position is returned to the caller.

 

The above strategy requires *explicit* wrapping at each call to a function that is to be memoized. In those languages that allow [closures](./Closure_(computer_science)), memoization can be effected *implicitly* via a [functor](./Function_object) factory that returns a wrapped memoized function object in a [decorator pattern](./Decorator_pattern). In pseudocode, this can be expressed as follows:

  don't remove trailing whitespace from blank lines within the block  
```
function construct-memoized-functor (F is a function object parameter)
    allocate a function object called memoized-version;

    let memoized-version(arguments) be
        if self has no attached array values then [self is a reference to this object]
            allocate an associative array called values;
            attach values to self;
        end if;

        if self.values[arguments] is empty then
            self.values[arguments] = F(arguments);
        end if;

        return self.values[arguments];
    end let;

    return memoized-version;
end function
```
  don't remove trailing whitespace from blank lines within the block  

Rather than call `factorial`, a new function object `memfact` is created as follows:

 
```
 memfact = construct-memoized-functor(factorial)
```
 

The above example assumes that the function `factorial` has already been defined *before* the call to `construct-memoized-functor` is made. From this point forward, `memfact(n)` is called whenever the factorial of *n* is desired. In languages such as Lua, more sophisticated techniques exist which allow a function to be replaced by a new function with the same name, which would permit:

 
```
 factorial = construct-memoized-functor(factorial)
```
 

Essentially, such techniques involve attaching the *original function object* to the created functor and forwarding calls to the original function being memoized via an alias when a call to the actual function is required (to avoid endless [recursion](./Recursion)), as illustrated below:

  don't remove trailing whitespace from blank lines within the block  
```
function construct-memoized-functor (F is a function object parameter)
    allocate a function object called memoized-version;

    let memoized-version(arguments) be
        if self has no attached array values then [self is a reference to this object]
            allocate an associative array called values;
            attach values to self;
            allocate a new function object called alias;
            attach alias to self; [for later ability to invoke F indirectly]
            self.alias = F;
        end if;

        if self.values[arguments] is empty then
            self.values[arguments] = self.alias(arguments); [not a direct call to F]
        end if;

        return self.values[arguments];
    end let;

    return memoized-version;
end function
```
  don't remove trailing whitespace from blank lines within the block  

(Note: Some of the steps shown above may be implicitly managed by the implementation language and are provided for illustration.)

 

### Parsers

 

When a [top-down parser](./Top-down_parsing) tries to parse an [ambiguous](./Syntactic_ambiguity) input with respect to an ambiguous [context-free grammar](./Context-free_grammar) (CFG), it may need an exponential number of steps (with respect to the length of the input) to try all alternatives of the CFG in order to produce all possible parse trees. This eventually would require exponential memory space. Memoization was explored as a [parsing](./Parsing) strategy in 1991 by Peter Norvig, who demonstrated that an algorithm similar to the use of [dynamic programming](./Dynamic_programming) and state-sets in [Earley's algorithm](./Earley_parser) (1970), and tables in the [CYK algorithm](./CYK_algorithm) of Cocke, Younger and Kasami, could be generated by introducing automatic memoization to a simple [backtracking](./Backtracking) [recursive descent parser](./Recursive_descent_parser) to solve the problem of exponential time complexity.[[1]](./Memoization#cite_note-Norvig1991-1) The basic idea in Norvig's approach is that when a parser is applied to the input, the result is stored in a memotable for subsequent reuse if the same parser is ever reapplied to the same input.

 

Richard Frost and Barbara Szydlowski also used memoization to reduce the exponential time complexity of [parser combinators](./Parser_combinator), describing the result as a memoizing purely functional top-down backtracking language processor.[[7]](./Memoization#cite_note-Frost1996-7) Frost showed that basic memoized parser combinators can be used as building blocks to construct complex parsers as executable specifications of CFGs.[[8]](./Memoization#cite_note-Frost1994-8)[[9]](./Memoization#cite_note-Frost2003-9)

 

Memoization was again explored in the context of parsing in 1995 by Mark Johnson note:don't wikify name: not same MarkJ  and Jochen Dörre.[[10]](./Memoization#cite_note-Johnson1995-10)[[11]](./Memoization#cite_note-Johnson&Dorre-11) In 2002, it was examined in considerable depth by Bryan Ford in the form called [packrat parsing](./Packrat_parser).[[12]](./Memoization#cite_note-Ford2002-12)

 

In 2007, Frost, Hafiz and Callaghan[*[citation needed](./Wikipedia:Citation_needed)*] described a top-down parsing algorithm that uses memoization for refraining redundant computations to accommodate any form of ambiguous CFG in [polynomial](./Polynomial) time ([Θ](./Big_O_notation)(n4) for [left-recursive](./Left_recursion) grammars and Θ(n3) for non left-recursive grammars). Their top-down parsing algorithm also requires polynomial space for potentially exponential ambiguous parse trees by 'compact representation' and 'local ambiguities grouping'. Their compact representation is comparable with Tomita's compact representation of [bottom-up parsing](./Bottom-up_parsing).[[13]](./Memoization#cite_note-Tomita1985-13) Their use of memoization is not only limited to retrieving the previously computed results when a parser is applied to a same input position repeatedly (which is essential for polynomial time requirement); it is specialized to perform the following additional tasks:

 
- The memoization process (which could be viewed as a ‘wrapper’ around any parser execution) accommodates an ever-growing **direct left-recursive** parse by imposing depth restrictions with respect to input length and current input position.
- The algorithm's memo-table ‘lookup’ procedure also determines the reusability of a saved result by comparing the saved result's computational context with the parser's current context. This contextual comparison is the key to accommodate **indirect (or hidden) left-recursion**.
- When performing a successful lookup in a memotable, instead of returning the complete result-set, the process only returns the references of the actual result and eventually speeds up the overall computation.
- During updating the memotable, the memoization process groups the (potentially exponential) ambiguous results and ensures the polynomial space requirement.

 

Frost, Hafiz and Callaghan also described the implementation of the algorithm in PADL’08[*[citation needed](./Wikipedia:Citation_needed)*] as a set of [higher-order functions](./Higher-order_function) (called [parser combinators](./Parser_combinators)) in [Haskell](./Haskell_(programming_language)), which enables the construction of directly executable specifications of CFGs as language processors. The importance of their polynomial algorithm's power to accommodate ‘any form of ambiguous CFG’ with top-down parsing is vital with respect to the syntax and semantics analysis during [natural language processing](./Natural_language_processing). The [X-SAIGA](http://www.cs.uwindsor.ca/~hafiz/proHome.html) site has more about the algorithm and implementation details.

 

While Norvig increased the *power* of the parser through memoization, the augmented parser was still as time complex as Earley's algorithm, which demonstrates a case of the use of memoization for something other than speed optimization. Johnson and Dörre[[11]](./Memoization#cite_note-Johnson&Dorre-11) demonstrate another such non-speed related application of memoization: the use of memoization to delay linguistic constraint resolution to a point in a parse where sufficient information has been accumulated to resolve those constraints. By contrast, in the speed optimization application of memoization, Ford demonstrated that memoization could guarantee that [parsing expression grammars](./Parsing_expression_grammar) could parse in [linear](./Big_O_notation) time even those [languages](./Formal_language) that resulted in worst-case backtracking behavior.[[12]](./Memoization#cite_note-Ford2002-12)

 

Consider the following [grammar](./Formal_grammar):

 
```
S → (A c) | (B d)
A → X (a|b)
B → X b
X → x [X]
```
 

(Notation note: In the above example, the [production](./Formal_grammar#The_syntax_of_grammars) S → (A **c**) | (B **d**) reads: "An *S* is either an *A* followed by a **c** or a *B* followed by a **d**." The production X → **x** [X] reads "An *X* is an **x** followed by an optional *X*.")

 

This grammar generates one of the following three variations of [string](./String_(computer_science)): *xac*, *xbc*, or *xbd* (where *x* here is understood to mean *one or more *x*'s*.) Next, consider how this grammar, used as a parse specification, might effectto carry out, not "affect" a top-down, left-right parse of the string *xxxxxbd*:

 The rule *A* will recognize *xxxxxb* (by first descending into *X* to recognize one *x*, and again descending into *X* until all the *x*'s are consumed, and then recognizing the *b*), and then return to *S*, and fail to recognize a *c*. The next clause of *S* will then descend into B, which in turn **again descends into *X*** and recognizes the *x*'s by means of many recursive calls to *X*, and then a *b*, and returns to *S* and finally recognizes a *d*. 

The key concept here is inherent in the phrase **again descends into *X***. The process of looking forward, failing, backing up, and then retrying the next alternative is known in parsing as backtracking, and it is primarily backtracking that presents opportunities for memoization in parsing. Consider a function `RuleAcceptsSomeInput(Rule, Position, Input)`, where the parameters are as follows:

 
- `Rule` is the name of the rule under consideration.
- `Position` is the offset currently under consideration in the input.
- `Input` is the input under consideration.

 

Let the return value of the function `RuleAcceptsSomeInput` be the length of the input accepted by `Rule`, or 0 if that rule does not accept any input at that offset in the string. In a backtracking scenario with such memoization, the parsing process is as follows:

 When the rule *A* descends into *X* at offset 0, it memoizes the length 5 against that position and the rule *X*. After having failed at *d*, *B* then, rather than descending again into *X*, queries the position 0 against rule *X* in the memoization engine, and is returned a length of 5, thus saving having to actually descend again into *X*, and carries on *as if* it had descended into *X* as many times as before. 

In the above example, one or *many* descents into *X* may occur, allowing for strings such as *xxxxxxxxxxxxxxxxbd*. In fact, there may be *any number* of *x*'s before the *b*. While the call to S must recursively descend into X as many times as there are *x*'s, *B* will never have to descend into X at all, since the return value of `RuleAcceptsSomeInput(X, 0, xxxxxxxxxxxxxxxxbd)` will be 16 (in this particular case).

 

Those parsers that make use of [syntactic predicates](./Syntactic_predicate) are also able to memoize the results of predicate parses, as well, thereby reducing such constructions as:

 
```
S → (A)? A
A → /* some rule */
```
 

to one descent into *A*.

 

If a parser builds a [parse tree](./Parse_tree) during a parse, it must memoize not only the *length* of the input that matches at some offset against a given rule, but also must store the sub-tree that is generated by that rule at that offset in the input, since subsequent calls to the rule by the parser will not actually descend and rebuild that tree. For the same reason, memoized parser algorithms that generate calls to external code (sometimes called a [semantic action routine](./Semantic_action_routine)) when a rule matches must use some scheme to ensure that such rules are invoked in a predictable order.

 

Since, for any given backtracking or syntactic predicate capable parser not every grammar will *need* backtracking or predicate checks, the overhead of storing each rule's parse results against every offset in the input (and storing the parse tree if the parsing process does that implicitly) may actually *slow down* a parser. This effect can be mitigated by explicit selection of those rules the parser will memoize.[[14]](./Memoization#cite_note-AcarEtAl2003-14)

 

## See also

 
- [Approximate computing](./Approximate_computing) – category of techniques to improve efficiency
- [Computational complexity theory](./Computational_complexity_theory) – more information on algorithm complexity
- [Director string](./Director_string) – rapidly locating free variables in expressions
- [Flyweight pattern](./Flyweight_pattern) – an object programming [design pattern](./Design_pattern_(computer_science)), that also uses a kind of memoization
- [Hashlife](./Hashlife) – a memoizing technique to speed up the computation of [cellular automata](./Cellular_automata)
- [Lazy evaluation](./Lazy_evaluation) – shares some concepts with memoization
- [Materialized view](./Materialized_view) – analogous caching in database queries
- [Partial evaluation](./Partial_evaluation) – a related technique for automatic program optimization

 

## References

 
1. [1](./Memoization#cite_ref-Norvig1991_1-0) [2](./Memoization#cite_ref-Norvig1991_1-1) [3](./Memoization#cite_ref-Norvig1991_1-2) Norvig, Peter (1991). ["Techniques for Automatic Memoization with Applications to Context-Free Parsing"](https://dl.acm.org/doi/abs/10.5555/971738.971743). *Computational Linguistics*. **17** (1): 91–98.
2. [↑](./Memoization#cite_ref-2) Warren, David S. (1992-03-01). ["Memoing for logic programs"](https://doi.org/10.1145%2F131295.131299). *Communications of the ACM*. **35** (3): 93–111. [doi](./Doi_(identifier)):[10.1145/131295.131299](https://doi.org/10.1145%2F131295.131299). [ISSN](./ISSN_(identifier)) [0001-0782](https://search.worldcat.org/issn/0001-0782).
3. [↑](./Memoization#cite_ref-Michie1968_3-0) Michie, Donald (1968). ["'Memo' Functions and Machine Learning"](https://www.cs.utexas.edu/users/hunt/research/hash-cons/hash-cons-papers/michie-memo-nature-1968.pdf) (PDF). *[Nature](./Nature_(journal))*. **218** (5136): 19–22. [Bibcode](./Bibcode_(identifier)):[1968Natur.218...19M](https://ui.adsabs.harvard.edu/abs/1968Natur.218...19M). [doi](./Doi_(identifier)):[10.1038/218019a0](https://doi.org/10.1038%2F218019a0). [S2CID](./S2CID_(identifier)) [4265138](https://api.semanticscholar.org/CorpusID:4265138).
4. [↑](./Memoization#cite_ref-Hoffman1992_4-0) Hoffman, Berthold (1992). "Term Rewriting with Sharing and Memoïzation". In Kirchner, H.; Levi, G. (eds.). *Algebraic and Logic Programming: Third International Conference, Proceedings, Volterra, Italy, 2–4 September 1992*. Lecture Notes in Computer Science. Vol. 632. Berlin: Springer. pp. 128–142. [doi](./Doi_(identifier)):[10.1007/BFb0013824](https://doi.org/10.1007%2FBFb0013824). [ISBN](./ISBN_(identifier)) [978-3-540-55873-6](./Special:BookSources/978-3-540-55873-6).
5. [↑](./Memoization#cite_ref-MayfieldEtAl1995_5-0) Mayfield, James; et al. (1995). ["Using Automatic Memoization as a Software Engineering Tool in Real-World AI Systems"](http://ebiquity.umbc.edu/get/a/publication/799.pdf) (PDF). *Proceedings of the Eleventh IEEE Conference on Artificial Intelligence for Applications (CAIA '95)*. pp. 87–93. [doi](./Doi_(identifier)):[10.1109/CAIA.1995.378786](https://doi.org/10.1109%2FCAIA.1995.378786). [hdl](./Hdl_(identifier)):[11603/12722](https://hdl.handle.net/11603%2F12722). [ISBN](./ISBN_(identifier)) [0-8186-7070-3](./Special:BookSources/0-8186-7070-3). [S2CID](./S2CID_(identifier)) [8963326](https://api.semanticscholar.org/CorpusID:8963326).
6. [↑](./Memoization#cite_ref-perl-firstclass_6-0) ["Bricolage: Memoization"](http://perl.plover.com/MiniMemoize/memoize.html).
7. [↑](./Memoization#cite_ref-Frost1996_7-0) Frost, Richard; Szydlowski, Barbara (1996). ["Memoizing Purely Functional Top-Down Backtracking Language Processors"](https://doi.org/10.1016%2F0167-6423%2896%2900014-7). *Sci. Comput. Program*. **27** (3): 263–288. [doi](./Doi_(identifier)):[10.1016/0167-6423(96)00014-7](https://doi.org/10.1016%2F0167-6423%2896%2900014-7).
8. [↑](./Memoization#cite_ref-Frost1994_8-0) Frost, Richard (1994). "Using Memoization to Achieve Polynomial Complexity of Purely Functional Executable Specifications of Non-Deterministic Top-Down Parsers". *SIGPLAN Notices*. **29** (4): 23–30. [doi](./Doi_(identifier)):[10.1145/181761.181764](https://doi.org/10.1145%2F181761.181764). [S2CID](./S2CID_(identifier)) [10616505](https://api.semanticscholar.org/CorpusID:10616505).
9. [↑](./Memoization#cite_ref-Frost2003_9-0) Frost, Richard (2003). "Monadic Memoization towards Correctness-Preserving Reduction of Search". *Canadian Conference on AI 2003*. Lecture Notes in Computer Science. Vol. 2671. pp. 66–80. [doi](./Doi_(identifier)):[10.1007/3-540-44886-1_8](https://doi.org/10.1007%2F3-540-44886-1_8). [ISBN](./ISBN_(identifier)) [978-3-540-40300-5](./Special:BookSources/978-3-540-40300-5).
10. [↑](./Memoization#cite_ref-Johnson1995_10-0) Johnson, Mark (1995). "Memoization of Top-Down Parsing". *Computational Linguistics*. **21** (3): 405–417. [arXiv](./ArXiv_(identifier)):[cmp-lg/9504016](https://arxiv.org/abs/cmp-lg/9504016). [Bibcode](./Bibcode_(identifier)):[1995cmp.lg....4016J](https://ui.adsabs.harvard.edu/abs/1995cmp.lg....4016J).
11. [1](./Memoization#cite_ref-Johnson&Dorre_11-0) [2](./Memoization#cite_ref-Johnson&Dorre_11-1) Johnson, Mark & Dörre, Jochen (1995). "Memoization of Coroutined Constraints". *Proceedings of the 33rd Annual Meeting of the Association for Computational Linguistics*. Cambridge, Massachusetts. [arXiv](./ArXiv_(identifier)):[cmp-lg/9504028](https://arxiv.org/abs/cmp-lg/9504028).`{{cite book}}`:  CS1 maint: location missing publisher ([link](./Category:CS1_maint:_location_missing_publisher))
12. [1](./Memoization#cite_ref-Ford2002_12-0) [2](./Memoization#cite_ref-Ford2002_12-1) Ford, Bryan (2002). *Packrat Parsing: a Practical Linear-Time Algorithm with Backtracking* (Master’s thesis). Massachusetts Institute of Technology. [hdl](./Hdl_(identifier)):[1721.1/87310](https://hdl.handle.net/1721.1%2F87310).
13. [↑](./Memoization#cite_ref-Tomita1985_13-0) [Tomita, Masaru](./Masaru_Tomita) (1985). *Efficient Parsing for Natural Language*. Boston: Kluwer. [ISBN](./ISBN_(identifier)) [0-89838-202-5](./Special:BookSources/0-89838-202-5).
14. [↑](./Memoization#cite_ref-AcarEtAl2003_14-0) Acar, Umut A.; et al. (2003). "Selective Memoization". *Proceedings of the 30th ACM SIGPLAN-SIGACT Symposium on Principles of Programming Languages, 15–17 January 2003*. Vol. 38. New Orleans, Louisiana. pp. 14–25. [arXiv](./ArXiv_(identifier)):[1106.0447](https://arxiv.org/abs/1106.0447). [doi](./Doi_(identifier)):[10.1145/640128.604133](https://doi.org/10.1145%2F640128.604133). `{{cite book}}`: `|journal=` ignored ([help](./Help:CS1_errors#periodical_ignored))CS1 maint: location missing publisher ([link](./Category:CS1_maint:_location_missing_publisher))

 

## External links

   [![Wiktionary logo](//upload.wikimedia.org/wikipedia/commons/thumb/9/99/Wiktionary-logo-en-v2.svg/40px-Wiktionary-logo-en-v2.svg.png)](./File:Wiktionary-logo-en-v2.svg) Look up ***[memoization](https://en.wiktionary.org/wiki/Special:Search/memoization)*** in Wiktionary, the free dictionary.  Examples of memoization in various programming languages 
- [groovy.lang.Closure#memoize()](https://web.archive.org/web/20150302033735/http://groovy.codehaus.org/api/groovy/lang/Closure.html#memoize()) – Memoize is an [Apache Groovy](./Groovy_(programming_language)) 1.8 language feature.
- [Memoize](http://www.cliki.net/memoize) – Memoize is a small library, written by Tim Bradshaw, for performing memoization in [Common Lisp](./Common_Lisp).
- [IncPy](http://www.pgbovine.net/incpy.html) – A custom [Python](./Python_(programming_language)) interpreter that performs automatic memoization (with no required user annotations)
- Dave Herman's [Macros for defining memoized procedures](http://planet.racket-lang.org/display.ss?package=memoize.plt&owner=dherman) in [Racket](./Racket_(programming_language)).
- [Memoize.pm](https://metacpan.org/module/Memoize) – a [Perl module](./Perl_module) that implements memoized functions.
- [Java memoization](https://web.archive.org/web/20180506230333/http://www.onjava.com/pub/a/onjava/2003/08/20/memoization.html) – an example in Java using dynamic proxy classes to create a generic memoization pattern. ( archived version of [http://www.onjava.com/pub/a/onjava/2003/08/20/memoization.html](http://www.onjava.com/pub/a/onjava/2003/08/20/memoization.html) ).
- [memoization.java](https://github.com/sebhoss/memoization.java) - A Java memoization library.
- [C++Memo](https://archive.today/20140403004614/http://projects.giacomodrago.com/c++memo/) – A [C++](./C++) memoization framework.
- [C-Memo](https://sourceforge.net/projects/c-memo/) – Generic memoization library for C, implemented using pre-processor function wrapper macros.
- [Tek271 Memoizer](https://github.com/ahabra/memoize) – Open source Java memoizer using annotations and pluggable cache implementations.
- [memoizable](https://github.com/dkubb/memoizable) – A [Ruby](./Ruby_programming_language) gem that implements memoized methods.
- [Python memoization](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/52201) – A [Python](./Python_(programming_language)) example of memoization.
- [OCaml memoization](https://web.archive.org/web/20120106065126/http://martin.jambon.free.fr/309/pa_memo.ml.html) – Implemented as a [Camlp4](./Camlp4) syntax extension.
- [Memoization in Lua](http://lua-users.org/wiki/FuncTables) – Two example implementations of a general memoize function in [Lua](./Lua_(programming_language)).
- [Memoization in Mathematica](http://szhorvat.net/pelican/memoization-in-mathematica.html) – Memoization and limited memoization in [Mathematica](./Mathematica).
- [Memoization in Javascript](https://archive.today/20130203205946/http://talideon.com/weblog/2005/07/javascript-memoization.cfm) – Extending the Function prototype in [JavaScript](./JavaScript) ( archived version of [http://talideon.com/weblog/2005/07/javascript-memoization.cfm](https://talideon.com/weblog/2005/07/javascript-memoization.cfm) ).
- [Memoization in Javascript](http://odhyan.com/blog/2010/09/caching-in-javascript-yui-cache/) – Examples of memoization in javascript using own caching mechanism and using the YUI library
- [X-SAIGA](http://www.cs.uwindsor.ca/~hafiz/proHome.html) – eXecutable SpecificAtIons of GrAmmars. Contains publications related to top-down parsing algorithm that supports left-recursion and ambiguity in polynomial time and space.
- [Memoization in Scheme](http://codeimmersion.i3ci.hampshire.edu/2009/10/09/memoization/) – A [Scheme](./Scheme_(programming_language)) example of memoization on a class webpage.
- [Memoization in Combinatory Logic](https://code.google.com/p/clache/) – A web service to reduce [Combinatory Logic](./Combinatory_Logic) while memoizing every step in a database.
- [MbCache](https://code.google.com/p/mbcache/) – Cache method results in [.NET](./.NET_Framework).

 
| vteParsing algorithms |
| --- |
| Top-down | EarleyLLRecursive descentTail recursive |
| Bottom-up | PrecedenceSimpleOperatorShunting-yardLRSimpleLook-aheadCanonicalGeneralizedCYKRecursive ascentShift-reduce |
| Mixed, other | CombinatorChartLeft cornerStatistical |
| Related topics | PEGDefinite clause grammarDeterministic parsingDynamic programmingMemoizationParser generatorLALRParse treeASTScannerless parsingHistory of compiler constructionComparison of parser generatorsOperator-precedence grammar |