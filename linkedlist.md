# Get start of second half

```text
while (d)
* ds  * ds      * d   * d       *  s  *  s
*  s  *  s      *  s  *  s      * ds  * ds
* ds  * ds      * ds  * ds      *  s  >  s
>  s  >  s      *  s  *  s      > ds  * d
* d   * d       > ds  > ds      *     *
*               *               * d   - d
- d   - d       - d   - d       
                                - d
front           broken          back

while (d && d.next)
* ds  * ds      * d   * d       *  s  *  s
*  s  *  s      *  s  *  s      * ds  * ds
* ds  > ds      * ds  * ds      >  s  >  s
>  s  *         *  s  >  s      * d   * d
* d   * d       > ds  * d       *     *
*               *               * d   - d
- d             - d
back            broken          broken

while (d && d.next && d.next.next) 
* ds  * ds      * d   * d       *  s  *  s
*  s  *  s      *  s  *  s      * ds  > ds
> ds  > ds      * ds  * ds      >  s  *  
*     *         >  s  >  s      * d   * d
* d   * d       * d   * d       *     *
*               *               * d   
broken          front           broken
```

# 1669. Merge In Between Linked Lists
* Get a-1, b+1, m-1 nodes and string them together

# 2487. Remove Nodes From Linked List
* monotonic stack, rebuilding the list at the same time

