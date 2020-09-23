<div align="center">

## Infix 2 Postfix


</div>

### Description

It converts infix equation to postfix or reverse polish notation
 
### More Info
 
It uses string input with a maximum length of 50 which can be changed by the programmer

It shows the user what the postfix notation the entered equation and prints the answer to the screen.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Elmer Baluyo](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/elmer-baluyo.md)
**Level**          |Beginner
**User Rating**    |4.3 (17 globes from 4 users)
**Compatibility**  |C, C\+\+ \(general\)
**Category**       |[Math](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/math__3-12.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/elmer-baluyo-infix-2-postfix__3-780/archive/master.zip)

### API Declarations

```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <conio.h>
```


### Source Code

```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <conio.h>
#define MAX 50
int Stack[MAX];
int Top = 0;
void push (int x)
{
 if (Top<MAX)
  Stack[Top++] = x;
}
int pop (void)
{
 if (Top>0)
 return Stack[--Top];
 return MAX;
}
void get_infix (char *infix)
{
 printf("\nEnter infix notation(max:%d\)->", MAX);
 scanf("%s",infix);
}
infix_2_postfix(char *infix, char *postfix)
{
 while (*infix) {
  switch (*infix) {
  case '+':
  case '*':
   push (*infix);
   break;
  case '(':
   break;
  case ')':
   *postfix = (char) pop();
   postfix++;
   break;
  default:
   *postfix = *infix;
   postfix++;
   break;
  }
  infix++;
 }
 while (Top) {
 *postfix = (char) pop();
 postfix++;
 }
 *postfix = '\0';
}
int eval (char *postfix)
{
int ans = 0;
 while (*postfix) {
 switch (*postfix) {
  case '+': ans = (pop()-48) + (pop()-48); push(ans+48);
   break;
  case '*': ans = (pop()-48) * (pop()-48); push(ans+48);
   break;
  default:
   push(*postfix);
   break;
  }
 postfix++;
 }
 return ans;
}
void main(void)
{
int i;
char infix[MAX], postfix[MAX];
 get_infix(infix);
 infix_2_postfix(infix, postfix);
 printf("\n %s  %s = %d", infix, postfix, eval(postfix));
}
```

