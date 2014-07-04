# A cheat sheet for Google Spreadsheets

#### Check field is unique

1st arg is the area to search in, every other arg is the criteria. Notice the `counta()`:

```
=counta(filter(A:A, A:A = A6))
```

#### Capitalize First Letter

```
=proper(A1)
```
