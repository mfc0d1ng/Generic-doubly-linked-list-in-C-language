# Generic-doubly-linked-list-in-C-language
A shared library which provides a set of functions for handling the doubly linked list in C.

<h2> How to download ?</h2>
You can download it <a href="">here</a>

<h2> How to install? </h2>
 Unzip the downloaded file and move liblist.so to /usr/lib

 <h2> How to link? </h2>
  You can link the library to your C project as follows: gcc example.c -l list

  <br>
<h2> Examples </h2>

* Example A:

<pre>
<code class="language-c">
#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;
#include "list.h"

int main()
{
    /* Construct integers */
    list integers = list_new();

    for (size_t i = 101; i < 110; i++)
    {
        /* Add data to integers */
        list_push_back(int, &integers, i);
    }

    /* Insert 100 at the beginning of integers */
    list_insert(int, &integers, list_begin(&integers), 100);

    /* Print contents of integers */
    printf("list integers contains: ");
    for (list_iterator it = list_begin(&integers); it != NULL; it = it->next)
    {
        printf("%i ", list_data(int, it));
    }

    /* Erase integers */
    list_destroy(&integers);
    
    return EXIT_SUCCESS;
}
</code>
</pre>

* Example B:

<pre>
<code class="language-c">
#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;
#include "list.h"

 /* Sort predicate */
int sort_fruits_predicate(const void* __ls, const void* __rs)
{
    return strcmp(*(const char **)__ls, *(const char **)__rs) > 0;
}

int main()
{
    /* Construct fruits */
    list* fruits = list_object();

    /* Add fruits to List fruits */
    list_push_back(const char*, fruits, "strawberry");
    list_push_back(const char*, fruits, "apple");
    list_push_back(const char*, fruits, "pineapple");
    list_push_back(const char*, fruits, "banana");

    /* Sort fruits in ascending order */
    list_sort(fruits, sort_fruits_predicate);

    /* Print contents of fruits */
    printf("List fruits after sorting: ");
    for (list_iterator it = list_begin(fruits); it != NULL; it = it->next)
    {
        printf("%s ", list_data(const char*, it));
    }

    /* Erase fruits */
    list_delete(fruits);
    
    return EXIT_SUCCESS;
}
</code>
</pre>
