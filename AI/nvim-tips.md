我：I query the value of vim 'breakat' option by `:set breakat?`, but I cannot
determine if the result string contains space, how?

Warp AI:

## Method 1: Use echo to make spaces visible
```
:echo &breakat
```
This will show the string with spaces more clearly visible. (Khoguan: 無差)

## Method 2: Check the length and compare
```
:echo len(&breakat)
:echo len(substitute(&breakat, ' ', '', 'g'))
```
If the second number is smaller, then spaces are present.

## Method 3: Use substitute() to highlight spaces
```
:echo substitute(&breakat, ' ', '<SPACE>', 'g')
```
This replaces all spaces with <SPACE> to make them visible.

## Method 4: Check for space directly
```
:echo stridx(&breakat, ' ') >= 0 ? 'Contains space' : 'No space'
```
This returns a boolean-like result.

## Method 5: Use match() function
```
:echo match(&breakat, ' ') >= 0 ? 'Space found' : 'No space'
```

## Default breakat value
By default, breakat typically contains:
```
 ^I!@*-+;:,./?
```
Where ^I represents a tab character and the first character is indeed a space.

The most practical method is probably Method 3 using substitute() as it clearly
shows where spaces are located in the string.
