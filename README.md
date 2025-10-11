
//p3

```


:T
[ 0 0 0 0 0 ] h !
[ 0 0 0 0 0 ] c !
1000 y !
1000 z !
200 p !

`CPU:    [ X X X X X ]    Bank:$` z . /N
/N
`          POT:$` p . /N
/N
`YOU:    [ ` 
h 0 ? 48 + /C 32 /C 
h 1 ? 48 + /C 32 /C 
h 2 ? 48 + /C 32 /C 
h 3 ? 48 + /C 32 /C 
h 4 ? 48 + /C 
` ]    Bank:$` y . /N
;


```

| Variable | Purpose               | Current Values |
| -------- | --------------------- | -------------- |
| `h[]`    | Player hand (5 cards) | `[0 0 0 0 0]`  |
| `c[]`    | CPU hand (5 cards)    | `[0 0 0 0 0]`  |
| `y`      | Player bank           | `1000`         |
| `z`      | CPU bank              | `1000`         |
| `p`      | Pot                   | `200`          |




```
> T
CPU:    [ X X X X X ]    Bank:$1000


          POT:$200


YOU:    [ 0 0 0 0 0 ]    Bank:$1000


> 

```

```
:S
12345 s !
;

:C
s 7 * 3 + s !
s 32555 > /T ( 1 s ! ) /E ( )
s 13 / 13 * - 1 +
;

:D
0 i !
5 (
  C h i ?!    
  C c i ?!    
  i 1 + i !
)
;

:T
[ 0 0 0 0 0 ] h !
[ 0 0 0 0 0 ] c !
1000 y !
1000 z !
200 p !

`CPU:    [ X X X X X ]    Bank:$` z . /N
/N
`          POT:$` p . /N
/N
`YOU:    [ ` 
h 0 ? 48 + /C 32 /C
h 1 ? 48 + /C 32 /C
h 2 ? 48 + /C 32 /C
h 3 ? 48 + /C 32 /C
h 4 ? 48 + /C
` ]    Bank:$` y . /N
;
```



