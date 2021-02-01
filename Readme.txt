Compilation guide: https://stackoverflow.com/Questions/5456011/how-to-compile-lex-yacc-files-on-windows

Yacc guide: https://www.youtube.com/watch?v=__-wUHG2rfM

Definitions:
yyin :- the input stream pointer (i.e it points to an input file which is to be scanned or tokenised), however the default input of default main() is stdin .
yylex() :- implies the main entry point for lex, reads the input stream generates tokens, returns zero at the end of input stream . It is called to invoke the lexer (or scanner) and each time yylex() is called, the scanner continues processing the input from where it last left off.
yytext :- a buffer that holds the input characters that actually match the pattern (i.e lexeme) or say a pointer to the matched string .
yyleng :- the length of the lexeme .
yylval :- contains the token value .
yyval :- a local variable .*
yyout :- the output stream pointer (i.e it points to a file where it has to keep the output), however the default output of default main() is stdout .
yywrap() :- it is called by lex when input is exhausted (or at EOF). default yywrap always return 1.
yymore() :- returns the next token .
yyless(k) :- returns the first k characters in yytext .
yyparse() :- it parses (i.e builds the parse tree) of lexeme .*

The lexical analyzer returns VARIABLE and INTEGER tokens. For variables yylval specifies an index to the symbol table sym. For this program sym merely holds the value of the associated variable. When INTEGER tokens are returned, yylval contains the number scanned. Here is the input specification for lex.

The input specification for yacc follows. The tokens for INTEGER and VARIABLE are utilized by yacc to create #defines in y.tab.h for use in lex. This is followed by definitions for the arithmetic operators. We may specify %left, for left-associative or %right for right associative. The last definition listed has the highest precedence. Consequently multiplication and division have higher precedence than addition and subtraction. All four operators are left-associative. Using this simple technique we are able to disambiguate our grammar.
