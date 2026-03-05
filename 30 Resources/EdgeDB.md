- In edge db **data is represented as strongly typed objects that contain set-valued scalar properties and links to other objects.**

- Everything is a Set (in the mathematical sense)

- Type

- Like Tables or Relations in SQL

- Objects

- like rows in DBs

- except each is assigned an uuid

- Property

- Like columns

- name, type pairs

- has carnality, can be:

1.  Empty

2.  One

    1.  keyword: `required property`

    2.  same as \'required\' in SDL

3.  AtMostOne

    1.  keyword: `property`

4.  AtLeastOne

    1.  keyword: `required muti property`

5.  Many

    1.  keyword: `multi`

- Links

- like Foreign keys

- except the links can have property too

\* \* \* \*
