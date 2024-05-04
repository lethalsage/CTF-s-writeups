# REV
## `Enigma_Elysium`
### Points
200
### Challenge Description
```
Oops, I forgot to uncomment the print statement
```
### File Attached
[rev_me.out](/REV/rev_me.out)

### Explaination
as i downloaded it I couldn't open the file so i searched it on google and found a answer on [quora](https://www.quora.com/How-do-I-open-a-out-file-in-Linux)
![](/REV/Screenshot%20from%202023-10-23%2022-42-08.png)

so I did the command:
`cat -A rev_me.out`
and the output was:
![](/REV/Screenshot%20from%202023-10-23%2023-02-58.png)
scrolling down i found less filled lines by @
![](/REV/Screenshot%20from%202023-10-23%2022-46-56.png)
 and this line looks similar to the flag format
 ```
 ^@n1gm^@kc0^@y5^@d4r^@de{3^@4_3l^@1um}^@Result: %s$
```
and the i opened it on [dogbolt](https://dogbolt.org/)

on line 367 of decompiler angr i found similar line
![](/REV/Screenshot%20from%202023-10-23%2023-16-15.png)

```
 v0[0] = createNode("n1gm");
    v0[1] = createNode("kc0");
    v0[2] = createNode("y5");
    v0[1]->field_8 = createNode("d4r");
    v0[1]->field_10 = createNode("de{3");
    v0[2]->field_8 = createNode("4_3l");
    v0[2]->field_10 = createNode("1um}");
```
so by this and rearranging this i found the flag.


### Flag
`d4rkc0de{3n1gm4_3ly51um}`
