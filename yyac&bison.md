#lex 常用变量及函数#

##Lex 变量##
yyin   FILE* 类型。 它指向 lexer 正在解析的当前文件
yyout	FILE* 类型。 它指向记录 lexer 输出的位置。 缺省情况下，yyin 和 yyout 都指向标准输入和输出。
yytext	匹配模式的文本存储在这一变量中（char*）。
yyleng	给出匹配模式的长度。
yylineno	提供当前的行数信息。 （lexer不一定支持。）
yylval  Yacc调用lex的yylex()获得标志（token），与标志对应的值由lex放在变量yylval中。yylval的类型由YYSTYPE决定，YYSTYPE缺省类型是int






#Lex 函数#
yylex()	这一函数开始分析。 它由 Lex 自动生成。
yywrap()	这一函数在文件（或输入）的末尾调用。 如果函数的返回值是1，就停止解析。 因此它可以用来解析多个文件。 代码可以写在第三段，这就能够解析多个文件。 方法是使用 yyin 文件指针（见上表）指向不同的文件，直到所有的文件都被解析。 最后，yywrap() 可以返回 1 来表示解析的结束。
yyless(int n)	这一函数可以用来送回除了前�n? 个字符外的所有读出标记。
yymore()	这一函数告诉 Lexer 将下一个标记附加到当前标记后。
