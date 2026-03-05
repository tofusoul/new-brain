- Strings are just lists of chars 

- **String slicing**

- `word[0:3]` will give you the first 3 chars of the word

- notice that this is \'left inclusive, right exclusive. even though the right side is 3, it will not give the element at index 3, which will be the 4th element, it gives us back the 3rd element, where ase the left side starts at zero

- `word[-3]` gets us the char 3 back from the end of the word

- `word[::3]` 3rd value in the slicing notation refers to the step size

- so this will select every 3rd char

- **Sting methods**

- `format()`

- make numbers more readable
