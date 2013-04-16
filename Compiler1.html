<!DOCTYPE>
<html>
    <head>
        <meta charset="utf-8" />
        <script type="text/javascript">
            /*log打印函数 每次在原log上追加str和换行*/
            function log(str) { 
                var log_node = document.getElementById("log");
                var text_node = document.createTextNode(str);
                var br_node = document.createElement("br");
                log_node.appendChild(text_node);
                log_node.appendChild(br_node);
            }
        </script>
        <script type="text/javascript">
            /* 字符串字符处理雷 */
            function Reader(str) {
                this.data = str;
                this.currPos = 0;
                this.length = str.length;
            }
            /* 获取字符串下一个字符 */
            Reader.prototype.nextChar = function() {
                if(this.currPos >= this.length) {
                    return -1;
                }
                return this.data[this.currPos++];
            }
            /* 回退当前读取位置指针 n是回退的步伐 默认为1步*/
            Reader.prototype.retract = function(n) {
                if(n === undefined) {
                    n = 1;
                }
                this.currPos -= n;
                if(this.currPos < 0) {
                    this.currPos = 0;
                }
            }
        </script>
        <script type="text/javascript">
            /* 定义Token类型 */
            function Token(type, text) {
                this.type = type;
                this.text = text;
            }
            /* 定义关键字 保留字 */
            Token.tokens = {};
            Token.tokens.EOS_TOKEN = 1; //end of stream
            // using + 1 allows adding a new token easily later
            Token.tokens.COLON_TOKEN = Token.tokens.EOS_TOKEN + 1; //:
            Token.tokens.SEMICOLON_TOKEN = Token.tokens.COLON_TOKEN + 1; //;
            Token.tokens.LEFTPAREN_TOKEN = Token.tokens.SEMICOLON_TOKEN + 1; //( 4
            Token.tokens.RIGHTPAREN_TOKEN = Token.tokens.LEFTPAREN_TOKEN + 1; //)
            Token.tokens.LEFTBRACE_TOKEN = Token.tokens.RIGHTPAREN_TOKEN + 1; //{
            Token.tokens.RIGHTBRACE_TOKEN = Token.tokens.LEFTBRACE_TOKEN + 1; //}
            Token.tokens.MOD_TOKEN = Token.tokens.RIGHTBRACE_TOKEN + 1; //%

            Token.tokens.VAR_TOKEN = Token.tokens.MOD_TOKEN + 1; //var 9
            Token.tokens.TYPE_TOKEN = Token.tokens.VAR_TOKEN + 1; //int bool
            Token.tokens.BOOLLITERAL_TOKEN = Token.tokens.TYPE_TOKEN + 1; //true false
            Token.tokens.IF_TOKEN = Token.tokens.BOOLLITERAL_TOKEN + 1; //if 12
            Token.tokens.ELSE_TOKEN = Token.tokens.IF_TOKEN + 1; //else
            Token.tokens.WHILE_TOKEN = Token.tokens.ELSE_TOKEN + 1; //while
            Token.tokens.PRINT_TOKEN = Token.tokens.WHILE_TOKEN + 1; //print
            Token.tokens.IDENTIFIER_TOKEN = Token.tokens.PRINT_TOKEN + 1; //id 16

            Token.tokens.INTLITERAL_TOKEN = Token.tokens.IDENTIFIER_TOKEN + 1; // int number

            Token.tokens.PLUS_TOKEN = Token.tokens.INTLITERAL_TOKEN + 1; //+
            Token.tokens.PLUSPLUS_TOKEN = Token.tokens.PLUS_TOKEN + 1; //++
            Token.tokens.PLUSASSIGN_TOKEN = Token.tokens.PLUSPLUS_TOKEN + 1; //+=
            Token.tokens.MINUS_TOKEN = Token.tokens.PLUSASSIGN_TOKEN + 1; //-
            Token.tokens.MINUSMINUS_TOKEN = Token.tokens.MINUS_TOKEN + 1; //--
            Token.tokens.MINUSASSIGN_TOKEN = Token.tokens.MINUSMINUS_TOKEN + 1; // -=
            Token.tokens.MULT_TOKEN = Token.tokens.MINUSASSIGN_TOKEN + 1; // *
            Token.tokens.DIV_TOKEN = Token.tokens.MULT_TOKEN + 1; // /
            Token.tokens.ASSIGN_TOKEN = Token.tokens.DIV_TOKEN + 1; // = 
            Token.tokens.EQUAL_TOKEN = Token.tokens.ASSIGN_TOKEN + 1; // ==
            Token.tokens.NOTEQUAL_TOKEN = Token.tokens.EQUAL_TOKEN + 1; // !=
            Token.tokens.GREATER_TOKEN = Token.tokens.NOTEQUAL_TOKEN + 1; // >
            Token.tokens.GREATEREQUAL_TOKEN = Token.tokens.GREATER_TOKEN + 1; // >=
            Token.tokens.LESS_TOKEN = Token.tokens.GREATEREQUAL_TOKEN + 1; // <
            Token.tokens.LESSEQUAL_TOKEN = Token.tokens.LESS_TOKEN + 1; // <=
            Token.tokens.AND_TOKEN = Token.tokens.LESSEQUAL_TOKEN + 1; // &&
            Token.tokens.OR_TOKEN = Token.tokens.AND_TOKEN + 1; // ||
            Token.tokens.NOT_TOKEN = Token.tokens.OR_TOKEN + 1; // !
             
            Token.tokens.LINECOMMENT_TOKEN = Token.tokens.NOT_TOKEN + 1; // //
            Token.tokens.BLOCKCOMMENT_TOKEN = Token.tokens.LINECOMMENT_TOKEN + 1;// /*  .... */

            Token.tokens.ERROR_TOKEN = Token.tokens.BLOCKCOMMENT_TOKEN + 1;// 词法错误
            Token.tokens.NEWLINE_TOKEN = Token.tokens.ERROR_TOKEN + 1;// \n \r  39

            Token.backwardMap = {}; //for inverse look-up
            for(var x in Token.tokens) {
                Token.backwardMap[Token.tokens[x]] = x;
            }
        </script>
        <script type="text/javascript">
            function Scanner(reader) {
                this.reader = reader;
                this.currentToken = new Token();
                this.currLine = 0;
                this.bufferStr = "";
                this.state = Scanner.START_STATE;
            }
            Scanner.START_STATE = 0;
            Scanner.IDENTIFIER_STATE = Scanner.START_STATE + 1;
            Scanner.MULTISYMBOL_STATE = Scanner.IDENTIFIER_STATE + 1;
            Scanner.SLASH_STATE= Scanner.MULTISYMBOL_STATE + 1;
            Scanner.INTLITERAL_STATE = Scanner.SLASH_STATE + 1;

            Scanner.prototype.makeToken = function(type, text) {
                this.currentToken.type = type;
                this.currentToken.text = text;
                return type;
            };
            Scanner.prototype.nextToken = function() {
                switch(this.state) {
                    case Scanner.START_STATE:
                        var next_char = this.reader.nextChar();
                        /* 遇到字母开头 表明可能是标示符或者是保留字 跳转状态*/
                        if((next_char >= 'a' && next_char <= 'z') || (next_char >= 'A' && next_char <= 'Z')) {
                            this.state = Scanner.IDENTIFIER_STATE;
                            this.bufferStr = next_char; //记录单词首字符
                            return this.nextToken();
                        }
                        /* 遇到数字 跳到整数处理状态 */
                        if(next_char >= '0' && next_char <= '9') { 
                            this.state = Scanner.INTLITERAL_STATE;
                            this.bufferStr = next_char; //记录单词首字符
                            return this.nextToken();
                        }
                        switch(next_char) {
                            case -1 : return this.makeToken(Token.tokens.EOS_TOKEN);
                            case ':': return this.makeToken(Token.tokens.COLON_TOKEN);
                            case ';': return this.makeToken(Token.tokens.SEMICOLON_TOKEN);
                            case '(': return this.makeToken(Token.tokens.LEFTPAREN_TOKEN);
                            case ')': return this.makeToken(Token.tokens.RIGHTPAREN_TOKEN);
                            case '{': return this.makeToken(Token.tokens.LEFTBRACE_TOKEN);
                            case '}': return this.makeToken(Token.tokens.RIGHTBRACE_TOKEN);
                            case '%': return this.makeToken(Token.tokens.MOD_TOKEN);
                            case '*': return this.makeToken(Token.tokens.MULT_TOKEN);
                            case '\r': case '\n':
                                this.currLine++;
                                return this.makeToken(Token.tokens.NEWLINE_TOKEN);
                            default:
                                /*非字母 非单子元无歧义字符 则可能是其他有歧义符号*/
                                this.state = Scanner.MULTISYMBOL_STATE;
                                this.bufferStr = next_char;
                                return this.nextToken();
                        }
                        break;
                    case Scanner.INTLITERAL_STATE:
                        var next_char = this.reader.nextChar();
                        if(next_char >= '0' && next_char <= '9') { 
                            this.bufferStr += next_char;
                            return this.nextToken();
                        } else {
                            /* 读取了连续由数字构成的整数 则一个整数字元读取结束 切换状态到开始状态 以便下次读取新的字元*/
                            this.state = Scanner.START_STATE;
                            /* 由于多读入了一个非数字字符来判断是否整数结束 所以要对字符读取器回退一个字符 */
                            this.reader.retract(); 
                            return this.makeToken(Token.tokens.INTLITERAL_TOKEN, parseInt(this.bufferStr));
                        }
                        break;
                    case Scanner.IDENTIFIER_STATE:
                        var next_char = this.reader.nextChar();
                        if((next_char >= 'a' && next_char <= 'z') || (next_char >= 'A' && next_char <= 'Z')) {
                            this.bufferStr += next_char;
                            return this.nextToken();
                        } else {
                            /* 读取了连续由字母构成的单词 则一个单词字元读取结束 切换状态到开始状态 以便下次读取新的字元*/
                            this.state = Scanner.START_STATE;
                            /* 由于多读入了一个非字母字符来判断是否单词结束 所以要对字符读取器回退一个字符 */
                            this.reader.retract(); 
                        }

                        switch(this.bufferStr) {
                            case "var":
                                return this.makeToken(Token.tokens.VAR_TOKEN);
                            case "int": case "bool":
                                return this.makeToken(Token.tokens.TYPE_TOKEN, this.bufferStr);
                            case "true": case "false": case "TRUE": case "FALSE": 
                                return this.makeToken(Token.tokens.BOOLLITERAL_TOKEN, this.bufferStr.toLowerCase());
                            case "if": 
                                return this.makeToken(Token.tokens.IF_TOKEN);
                            case "else":
                                return this.makeToken(Token.tokens.ELSE_TOKEN);
                            case "while": 
                                return this.makeToken(Token.tokens.WHILE_TOKEN);
                            case "print" :
                                return this.makeToken(Token.tokens.PRINT_TOKEN);
                            default:
                                return this.makeToken(Token.tokens.IDENTIFIER_TOKEN, this.bufferStr);
                        }
                        break;
                    case Scanner.MULTISYMBOL_STATE:
                        this.state = Scanner.START_STATE;
                        switch(this.bufferStr) {
                            case '+':
                                var c = this.reader.nextChar();
                                if(c == '+') { //++
                                    return this.makeToken(Token.tokens.PLUSPLUS_TOKEN); 
                                } else if(c == '=') { // +=
                                    return this.makeToken(Token.tokens.PLUSASSIGN_TOKEN);
                                } else { // +
                                    this.reader.retract();
                                    return this.makeToken(Token.tokens.PLUS_TOKEN);
                                }
                            case '-':
                                var c = this.reader.nextChar();
                                if(c == '-') { //--
                                    return this.makeToken(Token.tokens.MINUSMINUS_TOKEN); 
                                } else if(c == '=') { // -=
                                    return this.makeToken(Token.tokens.MINUSASSIGN_TOKEN);
                                } else { // -
                                    this.reader.retract();
                                    return this.makeToken(Token.tokens.MINUS_TOKEN);
                                }
                            case '=':
                                var c = this.reader.nextChar();
                                if(c == '=') { //==
                                    return this.makeToken(Token.tokens.EQUAL_TOKEN);
                                } else { // = 
                                    this.reader.retract();
                                    return this.makeToken(Token.tokens.ASSIGN_TOKEN);
                                }
                            case '!':
                                var c = this.reader.nextChar();
                                if(c == '=') { // !=
                                    return this.makeToken(Token.tokens.NOTEQUAL_TOKEN);
                                } else { // !
                                    this.reader.retract();
                                    return this.makeToken(Token.tokens.NOT_TOKEN);
                                }
                            case '<':
                                var c = this.reader.nextChar();
                                if(c == '=') { //<=
                                    return this.makeToken(Token.tokens.LESSEQUAL_TOKEN);
                                } else { // <
                                    this.reader.retract();
                                    return this.makeToken(Token.tokens.LESS_TOKEN);
                                }
                            case '>':
                                var c = this.reader.nextChar();
                                if(c == '=') { //>=
                                    return this.makeToken(Token.tokens.GREATEREQUAL_TOKEN);
                                } else { // >
                                    this.reader.retract();
                                    return this.makeToken(Token.tokens.GREATER_TOKEN);
                                }
                            case '|':
                                var c = this.reader.nextChar();
                                if(c == '|') { // ||
                                    return this.makeToken(Token.tokens.OR_TOKEN);
                                } else { // error
                                    if(c != -1) {
                                        this.reader.retract();
                                    }
                                    return this.makeToken(Token.tokens.ERROR_TOKEN, "line " + this.currLine + ": Missing a |");
                                }
                            case '&':
                                var c = this.reader.nextChar();
                                if(c == '&') { // &&
                                    return this.makeToken(Token.tokens.AND_TOKEN);
                                } else { //error
                                    if(c != -1) {
                                        this.reader.retract();
                                    }
                                    return this.makeToken(Token.tokens.ERROR_TOKEN, "line " + this.currLine + ": Missing a &");
                                }
                            case '/':
                                this.state = Scanner.SLASH_STATE;
                                return this.nextToken();
                            default:
                                return this.nextToken();
                                //ignore other char
                        }
                        break;
                    case Scanner.SLASH_STATE:
                        this.state = Scanner.START_STATE;
                        var c = this.reader.nextChar();
                        this.bufferStr = "";
                        switch(c) {
                            case '/': // //....
                                do {
                                    var d = this.reader.nextChar();
                                    this.bufferStr += d;
                                } while(d != '\r' && d != '\n');
                                this.currLine++;
                                return this.makeToken(Token.tokens.LINECOMMENT_TOKEN, this.bufferStr);
                            case '*': // /* sdff */
                                while(true) {
                                    var d = this.reader.nextChar();
                                    if(d == '*') {
                                        if(this.reader.nextChar() == '/') {
                                            return this.makeToken(Token.tokens.BLOCKCOMMENT_TOKEN, this.bufferStr);
                                        } else {
                                            this.reader.retract();
                                        }
                                    } else if(d == -1) {
                                        return this.makeToken(Token.tokens.BLOCKCOMMENT_TOKEN, this.bufferStr);
                                    } else {
                                        this.bufferStr += d;
                                        if(d == '\r' || d == '\n') {
                                            this.currLine++;
                                        }
                                    }
                                }
                            default : // /
                                return this.makeToken(Token.tokens.DIV_TOKEN);
                        }
                        break;
                    default:
                        break;
                }
            };
        </script>
        <script type="text/javascript">
            function Parser(scanner) {
                this.scanner = scanner;
                this.currentToken = new Token();
                this.lookaheadToken = new Token();
                this.lookaheadToken.used = true;
            }
            Parser.prototype.nextToken = function() {
                if(this.lookaheadToken.used) { //lookaheadToken 被使用了
                    do {
                        var token = this.scanner.nextToken();
                    //skip comments and errors
                    }while(token == Token.tokens.BLOCKCOMMENT_TOKEN || token == Token.tokens.LINECOMMENT_TOKEN || token == Token.tokens.ERROR_TOKEN);

                    this.currentToken.type = this.scanner.currentToken.type;
                    this.currentToken.text = this.scanner.currentToken.text;
                    return token;
                } else { //looaheadToken 没有被使用
                    this.currentToken.type = this.lookaheadToken.type;
                    this.currentToken.text = this.lookaheadToken.text;
                    this.lookaheadToken.used = true;
                    return this.currentToken.type;
                }
            }
            Parser.prototype.lookahead = function() {
                if(this.lookaheadToken.used) {
                    do {
                        var token = this.scanner.nextToken();
                    }while(token == Token.tokens.BLOCKCOMMENT_TOKEN || token == Token.tokens.LINECOMMENT_TOKEN || token == Token.tokens.ERROR_TOKEN);

                    this.lookaheadToken.type = this.scanner.currentToken.type;
                    this.lookaheadToken.text = this.scanner.currentToken.text;
                    this.lookaheadToken.used = false;
                    return token;
                } else {
                    return this.lookaheadToken.type;
                }
            }
            //the entry point of our parser
            Parser.prototype.parse = function() {
                var rootBlock = new ExpressionBlockNode();
                this.parseExpressions(rootBlock);
                return rootBlock;
            }
            //to parse a list of expressions
            Parser.prototype.parseExpressions = function(expressionBlockNode) {
                while (this.lookahead() != Token.tokens.RIGHTBRACE_TOKEN &&
                       this.lookahead() != Token.tokens.EOS_TOKEN){
                    // skip \r \n Token
                    if(this.lookahead() == Token.tokens.NEWLINE_TOKEN) {
                        this.nextToken();
                        continue;
                    }
                    var expressionNode = this.parseExpression();
                    if (expressionNode){
                        expressionBlockNode.push(expressionNode);
                    }
                }
            }
            //to parse an expression 
            Parser.prototype.parseExpression = function() {
                switch (this.lookahead()){
                    case Token.tokens.PRINT_TOKEN: // print
                        var printToken = this.nextToken();
                        var expressionNode = this.parseExpression();
                        if (expressionNode == undefined){
                            log("Line " + this.scanner.currLine + ":(Syntax Error) Missing an expression after \"print\"");
                        }
                        this.matchSemicolon();
                        return new PrintNode(expressionNode, this.scanner.currLine);
                    case Token.tokens.VAR_TOKEN: //var
                        return this.parseVarExpression();
                    case Token.tokens.IF_TOKEN: // if
                        return this.parseIfExpression();
                    case Token.tokens.WHILE_TOKEN: // while
                        return this.parseWhileExpression();
                    default:
                        //unexpected, consume it
                        return this.parseCompoundExpression(0);
                }
            }
            //parse var a:bool; or var b:int = 213; 
            Parser.prototype.parseVarExpression = function() {
                //cosume var token
                this.nextToken();
                
                if(this.lookahead() == Token.tokens.IDENTIFIER_TOKEN) {  // is a id
                    this.nextToken(); // consume id token
                    var varName = this.currentToken.text;
                    if(this.lookahead() != Token.tokens.COLON_TOKEN) { // is not :
                        log("Line " + this.scanner.currLine + ":(Syntax Error) Expecting a : after " + varName);
                        this.skipError();
                        return;
                    }
                    this.nextToken(); //consume : token
                    if(this.lookahead() != Token.tokens.TYPE_TOKEN) { // is not type token
                        log("Line " + this.scanner.currLine + ":(Syntax Error) Expecting a \"int\" or \"bool\" after :");
                        this.skipError();
                        return;
                    }
                    this.nextToken(); //consume type token
                    var type = this.currentToken.text;
                    var initNode;
                    if(this.lookahead() == Token.tokens.ASSIGN_TOKEN) { // is a = token
                        this.nextToken(); //consume = token
                        initNode = this.parseExpression();
                    }
                    this.matchSemicolon();
                    return new VariableNode(varName, type, initNode, this.scanner.currLine);
                }
                log("Line " + this.scanner.currLine + ":(Syntax Error) Expecting an identifier after \"var\"");
                this.skipError();
            }
            Parser.prototype.parseIfExpression = function() {
                //cosume if token
                this.nextToken();

                var condition =  this.parseParenExpression();
                var expressions = this.parseBlockExpression();
                var elseExpressions;
                if(this.lookahead() == Token.tokens.ELSE_TOKEN) {
                    //cosume else token
                    this.nextToken();
                    elseExpressions = this.parseBlockExpression();
                }
                return new IfNode(condition, expressions, elseExpressions, this.scanner.currLine);
            }
            Parser.prototype.parseWhileExpression = function() {
                //cosume while token
                this.nextToken();

                var condition =  this.parseParenExpression();
                var expressions = this.parseBlockExpression();
                return new WhileNode(condition, expressions, this.scanner.currLine);
            }
            Parser.prototype.parseParenExpression = function() {
                if(this.lookahead() != Token.tokens.LEFTPAREN_TOKEN) {
                    log("Line " + this.scanner.currLine + ":(Syntax Error) Expecting a ( ");
                } else {
                    this.nextToken(); //cosume ( token
                }
                var expression = this.parseExpression();
                if(this.lookahead() != Token.tokens.RIGHTPAREN_TOKEN) {
                    log("Line " + this.scanner.currLine + ":(Syntax Error) Expecting a ) ");
                } else {
                    this.nextToken(); //cosume ) token
                }
                return expression;
            }
            Parser.prototype.parseBlockExpression = function() {
                if(this.lookahead() != Token.tokens.LEFTBRACE_TOKEN) {
                    log("Line " + this.scanner.currLine + ":(Syntax Error) Expecting a { ");
                } else {
                    this.nextToken(); //cosume { token
                }
                var block = new ExpressionBlockNode();
                var blockExpression = this.parseExpressions(block);
                if(this.lookahead() != Token.tokens.RIGHTBRACE_TOKEN) {
                    log("Line " + this.scanner.currLine + ":(Syntax Error) Expecting a } ");
                } else {
                    this.nextToken(); //cosume } token
                }
                return block;
            }
            Parser.prototype.matchSemicolon = function() {
                if(this.lookahead() != Token.tokens.SEMICOLON_TOKEN) { //一个语句结束了 应该末尾是一个;
                    log("Line " + this.scanner.currLine + ":(Syntax Error) Expecting a ; at the end of expression");
                } else {
                    this.nextToken(); //consume ; token
                }
            }
            Parser.prototype.parseOperand = function() {  // 对算数表达式进行分项 例如 1 + 2 * (b * (4 / 6) - a) + 5 - -5
                var token = this.nextToken();
                switch(token) {
                    case Token.tokens.INTLITERAL_TOKEN: // 整数常量
                        return new IntNode(this.currentToken.text, this.scanner.currLine);
                    case Token.tokens.BOOLLITERAL_TOKEN: // bool 常量
                        return new BoolNode(this.currentToken.text, this.scanner.currLine);
                    case Token.tokens.IDENTIFIER_TOKEN: // 标示符
                        var identifier = new IdentifierNode(this.currentToken.text, this.scanner.currLine);
                        if(this.lookahead() == Token.tokens.MINUSMINUS_TOKEN) {
                            this.nextToken(); //consume --
                            return new PostDecrementNode(identifier, this.scanner.currLine); // id--
                        } else if(this.lookahead() == Token.tokens.PLUSPLUS_TOKEN) {
                            this.nextToken(); //consume ++
                            return new PostIncrementNode(identifier, this.scanner.currLine); // id++
                        } else {
                            return identifier; // id
                        }
            		case Token.tokens.MINUSMINUS_TOKEN: // --id
            			if (this.lookahead() == Token.tokens.IDENTIFIER_TOKEN){
            				this.nextToken();
            				return new PreDecrementNode(new IdentifierNode(this.currentToken.text, this.scanner.currLine), this.scanner.currLine);
            			}else{
                            log("Line " + this.scanner.currLine + ":(Syntax Error) Expecting an identifier for -- expression");
            				return null;
            			}
            		case Token.tokens.PLUSPLUS_TOKEN: // ++id
            			if (this.lookahead() == Token.tokens.IDENTIFIER_TOKEN){
            				this.nextToken();
            				return new PreIncrementNode(new IdentifierNode(this.currentToken.text, this.scanner.currLine), this.scanner.currLine);
            			}else{
                            log("Line " + this.scanner.currLine + ":(Syntax Error) Expecting an identifier for ++ expression");
            				return null;
            			}
                    case Token.tokens.LEFTPAREN_TOKEN: // 左括号 （
                        var operand = new ParenNode(this.parseCompoundExpression(0), this.scanner.currLine); // (....) 括号表达式项目
                        if(this.lookahead() == Token.tokens.RIGHTPAREN_TOKEN) { 
                            // consume )
                            this.nextToken();
                        } else {
                            log("Line " + this.scanner.currLine + ":(Syntax Error) Expecting a ) ");
                        }
                        return operand;
            		case Token.tokens.NOT_TOKEN:
			            return new NotNode(this.parseOperand(), this.scanner.currLine); // 非  因为!的优先级最高 所以可以单独拿出来
                    case Token.tokens.MINUS_TOKEN: 
                        return new NegateNode(this.parseOperand(), this.scanner.currLine); // 负数
            		case Token.tokens.SEMICOLON_TOKEN:  // ;表达式结束 
			            return null;
                    default:
                        log("Line " + this.scanner.currLine + ":(Syntax Error) Unexpected Token ");
                        return null;
                }
            }
            Parser.prototype.parseCompoundExpression = function(rightBindingPower) { //  处理复杂的表达式
                var operandNode = this.parseOperand(); //得到表达式第一个操作数项目
                if(operandNode == null) {
                    return null;
                }
                var compoundExpressionNode = new CompoundNode(this.scanner.currLine);
                compoundExpressionNode.push(operandNode);  //操作数压堆栈

                var operator = this.lookahead(); //获取操作符
                var leftBindingPower = this.getBindingPower(operator);
                if(leftBindingPower == -1) { //不是一个操作符 表明表达式结束
                    return compoundExpressionNode;
                }

                while(rightBindingPower < leftBindingPower) { //这里的left 和 right 我们习惯的反方向 
                    operator = this.nextToken();
                    compoundExpressionNode.push(this.createOperatorNode(operator)); //运算符压堆栈

                    var node = this.parseCompoundExpression(leftBindingPower);
                    compoundExpressionNode.push(node);   // 操作数(一个表达式)压堆栈
                    
                    operator = this.lookahead(); //接下来的操作符
                    leftBindingPower = this.getBindingPower(operator);
                    if(leftBindingPower == -1) { //不是操作符 表明表达式结束
                        return compoundExpressionNode;
                    }
                }
                return compoundExpressionNode;
            }
            Parser.prototype.getBindingPower = function(token) { //算符优先级 数字越高越优先
                switch(token) {
		            case Token.tokens.MULT_TOKEN:
		            case Token.tokens.DIV_TOKEN:
		            case Token.tokens.MOD_TOKEN:
		            	return 200; // * / %

                    case Token.tokens.PLUS_TOKEN:
                    case Token.tokens.MINUS_TOKEN:
                        return 190; //+ -

		            case Token.tokens.EQUAL_TOKEN:
		            case Token.tokens.NOTEQUAL_TOKEN:
			            return 180;  // == !=

		            case Token.tokens.AND_TOKEN: 
			            return 170; // &&
		            case Token.tokens.OR_TOKEN:
			            return 160; // ||

			        case Token.tokens.ASSIGN_TOKEN:
		            case Token.tokens.MINUSASSIGN_TOKEN:
		            case Token.tokens.PLUSASSIGN_TOKEN:
			            return 150; // == -= +=

                    default:
                        return -1;
                }
            }
            Parser.prototype.createOperatorNode = function(operator) { //返回操作符node
                switch(operator) {
                    case Token.tokens.PLUS_TOKEN:
                        return new OperatorPlusNode(this.scanner.currLine);
                    case Token.tokens.MINUS_TOKEN:
                        return new OperatorMinusNode(this.scanner.currLine);
                    case Token.tokens.MULT_TOKEN:
                        return new OperatorMultNode(this.scanner.currLine);
                    case Token.tokens.DIV_TOKEN:
                        return new OperatorDivNode(this.scanner.currLine);
            		case Token.tokens.MOD_TOKEN:
            			return new OperatorModNode(this.scanner.currLine);
            		case Token.tokens.AND_TOKEN:
            			return new OperatorAndNode(this.scanner.currLine);
            		case Token.tokens.OR_TOKEN:
            			return new OperatorOrNode(this.scanner.currLine);
            		case Token.tokens.EQUAL_TOKEN:
            			return new OperatorEqualNode(this.scanner.currLine);
            		case Token.tokens.NOTEQUAL_TOKEN:
            			return new OperatorNotEqualNode(this.scanner.currLine);
                    case Token.tokens.ASSIGN_TOKEN:
                        return new OperatorAssignNode(this.scanner.currLine);
                    case Token.tokens.MINUSASSIGN_TOKEN:
                        return new OperatorMinusAssignNode(this.scanner.currLine);
                    case Token.tokens.PLUSASSIGN_TOKEN:
                        return new OperatorPlusAssignNode(this.scanner.currLine);
                    default:
                        return null;
                }
            }
            Parser.prototype.skipError = function() {
                while(this.lookahead() != Token.tokens.NEWLINE_TOKEN && this.lookahead() != Token.tokens.EOS_TOKEN) {
                    this.nextToken();
                }
            }
        </script>
        <script type="text/javascript">
            function extend(subClass, baseClass) {
                function inheritance() {}
                inheritance.prototype = baseClass.prototype;
                
                subClass.prototype = new inheritance();
                subClass.prototype.constructor = subClass;
                subClass.baseConstructor = baseClass;
                subClass.superClass = baseClass.prototype;
            }

            function Node(param) {
            }

            function ExpressionBlockNode() {
                ExpressionBlockNode.baseConstructor.call(this, "test");
                this.expressions = [];
            }
            extend(ExpressionBlockNode, Node);
            ExpressionBlockNode.prototype.push = function(expression) {
                this.expressions.push(expression);
            }
            ExpressionBlockNode.prototype.iterate = function(func) {
                for(var i = 0, l = this.expressions.length; i < l; i++) {
                    var expression = this.expressions[i];
                    func(expression, i);
                }
            }

            function PrintNode(expressionNode, line) {
                this.expressionNode = expressionNode;
                this.line = line;
            }
            extend(PrintNode, Node);

            function IntNode(data, line){
                this.data = data;
                this.line = line;
            }
            extend(IntNode, Node);

            function BoolNode(data, line){
                this.data = data;
                this.line = line;
            }
            extend(IntNode, Node);

            function VariableNode(varName, type, initExpressionNode, line) {
                this.varName = varName;
                this.type = type;
                this.initExpressionNode = initExpressionNode;
                this.line = line;
            }
            extend(VariableNode, Node);

            function IfNode(conditionExpression, expressions, elseExpressions, line){
                this.conditionExpression = conditionExpression;
                this.expressions = expressions;
                this.elseExpressions = elseExpressions;
                this.line = line;
            }
            extend(IfNode, Node);

            function WhileNode(conditionExpression, expressions, line){
                this.conditionExpression = conditionExpression;
                this.expressions = expressions;
                this.line = line;
            }
            extend(WhileNode, Node);

            function IdentifierNode(identifer, line){
            	this.identifer = identifer;
                this.line = line;
            }
            extend(IdentifierNode, Node);
            
            function ParenNode(node, line){
            	this.node = node;
                this.line = line;
            }
            extend(ParenNode, Node);
            
            function NegateNode(node, line){
            	this.node = node;
                this.line = line;
            }
            extend(NegateNode, Node);
            
            function CompoundNode(line){
            	this.nodes = [];
                this.line = line;
            }
            extend(CompoundNode, Node);
            CompoundNode.prototype.push = function (node){
            	this.nodes.push(node);
            }

            function OperatorNode(){
            }
            extend(OperatorNode, Node);
            
            function OperatorPlusNode(line){
                this.line = line;
            }
            extend(OperatorPlusNode, OperatorNode);
            
            function OperatorMinusNode(line){
                this.line = line;
            }
            extend(OperatorMinusNode, OperatorNode);
            
            function OperatorMultNode(line){
                this.line = line;
            }
            extend(OperatorMultNode, OperatorNode);
            
            function OperatorDivNode(line){
                this.line = line;
            }
            extend(OperatorDivNode, OperatorNode);
            
            function OperatorModNode(line){
                this.line = line;
            }
            extend(OperatorModNode, OperatorNode);
            
            function OperatorAndNode(line){
                this.line = line;
            }
            extend(OperatorAndNode, OperatorNode);
            
            function OperatorOrNode(line){
                this.line = line;
            }
            extend(OperatorOrNode, OperatorNode);
            
            function OperatorEqualNode(line){
                this.line = line;
            }
            function NotNode(node, line){
	            this.node = node;
                this.line = line;
            }
            extend(NotNode, Node);
            extend(OperatorEqualNode, OperatorNode);
            
            function OperatorNotEqualNode(line){
                this.line = line;
            }
            extend(OperatorNotEqualNode, OperatorNode);

            function OperatorAssignNode(line){
                this.line = line;
            }
            extend(OperatorAssignNode, OperatorNode);
            
            function OperatorPlusAssignNode(line){
                this.line = line;
            } extend(OperatorPlusAssignNode, OperatorNode);
            
            function OperatorMinusAssignNode(line){
                this.line = line;
            }
            extend(OperatorMinusAssignNode, OperatorNode);
            
            function PostIncrementNode(node, line){
            	this.node = node;
                this.line = line;
            }
            extend(PostIncrementNode, OperatorNode);
            
            function PreIncrementNode(node, line){
            	this.node = node;
                this.line = line;
            }
            extend(PreIncrementNode, OperatorNode);
            
            function PostDecrementNode(node, line){
            	this.node = node;
                this.line = line;
            }
            extend(PostDecrementNode, OperatorNode);
            
            function PreDecrementNode(node, line){
            	this.node = node;
                this.line = line;
            }
            extend(PreDecrementNode, OperatorNode);
        </script>

        <script type="text/javascript">
        function Analyser() {
            this.vars = {};
        }
        Analyser.TYPE_BOOL = 1;
        Analyser.TYPE_INT = 2;
        Analyser.prototype.evaluateExpressionBlockNode = function(node) {
            if(!node) {
                return;
            }
            for(var i = 0; i<node.expressions.length; i++) {
                this.evaluateExpressionNode(node.expressions[i]);
            }
        }
        Analyser.prototype.evaluateExpressionNode = function(node) {
            if (node instanceof VariableNode){
        		this.evaluateVariableNode(node);
        	}else if (node instanceof PrintNode){
        		this.evaluatePrintNode(node);
        	}else if (node instanceof CompoundNode){
        		this.evaluateCompoundNode(node);
        	}else if (node instanceof IdentifierNode){
        		this.evaluateIdentifierNode(node);
        	}else if (node instanceof IntNode){
        		this.evaluateIntNode(node);
        	}else if (node instanceof BoolNode){
        		this.evaluateBoolNode(node);
        	}else if (node instanceof PostIncrementNode){
        		this.evaluatePostIncrementNode(node);
        	}else if (node instanceof PreIncrementNode){
        		this.evaluatePreIncrementNode(node);
        	}else if (node instanceof PostDecrementNode){
        		this.evaluatePostDecrementNode(node);
        	}else if (node instanceof PreDecrementNode){
        		this.evaluatePreDecrementNode(node);
        	}else if (node instanceof NegateNode){
        		this.evaluateNegateNode(node);
        	}else if (node instanceof NotNode){
        		this.evaluateNotNode(node);
        	}else if (node instanceof ParenNode){
        		this.evaluateParenNode(node);
        	}else if (node instanceof IfNode){
        		this.evaluateIfNode(node);
        	}else if (node instanceof WhileNode){
        		this.evaluateWhileNode(node);
        	}
        }
        Analyser.prototype.evaluateIntNode = function(node) {
            node.valueType = Analyser.TYPE_INT;
        }
        Analyser.prototype.evaluateBoolNode= function(node) {
            node.valueType = Analyser.TYPE_BOOL;
        }
        Analyser.prototype.evaluatePrintNode = function(node) {
            this.evaluateExpressionNode(node.expressionNode);
        }
        Analyser.prototype.evaluateNegateNode = function  (node){
            this .evaluateExpressionNode(node.node);
            node.valueType = node.node.valueType;
        }
        Analyser.prototype.evaluateNotNode = function  (node){
            this .evaluateExpressionNode(node.node);
            node.valueType = node.node.valueType;
        }
        Analyser.prototype.evaluateParenNode = function  (node){
            this .evaluateExpressionNode(node.node);
            node.valueType = node.node.valueType;
        }
        Analyser.prototype.evaluatePostIncrementNode = function  (node){
            this .evaluateExpressionNode(node.node);
            node.valueType = node.node.valueType;
        }
        Analyser.prototype.evaluatePreIncrementNode = function  (node){
            this .evaluateExpressionNode(node.node);
            node.valueType = node.node.valueType;
        }
        Analyser.prototype.evaluatePostDecrementNode = function  (node){
            this .evaluateExpressionNode(node.node);
            node.valueType = node.node.valueType;
        }
        Analyser.prototype.evaluatePreDecrementNode = function  (node){
            this .evaluateExpressionNode(node.node);
            node.valueType = node.node.valueType;
        }
        Analyser.prototype.evaluateCompoundNode = function(node) {
            var type = null;
            var operator = null;

            for (var i = 0; i < node.nodes.length; i++) {
                var subNode = node.nodes[i];
                this.evaluateExpressionNode(subNode);

                if(type == null) {
                    type = subNode.valueType;
                } else if(subNode instanceof OperatorNode) {
                    operator = subNode;
                } else if(operator instanceof OperatorPlusNode || 
                          operator instanceof OperatorMinusNode ||
                          operator instanceof OperatorMultNode ||
                          operator instanceof OperatorDivNode || 
                          operator instanceof OperatorModNode) {
                    if(type != Analyser.TYPE_INT || subNode.valueType != Analyser.TYPE_INT) {
                        log("Line " + operator.line + ":(Semantic Error) " + " Require Integers on both sides of arithmetic operator");
                    }
                    type = Analyser.TYPE_INT;
                } else if(operator instanceof OperatorAndNode || operator instanceof OperatorOrNode) {
                    if(type != Analyser.TYPE_BOOL|| subNode.valueType != Analyser.TYPE_BOOL) {
                        log("Line " + operator.line + ":(Semantic Error) " + " Require Booleans on both sides of logical operator");
                    }
                    type = Analyser.TYPE_BOOL;
                } else if(operator instanceof OperatorEqualNode || operator instanceof OperatorNotEqualNode) {
                    if(type != subNode.valueType) {
                        log("Line " + operator.line + ":(Semantic Error) " +" Require the type on both sides of comparison operator to be the same");
                    }
                    type = Analyser.TYPE_BOOL;
                } else if(operator instanceof OperatorAssignNode) {
                    if(type != subNode.valueType) {
                        log("Line " + operator.line + ":(Semantic Error) " +" Require the type on both sides of \"=\" to be the same");
                    }
                } else if(operator instanceof OperatorMinusAssignNode || operator instanceof OperatorPlusAssignNode) {
                    if(type != Analyser.TYPE_INT || subNode.valueType != Analyser.TYPE_INT) {
                        log("Line " + operator.line + ":(Semantic Error) " +" Require the type on both sides of plus/minus assignment operator to be the same");
                    }
                }
            //    operator = null;
            }
            node.valueType = type;
        }
        Analyser.prototype.evaluateIfNode = function  (node){
            this.evaluateExpressionNode(node.conditionExpression);
            if  (node.conditionExpression.valueType != Analyser.TYPE_BOOL){
                log("Line " + node.conditionExpression.line+ ":(Semantic Error) " + " The condition must be of Boolean type.");
            }
         
            this.evaluateExpressionBlockNode(node.expressions);
            this.evaluateExpressionBlockNode(node.elseExpressions);
        }
        Analyser.prototype.evaluateWhileNode = function  (node){
            this.evaluateExpressionNode(node.conditionExpression);
            if  (node.conditionExpression.valueType != Analyser.TYPE_BOOL){
                log("Line " + node.conditionExpression.line+ ":(Semantic Error) " + " The condition must be of Boolean type.");
            }
            this.evaluateExpressionBlockNode(node.expressions);
        }
        Analyser.prototype.evaluateIdentifierNode = function(node) {
            if(!this.vars[node.identifer]) {  //变量没有提前声明
                log("Line " + node.line + ":(Semantic Error) " + node.identifer + " should be declared before using.");
            } else {
                node.valueType = this.vars[node.identifer].valueType;
            }
        }
        Analyser.prototype.evaluateVariableNode = function(node) {
            if(this.vars[node.varName]) {
                log("Line " + node.line + ":(Semantic Error) " + node.varName + " has been declared already.");
            } else {
                this.vars[node.varName] = node;
            }

            if(node.initExpressionNode) { //有初始化表达式
                this.evaluateExpressionNode(node.initExpressionNode);
                // 变量声明类型与初始化类型匹配检查
                if(node.type == "bool" && node.initExpressionNode.valueType == Analyser.TYPE_INT) {
                    log("Line " + node.line + ":(Semantic Error) " + node.varName + " is bool type, can't assign int value.");
                } else if(node.type == "int" && node.initExpressionNode.valueType == Analyser.TYPE_BOOL) {
                    log("Line " + node.line + ":(Semantic Error) " + node.varName + " is int type, can't assign bool value.");
                }
            } else { //自动初始化变量
                if(node.type == "bool") {
                    node.initExpressionNode = new BoolNode("false");
                } else if(node.type == "int") {
                    node.initExpressionNode = new IntNode(0);
                }
            }

            node.valueType = node.type == "bool" ? Analyser.TYPE_BOOL : Analyser.TYPE_INT;
        }
        </script>

        <script type="text/javascript">
        function Compiler() {
            this.lineBreak = "<br/>";
            this.register = 0;
        }
        Compiler.prototype.getMachineCode = function(expressionBlockNode) {
            this.code = "";
            this.evaluateExpressionBlockNode(expressionBlockNode);
            return this.code;
        }
        Compiler.prototype.getNextRegister = function() {
            return "$" + this.register++;
        }
        Compiler.prototype.writeln = function(code) {
            this.code = this.code + code + this.lineBreak;
            log(code);
        }
        Compiler.prototype.evaluateExpressionBlockNode = function(node) {
            if(!node) {
                return;
            }
            for(var i = 0; i<node.expressions.length; i++) {
                this.evaluateExpressionNode(node.expressions[i]);
            }
        }
        Compiler.prototype.evaluateExpressionNode = function(node) {
            if (node instanceof VariableNode){
        		return this.evaluateVariableNode(node);
        	}else if (node instanceof PrintNode){
        		return this.evaluatePrintNode(node);
        	}else if (node instanceof CompoundNode){
        		return this.evaluateCompoundNode(node);
        	}else if (node instanceof IdentifierNode){
        		return this.evaluateIdentifierNode(node);
        	}else if (node instanceof IntNode){
        		return this.evaluateIntNode(node);
        	}else if (node instanceof BoolNode){
        		return this.evaluateBoolNode(node);
        	}else if (node instanceof PostIncrementNode){
        		return this.evaluatePostIncrementNode(node);
        	}else if (node instanceof PreIncrementNode){
        		return this.evaluatePreIncrementNode(node);
        	}else if (node instanceof PostDecrementNode){
        		return this.evaluatePostDecrementNode(node);
        	}else if (node instanceof PreDecrementNode){
        		return this.evaluatePreDecrementNode(node);
        	}else if (node instanceof NegateNode){
        		return this.evaluateNegateNode(node);
        	}else if (node instanceof NotNode){
        		return this.evaluateNotNode(node);
        	}else if (node instanceof ParenNode){
        		return this.evaluateParenNode(node);
        	}else if (node instanceof IfNode){
        		return this.evaluateIfNode(node);
        	}else if (node instanceof WhileNode){
        		return this.evaluateWhileNode(node);
        	}
        }
        Compiler.prototype.evaluateIntNode = function(node) {
            var register = this.getNextRegister();
            this.writeln("lwi " + register + ", " + node.data + ";");
            return register;
        }
        Compiler.prototype.evaluateBoolNode= function(node) {
            var register = this.getNextRegister();
		    this.writeln("lwi " + register + "," + (node.data == "true" ? 1 : 0) + ";");
            return register;
        }
        Compiler.prototype.evaluatePrintNode = function(node) {
            var register = this.evaluateExpressionNode(node.expressionNode);
            this.writeln("print " + register + ";");
        }
        Compiler.prototype.evaluateNegateNode = function  (node){
            var register = this .evaluateExpressionNode(node.node);
        }
        Compiler.prototype.evaluateNotNode = function  (node){
            var register = this .evaluateExpressionNode(node.node);
        }
        Compiler.prototype.evaluateParenNode = function  (node){
            var resgister = this .evaluateExpressionNode(node.node);
        }
        Compiler.prototype.evaluatePostIncrementNode = function  (node){
            var register = this .evaluateExpressionNode(node.node);
        }
        Compiler.prototype.evaluatePreIncrementNode = function  (node){
            var register = this .evaluateExpressionNode(node.node);
        }
        Compiler.prototype.evaluatePostDecrementNode = function  (node){
            var register = this .evaluateExpressionNode(node.node);
        }
        Compiler.prototype.evaluatePreDecrementNode = function  (node){
            var register = this .evaluateExpressionNode(node.node);
        }
        Compiler.prototype.evaluateCompoundNode = function(node) {
            var operator = null;
            var resultRegister = null;

            for (var i = 0; i < node.nodes.length; i++) {
                var subNode = node.nodes[i];
                var currRegister = this.evaluateExpressionNode(subNode);

                if(subNode instanceof OperatorNode) {
                    operator = subNode;
                } else if(resultRegister == null) {
                    resultRegister = this.getNextRegister();
                    this.writeln("move " + resultRegister + ", " + currRegister + ";");
                } else if(operator instanceof OperatorPlusNode) {
                    this.writeln("add " + resultRegister + ", " + resultRegister + ", " + currRegister);
                } else if(operator instanceof OperatorMinusNode) {
                    this.writeln("sub " + resultRegister + ", " + resultRegister + ", " + currRegister);
                } else if(operator instanceof OperatorMultNode) {
                } else if(operator instanceof OperatorDivNode) {
                } else if(operator instanceof OperatorModNode) {
                } else if(operator instanceof OperatorAndNode) { 
                } else if(operator instanceof OperatorOrNode) {
                } else if(operator instanceof OperatorEqualNode) {
                } else if(operator instanceof OperatorNotEqualNode) {
                } else if(operator instanceof OperatorAssignNode) {
                } else if(operator instanceof OperatorMinusAssignNode) {
                } else if(operator instanceof OperatorPlusAssignNode) {
                }
            }
            return resultRegister;
        }
        Compiler.prototype.evaluateIfNode = function  (node){
            this.evaluateExpressionNode(node.conditionExpression);
            if  (node.conditionExpression.valueType != Compiler.TYPE_BOOL){
                log("Line " + node.conditionExpression.line+ ":(Semantic Error) " + " The condition must be of Boolean type.");
            }
         
            this.evaluateExpressionBlockNode(node.expressions);
            this.evaluateExpressionBlockNode(node.elseExpressions);
        }
        Compiler.prototype.evaluateWhileNode = function  (node){
            this.evaluateExpressionNode(node.conditionExpression);
            if  (node.conditionExpression.valueType != Compiler.TYPE_BOOL){
                log("Line " + node.conditionExpression.line+ ":(Semantic Error) " + " The condition must be of Boolean type.");
            }
            this.evaluateExpressionBlockNode(node.expressions);
        }
        Compiler.prototype.evaluateIdentifierNode = function(node) {
            if(!this.vars[node.identifer]) {  //变量没有提前声明
                log("Line " + node.line + ":(Semantic Error) " + node.identifer + " should be declared before using.");
            } else {
                node.valueType = this.vars[node.identifer].valueType;
            }
        }
        Compiler.prototype.evaluateVariableNode = function(node) {
            if(this.vars[node.varName]) {
                log("Line " + node.line + ":(Semantic Error) " + node.varName + " has been declared already.");
            } else {
                this.vars[node.varName] = node;
            }

            if(node.initExpressionNode) { //有初始化表达式
                this.evaluateExpressionNode(node.initExpressionNode);
                // 变量声明类型与初始化类型匹配检查
                if(node.type == "bool" && node.initExpressionNode.valueType == Compiler.TYPE_INT) {
                    log("Line " + node.line + ":(Semantic Error) " + node.varName + " is bool type, can't assign int value.");
                } else if(node.type == "int" && node.initExpressionNode.valueType == Compiler.TYPE_BOOL) {
                    log("Line " + node.line + ":(Semantic Error) " + node.varName + " is int type, can't assign bool value.");
                }
            } else { //自动初始化变量
                if(node.type == "bool") {
                    node.initExpressionNode = new BoolNode("false");
                } else if(node.type == "int") {
                    node.initExpressionNode = new IntNode(0);
                }
            }

            node.valueType = node.type == "bool" ? Compiler.TYPE_BOOL : Compiler.TYPE_INT;
        }
        </script>
        <script type="text/javascript">
            window.onload = function () {
                var textarea = document.getElementById("source_code");
                var run_button = document.getElementById("run");
                /* 测试Scanner类 逐个读取Token 且输出每次Token到log*/
                run_button.onclick = function() {
                    var code_to_be_compiled = textarea.value;
                    var reader = new Reader(code_to_be_compiled);
                    var scanner = new Scanner(reader);
                    var parser = new Parser(scanner);
                    var expressionBlockNode = parser.parse();
                    console.log(expressionBlockNode);
                    var analyser = new Analyser();
                    analyser.evaluateExpressionBlockNode(expressionBlockNode);
                    var compiler = new Compiler();
                    var code = compiler.getMachineCode(expressionBlockNode);
                };
            };
        </script>
    </head>
    <body>
        <textarea id="source_code" style="width:600px; height:200px">
print 3 + 1 + 5;
/*语法生成树在js console log里*/
        </textarea>
        <button id="run">Run</button>
        <div id="log">
        </div>
    </body>
</html>
