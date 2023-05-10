%{
int nline,nchar,nword;
%}
%%
[\n] { nline++; nchar+=yyleng;}
[^\t\n ]+ { nword++;  nchar+=yyleng;}
.|\n { nchar++; }
%%
int yywrap(void)
{
return 1;
}
int main(int argc,char *argv[])
{
yyin=fopen(argv[1],"r");
yylex();
printf("number of line =%d\n",nline);
printf("number of words =%d\n",nword);
printf("number of characters =%d\n",nchar);
fclose(yyin);
}
