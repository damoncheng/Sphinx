=============================
Restructed summary
=============================

..
    This is a study restructedText based on sphinx   


**Inline Markup**

    *text*     #emphasis(italics)

    **text**   #string emphasis(boldface)

    ``text``   #code sample

**Lists and Quote-like blocks**

    * This is a bulleted list.
    * It has two items, the second item uses two lines.

    1. This is a numbered list.
    2. It has two items too.

    #. This is a numbered list.
    #. It has two items too.

    * this is
    * a list

        * with a nested list
        * and some subitems

    * and here the parent list continues

    term (up to a line of text)

        Definition of the term, which must be indented

        and can even consist of multiple paragraphs

    next term
        Description.

    | These lines are
    | broken exactly like in
    | the source file.

**Source Code**

This is a normal text paragraph. The next paragraph is a code sample::

    It is not processed in any way, except
    that the indentation is removed.

    It can span multiple lines.

This is a normal text paragraph again.

**Tables**

====== ====== ======
A      B      C
====== ====== ======
False  False  False
True   True   False
====== ====== ======

**Hperlinks**

This is a paragraph that contains `a link`_.

.. _a link : http://www.baidu.com/
