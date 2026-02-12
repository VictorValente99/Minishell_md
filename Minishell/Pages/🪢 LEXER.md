Mainly does: 
- Reads the input (string) of the readline.
- Group the charactes in to lexemes (a word || symbol, recognized as a cmd) > classification.
- Generate the tokens list.
- Manage the symbol lists.
## How the lexer talks with other parts?

![[Pasted image 20260212105715.png]]
In order to optimize the analysis, it goes like:

tokens > 
send to syntax analyser > 
checks for syntax errors > 
if goes rigth > 
get_next_token > 
else > stop;

## Example:

`Minishell$ echo 'ola mundo' | cat -e` 

The tokens and symbols become:

| 1   | echo      | id 1 |
| --- | --------- | ---- |
| 2   | '         |      |
| 3   | ola mundo | id 2 |
| 4   | '         |      |
| 5   | \|        |      |
| 6   | cat       | id 3 |
| 7   | -         |      |
| 8   | e         | id 4 |

So when a lexeme is taken and recognized as a pattern, it become a **token**, and then, the token is analysed to turn into a **identifier**. The identifiers are saved on the **Symbol Table**,  which stores essential information about each name, such as its type,  scope, and memory location. 
So if it is a reserved word or symbol, it will be a token, and if it is something else, it will generate a identifier, in the order of the **Symbol Table**.  
The method to read the lexemes it will be by buffer.