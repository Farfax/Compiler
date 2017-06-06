#include<iostream>
#include<iomanip>
#include <cmath>
template<class Type>
class stack
{
	int Size;

	class Node
	{
	public:
		Node() :
			Data(NULL),
			Next(NULL)
		{}
		Type Data;
		Node* Next;

	} Nodes;

public:
	stack() :
		Size(0)
	{}
	~stack()
	{
		while (!empty()) // kek it's work xD
			pop();
	}

	Type& top()
	{
		return Nodes.Next->Data;
	}

	void pop()
	{
		if (Nodes.Next == NULL)
			return;
		else
		{
			Node* temp = Nodes.Next->Next;
			// Nodes.Next=NULL; //  delete Nodes.Next;Stos didn't allow to delete :(
			delete Nodes.Next; //Lol it's work now, i don't know why xD
			Nodes.Next = temp;
			Size--;
		}


	}

	void push(const Type& toAdd)
	{
		Node* temp = new Node;
		temp->Data = toAdd;
		temp->Next = Nodes.Next;
		Nodes.Next = temp;
		Size++;
	}

	bool empty()
	{
		return Size == 0;
	}

	int size()
	{
		return Size;
	}
};
template<class T>
class vector // it's not true vector , but ok here
{
	int iter, limiter;
	T* value;
public:
	vector(int _size) :
		iter(0),
		limiter(_size)
	{
		value = new T[_size];
	}
	vector(const vector<T>& vec)
	{
		iter = vec.iter;
		limiter = vec.limiter;

		value = new T[iter];
		memcpy(value, vec.value, sizeof(T)*iter);
		//for (int i = 0; i < vec.iter; i++)
		//	value[i] = vec.value[i];
	}
	vector() :
		iter(0),
		limiter(0)
	{
		value = nullptr;
	}
	~vector()
	{
		//if(value!=nullptr)
		//delete[] value;
		//
		//value = nullptr;
	}
	T* begin()
	{
		return value;
	}

	T* end()
	{
		return &value[iter];
	}
	void push_back(T toAdd) // if error check on T
	{
		if (iter >= limiter)
			resize(limiter + 100);

		value[iter] = toAdd;
		//	std::swap(toAdd, value[iter]);
		iter++;
	}

	void resize(const int& newSize = 50)
	{

		if (value == nullptr)
			value = new T[newSize];
		else
		{
			T* newArray = new T[newSize];
			//value[iter - 1] = NULL;
			memcpy(newArray, value, sizeof(T)*iter);
		//	for (int i = 0; i < iter; i++)
		//		newArray[i] = value[i];
			delete[] value;
			value = newArray;
		}
		limiter = newSize;

	}

	bool empty() const
	{
		return  iter == 0;
	}

	int size() const
	{
		return iter;
	}

	void clear()
	{
		delete[] value;
		value = nullptr;
		limiter = 0;
		iter = 0;
	}
	T& operator[](const int& idx)
	{
		return value[idx];
	}

	T operator[](const int& idx) const
	{
		return value[idx];
	}
};

class string
{
	vector<char> value;
public:
	string()
	{
	}

	string(const string& obj)
	{
		int i = 0;

		for (i = 0; i<obj.size(); i++)
			value.push_back(obj[i]);
	}

	string(const char* obj)
	{
		int i = 0;

		while (obj[i] != '\0')
		{
			value.push_back(obj[i]);
			i++;
		}
	}

	void resize(int newSize)
	{
		value.resize(newSize);
	}

	int size() const
	{
		return value.size();
	}

	bool empty() const
	{
		return value.empty();
	}

	void clear()
	{
		value.clear();
	}
	int toInt() const
	{
		int result = 0;

		for (int i = 0; i < size(); i++)
			result += pow((float)10, (int)(size() - 1 - i))*(value[i] - '0');


		return result;
	}

	string& operator+=(const string& rhs)
	{
		for (int i = 0; i < rhs.size(); i++)
			value.push_back(rhs[i]);

		return *this;
	}

	string& operator+=(char rhs)
	{
		value.push_back(rhs);
		return *this;
	}

	string& operator+=(const char* rhs)
	{
		int i = 0;
		while (rhs[i] != '\0' && rhs[i] != EOF)
		{
			value.push_back(rhs[i]);
			i++;
		}
		return *this;
	}
	char& operator[](int idx)
	{
		return value[idx];
	}

	const char& operator[](const int& idx) const
	{
		return value[idx];
	}

	friend std::ostream& operator<<(std::ostream& os, const string& obj)
	{
		// write obj to stream
		for (int i = 0; i < obj.size(); i++)
			std::cout << obj[i];

		return os;
	}

	friend inline bool operator==(const string& lhs, const string& rhs)
	{
		if (lhs.size() != rhs.size())
			return false;

		for (int i = 0; i < rhs.size(); i++)
			if (lhs[i] != rhs[i])
				return false;

		return true;
	}

	friend inline bool operator!=(const string& lhs, const string& rhs)
	{
		return !(lhs == rhs);
	}

	friend inline bool  operator>(const string& lhs, const string& rhs)
	{
		int min;

		if (lhs.size() > rhs.size())
			min = rhs.size();
		else
			min = lhs.size();

		for (int i = 0; i <min; i++)
			if (lhs[i] > rhs[i])
				return true;
			else if (lhs[i] < rhs[i])
				return false;


		return lhs.size() > rhs.size();
	}

	friend inline bool operator<(const string& lhs, const string& rhs)
	{
		int min;
		if (lhs.size() > rhs.size())
			min = rhs.size();
		else
			min = lhs.size();

		for (int i = 0; i < min; i++)
			if (lhs[i] < rhs[i])
				return true;
			else if (lhs[i] > rhs[i])
				return false;


		return lhs.size() < rhs.size();
	}
};

template<class Value, class Key>
class map
{
	int size;

	class Node
	{
	public:
		Value data;
		Key key;
		Node* parent, *lhs, *rhs;
		Node() :
			data(NULL),
			parent(nullptr),
			lhs(nullptr),
			rhs(nullptr)
		{}
		~Node()
		{
			//if (lhs != nullptr)
			//	delete lhs;

			//if (rhs != nullptr)
			//	delete rhs;
		}
	};

	Node* root;

public:
	map() :
		root(nullptr),
		size(0)
	{}

	void add(Value toAdd, Key key)
	{
		if (root != nullptr)
		{
			Node* temp = root;
			do
			{
				if (key == temp->key)
					return;

				else if (key > temp->key)
				{
					if (temp->lhs == nullptr)
					{
						Node* child = new Node();
						size++;
						child->data = toAdd;
						child->key = key;
						child->parent = temp;
						temp->lhs = child;
						break;
					}
					else
						temp = temp->lhs;
				}
				else if (key < temp->key)
				{
					if (temp->rhs == nullptr)
					{
						Node* child = new Node();
						size++;
						child->data = toAdd;
						child->key = key;
						child->parent = temp;
						temp->rhs = child;
						break;
					}
					else
						temp = temp->rhs;
				}
			} while (true);
		}
		else
		{
			root = new Node();
			root->data = toAdd;
			root->key = key;
			size++;
		}
	}

	Value* find(const Key& key)
	{
		if (root != nullptr)
		{
			Node* temp = root;
			do
			{
				if (key == temp->key)
					return &temp->data;
				else if (key > temp->key)
				{
					if (temp->lhs != nullptr)
						temp = temp->lhs;
					else if (temp->rhs != nullptr)
						temp = temp->rhs;
				}
				else if (key < temp->key)
				{
					if (temp->rhs != nullptr)
						temp = temp->rhs;
					else
						temp = temp->lhs;
				}

				if (key == temp->key)
					return &temp->data;
			} while (true);

		}

		return nullptr;
	}

};
int MAX_OPERATION, CURRENT_OPERATION; //TODO: Operation numbers
enum Type
{
	PLUS,
	MINUS,
	NEGATION,

	AND,
	OR,

	EQUAL,
	NOTEQUAL,

	GREATER,
	EGREATER,
	LOWER,
	ELOWER,

	MULTI,
	DIV,
	MOD,

	INTEGER,
	WHITESPACE,

	LBRACKET,
	RBRACKET,

	LPARENT,
	RPARENT,

	ID,
	ASSIGN,

	LOOP,
	CONDITION,

	NONE,
	SEMI,
	END

};

class Token
{
public:
	Type type;
	string value;

	Token() :
		type(NONE),
		value("NUL")
	{}

	int values() const
	{
		//	return std::stoi(value);
		return value.toInt();
	}
	Token(const Type& type, const string& value) :
		type(type),
		value(value)
	{
		//		this->value.fix();
	}

	inline bool operator==(const Token& rhs)
	{
		if (rhs.type == type && rhs.value == value)
			return true;
		else
			return false;

	}

	inline bool operator==(const Type& rhs)
	{
		if (type == rhs)
			return true;
		else
			return false;

	}

	//Token& operator=(Token rhs)
	//{
	//	value = rhs.value;
	//	type = rhs.type;
	//	return *this;
	//}

	inline bool operator!=(const Token& rhs)
	{
		return !(*this == rhs);
	}

	inline bool operator!=(const Type& rhs)
	{
		return !(type == rhs);
	}
};

class Int
{
	bool _isNull;
	int _value;
public:
	Int() :
		_value(0),
		_isNull(true)
	{}

	Int(const int& value) :
		_value(value),
		_isNull(false)
	{}

	Int(const string& value) :
		//_value(std::stoi(value)),
		_value(value.toInt()),
		_isNull(false)
	{}

	//operator bool() const
	//{
	//	return ~_isNull;
	//}
	Int(const Int& value) :
		_value(value._value),
		_isNull(value._isNull)
	{}

	int value() const
	{
		return _value;
	}

	bool isNull() const
	{
		return _isNull;
	}

	Int& operator+(const Int& rhs)
	{
		if (MAX_OPERATION > CURRENT_OPERATION)
		{
			CURRENT_OPERATION++;

			if (!(rhs.isNull() || isNull()))
				_value += rhs.value();
			else
				_isNull = true;
		}

		return *this;
	}

	Int& operator-(const Int& rhs)
	{
		if (MAX_OPERATION > CURRENT_OPERATION)
		{
			CURRENT_OPERATION++;

			if (!(rhs.isNull() || isNull()))
				_value -= rhs.value();
			else
				_isNull = true;
		}

		return *this;
	}

	Int& operator*(const Int& rhs)
	{
		if (MAX_OPERATION > CURRENT_OPERATION)
		{
			CURRENT_OPERATION++;

			if (!(rhs.isNull() || isNull()))
				_value *= rhs.value();
			else
				_isNull = true;
		}

		return *this;
	}

	Int& operator/(const Int& rhs)
	{
		if (MAX_OPERATION > CURRENT_OPERATION)
		{
			CURRENT_OPERATION++;

			if (!(rhs.isNull() || isNull()))
			{
				if (rhs.value() == 0)
					_isNull = true;
				else
					_value /= rhs.value();
			}
			else
				_isNull = true;
		}

		return *this;
	}

	Int& operator%(const Int& rhs)
	{
		if (MAX_OPERATION > CURRENT_OPERATION)
		{
			CURRENT_OPERATION++;

			if (!(rhs.isNull() || isNull()))
				_value %= rhs.value();
			else
				_isNull = true;
		}

		return *this;
	}

	Int& operator==(const Int& rhs)
	{
		if (MAX_OPERATION > CURRENT_OPERATION)
		{
			CURRENT_OPERATION++;

			if (!(rhs.isNull() || isNull()))
			{
				if (_value == rhs.value())
					_value = false;
				else
					_isNull = true;
			}
			else
				_isNull = true;
		}

		return *this;
	}

	Int& operator!=(const Int& rhs)
	{
		if (MAX_OPERATION > CURRENT_OPERATION)
		{
			CURRENT_OPERATION++;

			if (!(rhs.isNull() || isNull()))
			{
				if (_value != rhs.value())
					_value = false;
				else
					_isNull = true;
			}
			else
				_isNull = true;
		}

		return *this;
	}

	Int& operator>(const Int& rhs)
	{
		if (MAX_OPERATION > CURRENT_OPERATION)
		{
			CURRENT_OPERATION++;

			if (!(rhs.isNull() || isNull()))
			{
				if (_value > rhs.value())
					_value = false;
				else
					_isNull = true;
			}
			else
				_isNull = true;
		}

		return *this;
	}

	Int& operator>=(const Int& rhs)
	{
		if (MAX_OPERATION > CURRENT_OPERATION)
		{
			CURRENT_OPERATION++;

			if (!(rhs.isNull() || isNull()))
			{
				if (_value >= rhs.value())
					_value = false;
				else
					_isNull = true;
			}
			else
				_isNull = true;
		}

		return *this;
	}

	Int& operator<(const Int& rhs)
	{
		if (MAX_OPERATION > CURRENT_OPERATION)
		{
			CURRENT_OPERATION++;

			if (!(rhs.isNull() || isNull()))
			{
				if (_value < rhs.value())
					_value = false;
				else
					_isNull = true;
			}
			else
				_isNull = true;
		}

		return *this;
	}

	Int& operator<=(const Int& rhs)
	{
		if (MAX_OPERATION > CURRENT_OPERATION)
		{
			CURRENT_OPERATION++;

			if (!(rhs.isNull() || isNull()))
			{
				if (_value <= rhs.value())
					_value = false;
				else
					_isNull = true;
			}
			else
				_isNull = true;
		}

		return *this;
	}

	Int& operator!()
	{
		if (MAX_OPERATION > CURRENT_OPERATION)
		{
			CURRENT_OPERATION++;

			if (isNull())
			{
				_isNull = false;
				_value = 0;
			}
			else
			{
				_isNull = true;
			}
		}

		return *this;
	}

	Int& operator+()
	{
		if (!(isNull()))
			_value = +value();

		return *this;
	}

	Int& operator-()
	{
		if (!(isNull()))
			_value = -value();

		return *this;
	}

	Int& operator&(const Int& rhs)
	{
		if (MAX_OPERATION > CURRENT_OPERATION)
		{
			CURRENT_OPERATION++;

			if (rhs.isNull() || isNull())
				_isNull = true;
			else
			{
				_value = false;
				_isNull = false;
			}
		}

		return *this;
	}

	Int& operator|(const Int& rhs)
	{
		if (MAX_OPERATION > CURRENT_OPERATION)
		{
			CURRENT_OPERATION++;

			if (rhs.isNull() && isNull())
				_isNull = true;
			else
			{
				_value = false;
				_isNull = false;
			}
		}

		return *this;
	}

	friend std::ostream& operator<<(std::ostream& os, const Int& obj)
	{
		// write obj to stream
		if (obj.isNull())
			std::cout << "Nul";
		else
			std::cout << obj.value();

		return os;
	}
};
//// LEXER///
class Lexer
{
	string input;
	int position, peekPos;
	char currentChar, peekChar;


public:
	Lexer(const string& input) :
		input(input),
		position(0),
		currentChar(input[position])
	{}

	//set char ahead, if End of file then EOF
	void advance()
	{
		position++;

		if (position > input.size() - 1)
			currentChar = EOF;
		else
			currentChar = input[position];
	}

	char peek()
	{
		int peek_pos = position + 1;

		if (peek_pos >= input.size())
			return EOF;
		else
			return input[peek_pos];
	}
	void peekNext()
	{
		peekPos = peekPos + 1;

		if (peekPos >= input.size())
			peekChar = EOF;
		else
			peekChar = input[peekPos];
	}

	char peekCheck()
	{
		int temp = peekPos + 1;

		if (peekPos >= input.size())
			return EOF;
		else
			return input[peekPos];
	}

	Token peekToken()
	{
		peekChar = currentChar;
		peekPos = position + 1;
		while (peekChar != EOF)
		{
			if (isspace(peekChar))
			{
				while (peekChar != EOF && isspace(peekChar))
					peekNext();
			}

			if (isdigit(peekChar))
				return Token(INTEGER, getInt());

			if (isalpha(peekChar))
				return _id();

			switch (peekChar)
			{
			case '+':
				peekNext();
				return Token(PLUS, "+");

			case '-':
				peekNext();
				return Token(MINUS, "-");

			case '!':
				if (peekCheck() == '=')
				{
					peekNext();
					peekNext();
					return Token(NOTEQUAL, "!=");
				}
				else
				{
					peekNext();
					return Token(NEGATION, "!");
				}
			case '%':
				peekNext();
				return Token(MOD, "%");

			case '*':
				peekNext();
				return Token(MULTI, "*");

			case '/':
				peekNext();
				return Token(DIV, "/");

			case '(':
				peekNext();
				return Token(LPARENT, "(");

			case ')':
				peekNext();
				return Token(RPARENT, ")");
			case '{':
				peekNext();
				return Token(LBRACKET, "{");

			case '}':
				peekNext();
				return Token(RBRACKET, "}");
			case ';':
				peekNext();
				return Token(SEMI, ";");

			case '=':
				if (peekCheck() == '=')
				{
					peekNext();
					peekNext();
					return Token(EQUAL, "==");
				}
				else
				{
					peekNext();
					return Token(ASSIGN, "=");
				}

			case '|':
				peekNext();
				return Token(OR, "|");

			case '&':
				peekNext();
				return Token(AND, "&");

			case '@':
				peekNext();
				return Token(LOOP, "@");

			case '?':
				peekNext();
				return Token(CONDITION, "?");

			case '<':
				if (peekCheck() == '=')
				{
					peekNext();
					peekNext();
					return Token(ELOWER, "<=");
				}
				peekNext();
				return Token(LOWER, "<");

			case '>':
				peekNext();
				if (peekCheck() == '=')
				{
					peekNext();
					peekNext();
					return Token(EGREATER, ">=");
				}
				return Token(GREATER, ">");
			default:
				return Token(END, "EOF");
			}
		}

		return Token(END, "EOF");
	}

	//read and return Variable Oken
	Token _id()
	{
		string result;

		while (currentChar != EOF && isalnum(currentChar))
		{
			result += currentChar;
			advance();
		}
		return Token(ID, result);
	}

	void ignoreWhiteSpace()
	{
		while (currentChar != EOF && isspace(currentChar))
			advance();
	}

	//return string of input Integer
	string getInt()	//TODO: Do Own Integer
	{
		string result;

		while (currentChar != EOF && isdigit(currentChar))
		{
			result += currentChar;
			advance();
		}

		return result;
	}

	//Tokenizer
	Token getNextToken()
	{
		while (currentChar != EOF)
		{
			if (isspace(currentChar))
			{
				ignoreWhiteSpace();
				continue;
			}

			if (isdigit(currentChar))
				return Token(INTEGER, getInt());

			if (isalpha(currentChar))
				return _id();

			switch (currentChar)
			{
			case '+':
				advance();
				return Token(PLUS, "+");

			case '-':
				advance();
				return Token(MINUS, "-");

			case '!':
				if (peek() == '=')
				{
					advance();
					advance();
					return Token(NOTEQUAL, "!=");
				}
				else
				{
					advance();
					return Token(NEGATION, "!");
				}
			case '%':
				advance();
				return Token(MOD, "%");

			case '*':
				advance();
				return Token(MULTI, "*");

			case '/':
				advance();
				return Token(DIV, "/");

			case '(':
				advance();
				return Token(LPARENT, "(");

			case ')':
				advance();
				return Token(RPARENT, ")");
			case '{':
				advance();
				return Token(LBRACKET, "{");

			case '}':
				advance();
				return Token(RBRACKET, "}");
			case ';':
				advance();
				return Token(SEMI, ";");

			case '=':
				if (peek() == '=')
				{
					advance();
					advance();
					return Token(EQUAL, "==");
				}
				else
				{
					advance();
					return Token(ASSIGN, "=");
				}

			case '|':
				advance();
				return Token(OR, "|");

			case '&':
				advance();
				return Token(AND, "&");

			case '@':
				advance();
				return Token(LOOP, "@");

			case '?':
				advance();
				return Token(CONDITION, "?");

			case '<':
				if (peek() == '=')
				{
					advance();
					advance();
					return Token(ELOWER, "<=");
				}
				advance();
				return Token(LOWER, "<");

			case '>':
				advance();
				if (peek() == '=')
				{
					advance();
					advance();
					return Token(EGREATER, ">=");
				}
				return Token(GREATER, ">");
			case '\0':
				return Token(END, "EOF");
			default:
				continue;
			}
		}

		return Token(END, "EOF");
	}
};

////TOKENS////
class AST
{
public:
	AST(const Token& token) :
		token(token) {}
	virtual ~AST() {}

	Token token;
	virtual Int visit() = 0;
};

class Compound :
	public AST
{
	vector<AST*> children;

public:
	Compound() :
		AST(Token(NONE, "NONE"))
	{}

	~Compound()
	{
		for (AST** it = children.begin(); it != children.end(); it++)
			delete *it;
	}
	void addNode(AST* node)
	{
		children.push_back(node);
	}

	Int visit() override
	{
		for (AST** it = children.begin(); it != children.end(); it++)
			(*it)->visit();

		return 1;
	}
};


//std::map<string, Int> varContainer;
map<Int, string> varContainer;
class Variable :
	public AST, Int
{
public:
	const string name;
	Variable(const Token& token) :
		AST(token),
		name(token.value)
	{
		//varContainer.insert(std::pair<string, Int>(name, Int()));
		varContainer.add(Int(), name);
	}

	Int visit() override
	{
		return *varContainer.find(name); //[name];
	}
};

class Condition : //TODO: Condition
	public AST
{
	AST* condition;
	AST* exp;

public:
	Condition(AST* condition, const Token& token, AST* exp) :
		AST(token),
		condition(condition),
		exp(exp)
	{}
	~Condition()
	{
		delete condition, exp;
	}
	Int visit() override
	{
		if (CURRENT_OPERATION < MAX_OPERATION)
		{
			Int isTrue = condition->visit();

			CURRENT_OPERATION++;

			if (CURRENT_OPERATION < MAX_OPERATION && !isTrue.isNull())
				exp->visit();
		}
		return 0;
	}

};

class Loop : // TODO: Loop
	public AST
{
	AST* condition;
	AST* exp;

public:
	Loop(AST* condition, const Token& token, AST* exp) :
		AST(token),
		condition(condition),
		exp(exp)
	{}

	~Loop()
	{
		delete condition, exp;
	}
	Int visit() override
	{
		if (CURRENT_OPERATION < MAX_OPERATION)
		{
			CURRENT_OPERATION++;

			while (!condition->visit().isNull())
			{
				if (CURRENT_OPERATION >= MAX_OPERATION)
					return 1;

				exp->visit();

				if (CURRENT_OPERATION >= MAX_OPERATION)
					return 1;

				CURRENT_OPERATION++;
			}
		}

		return 1;
	}
};
class Assign :
	public AST
{
	Variable* var;
	AST* exp;

public:
	Assign(Variable* var, const Token& token, AST* exp) :
		AST(token),
		var(var),
		exp(exp)
	{}
	~Assign()
	{
		delete var, exp;
	}
	Int visit() override
	{
		Int temp;
		if (MAX_OPERATION > CURRENT_OPERATION)
			temp = exp->visit();
		if (MAX_OPERATION > CURRENT_OPERATION)
		{
			*(varContainer.find(var->name)) = temp;
			CURRENT_OPERATION++;
		}

		return temp;
	}
};

class NoOp :
	public AST
{
public:
	NoOp() :
		AST(Token(NONE, "NONE"))
	{}
	~NoOp()
	{
	}
	Int visit() override
	{
		return 1;
	}
};

class BinOp :
	public AST
{
	AST* left, *right;

public:
	BinOp(AST* left, const Token& token, AST* right) :
		AST(token),
		left(left),
		right(right)
	{}

	~BinOp()
	{
		delete left, right;
	}
	Int visit() override
	{
		switch (token.type)
		{
		case PLUS:
			return left->visit() + right->visit();
		case MINUS:
			return left->visit() - right->visit();
		case MULTI:
			return left->visit() * right->visit();
		case DIV:
			return left->visit() / right->visit();
		case MOD:
			return left->visit() % right->visit();
		default:
			throw;
		}
	}
};

class EqualOp :
	public AST
{
	AST* left, *right;

public:
	EqualOp(AST* left, const Token& token, AST* right) :
		AST(token),
		left(left),
		right(right)
	{}
	~EqualOp()
	{
		delete left, right;
	}
	Int visit() override
	{
		switch (token.type)
		{
		case EQUAL:
			return left->visit() == right->visit();
		case NOTEQUAL:
			return left->visit() != right->visit();
		default:
			throw;
		}
	}
};

class AndOrOp :
	public AST
{
	AST* left, *right;

public:
	AndOrOp(AST* left, const Token& token, AST* right) :
		AST(token),
		left(left),
		right(right)
	{}
	~AndOrOp()
	{
		delete left, right;
	}
	Int visit() override
	{
		switch (token.type)
		{
		case AND:
			return left->visit() & right->visit();
		case OR:
			return left->visit() | right->visit();
		default:
			throw;
		}
	}
};

class GreaterOp :
	public AST
{
	AST* left, *right;

public:
	GreaterOp(AST* left, const Token& token, AST* right) :
		AST(token),
		left(left),
		right(right)
	{}
	~GreaterOp()
	{
		delete left, right;
	}
	Int visit() override
	{
		switch (token.type)
		{
		case GREATER:
			return left->visit() > right->visit();
		case EGREATER:
			return left->visit() >= right->visit();
		case LOWER:
			return left->visit() < right->visit();
		case ELOWER:
			return left->visit() <= right->visit();
		default:
			throw;
		}
	}
};

class INT :
	public AST
{
	int value;
public:
	INT(const Token& token) :
		AST(token),
		value(token.values())
	{}

	Int visit()  override
	{
		return token.values();
	}
};

class UnaryOp :
	public AST
{
	AST* exp;
public:
	UnaryOp(const Token& token, AST* exp) :
		exp(exp),
		AST(token)
	{}
	~UnaryOp()
	{
		delete exp;
	}
	Int visit()  override
	{
		switch (token.type)
		{
		case PLUS:
			return +exp->visit();
		case MINUS:
			return -exp->visit();
		case NEGATION:
			return !exp->visit();
		default:
			throw;
		}
	}

};

/// PARSER////
class Parser
{
	Token currentToken;
	Lexer& lexer;


	//Check currentToken with Excepted, if equal getNextToken else throw exception
	void eat(const Type& excepted)
	{
		if (excepted == currentToken.type)
			currentToken = lexer.getNextToken();
	}

public:
	Parser(Lexer& lexer) :
		lexer(lexer)
	{
		currentToken = lexer.getNextToken();
	}

	// return next factor(INTEGER)
	AST* factor()
	{
		Token token = currentToken;

		switch (token.type)
		{
		case INTEGER:
			eat(INTEGER);
			return new INT(token);

		case MINUS:
			eat(MINUS);
			{
				if (currentToken == ID)
					CURRENT_OPERATION++;
			}
			return new UnaryOp(token, factor());

		case PLUS:
			eat(PLUS);
			return new UnaryOp(token, factor());

		case NEGATION:
			eat(NEGATION);
			return new UnaryOp(token, factor());

		case LPARENT:
		{
			eat(LPARENT);
			AST* node;

			if (currentToken == LPARENT)
				eat(LPARENT);

			if (currentToken == ID && lexer.peekToken() == ASSIGN)
				node = assignment_statement();
			else
				node = andOr();// exp();

			eat(RPARENT);

			if (currentToken == LPARENT)
				eat(RPARENT);
			return node;
		}
		default:
			return variable();
		}
	}

	// Gramar for MULTIiply  & Divide
	AST* term()
	{
		AST* node = factor();

		while (currentToken.type == MULTI || currentToken.type == DIV || currentToken.type == MOD)
		{
			const Token token = currentToken;
			if (token.type == MULTI)
				eat(MULTI);
			else if (token.type == DIV)
				eat(DIV);
			else if (token.type == MOD)
				eat(MOD);

			node = new BinOp(node, token, factor());
		}
		return node;
	}

	// Grammar for Addition, Substraction
	AST* exp()
	{
		AST* node = term();

		while (currentToken.type == PLUS || currentToken.type == MINUS)
		{
			const Token token = currentToken;
			if (token.type == PLUS)
				eat(PLUS);
			else if (token.type == MINUS)
				eat(MINUS);

			node = new BinOp(node, token, term());
		}

		return node;
	}

	// Grammar for > >= <= <
	AST* greaterExp()
	{
		AST* node = exp();

		while (currentToken.type == GREATER || currentToken.type == LOWER || currentToken.type == EGREATER || currentToken.type == ELOWER)
		{
			const Token token = currentToken;

			if (token.type == GREATER)
				eat(GREATER);
			else if (token.type == EGREATER)
				eat(EGREATER);
			else if (token.type == LOWER)
				eat(LOWER);
			else if (token.type == ELOWER)
				eat(ELOWER);

			node = new GreaterOp(node, token, exp());
		}

		return node;
	}

	// Grammar for == !=
	AST* equalExp()
	{
		AST* node = greaterExp();

		while (currentToken.type == EQUAL || currentToken.type == NOTEQUAL)
		{
			const Token token = currentToken;

			if (token.type == EQUAL)
				eat(EQUAL);
			else if (token.type == NOTEQUAL)
				eat(NOTEQUAL);

			node = new EqualOp(node, token, greaterExp());
		}

		return node;
	}

	// Grammar for | &
	AST* andOr()
	{
		AST* node = equalExp();

		while (currentToken.type == OR || currentToken.type == AND)
		{
			const Token token = currentToken;
			if (token.type == OR)
				eat(OR);
			else if (token.type == AND)
				eat(AND);

			node = new AndOrOp(node, token, equalExp());
		}

		return node;
	}

	Compound* compound_statement()
	{
		eat(LBRACKET);

		vector<AST*> nodes = statementList();

		eat(RBRACKET);

		if (currentToken == INTEGER)
			eat(INTEGER);

		Compound* root = new Compound();

		for (AST** node = nodes.begin(); node != nodes.end(); node++)
			root->addNode(*node);

		return root;
	}

	Compound* compound_program()
	{
		vector<AST*> nodes = statementList();

		Compound* root = new Compound();

		for (AST** node = nodes.begin(); node != nodes.end(); node++)
			root->addNode(*node);

		return root;
	}
	vector<AST*> statementList()
	{
		AST* node = statement();

		vector<AST*> results;
		results.push_back(node);

		while (currentToken == ID || currentToken == INTEGER || currentToken == LOOP || currentToken == CONDITION || currentToken == LPARENT)
			results.push_back(statement());

		return results;
	}

	AST* statement()
	{
		AST* node;

		if (currentToken == LBRACKET)
			node = compound_statement();
		else
			if (currentToken == ID)
				node = assignment_statement();
			else if (currentToken == LOOP)
				node = loop_statement();
			else if (currentToken == CONDITION)
				node = condition_statement();
			else if (currentToken == INTEGER)
				node = andOr();
			else if (currentToken == LPARENT)
			{
				eat(LPARENT);
				node = statement();
			}
			else
				node = empty();

		if (currentToken == RPARENT)
			eat(RPARENT);

		return node;
	}

	// create Assign node from Var=exp
	Assign* assignment_statement()
	{
		stack<Variable*> varStack;
		AST* right;
		Token token(ASSIGN, "=");

		do
		{
			varStack.push(variable());
			eat(ASSIGN);
		} while (currentToken == ID && lexer.peekToken() == ASSIGN);

		right = andOr();

		do
		{
			right = new Assign(varStack.top(), token, right);
			varStack.pop();
		} while (!varStack.empty());

		return dynamic_cast<Assign*>(right);
	}

	Loop* loop_statement()
	{
		Token token(currentToken);
		eat(LOOP);

		AST* cond = andOr();

		AST* right = compound_statement();

		return new Loop(cond, token, right);
	}

	Condition* condition_statement()
	{
		Token token(currentToken);
		eat(CONDITION);

		AST* cond = andOr();

		//	AST* right = exp();
		AST* right = compound_statement();

		return new Condition(cond, token, right);
	}
	//create Var from currentToken, and eat Token
	Variable* variable()
	{
		Variable* node = new Variable(currentToken);

		eat(ID);
		return node;
	}
	NoOp* empty()
	{
		return new NoOp();
	}
	AST* parse()
	{
		AST* node = program();

		return node;
	}

	AST* program()
	{
		AST* node = compound_program();
		eat(END);
		return node;
	}
};

class Interpreter
{
	Parser& parser;
public:
	Interpreter(Parser& parser) :
		parser(parser)
	{}

	void interpret()
	{
		AST* tree = parser.parse();
		tree->visit();
		delete tree;
	}
};

vector<string>& split(const string& toSplit)
{
	vector<string> result;

	string temp;

	for (int i = 0; i<toSplit.size(); i++)
	{
		if (!isalpha(toSplit[i]))
		{
			result.push_back(temp);
			temp.clear();
		}
		else
		{
			char k = toSplit[i];
			if (isspace(k) || k == EOF)
				continue;
			temp += k;
		}
	}

	if (!temp.empty())
		result.push_back(temp);

	return result;
}
char temped[1000];
int main()
{
	string input, toPrint;
	CURRENT_OPERATION = 0;
	std::ios_base::sync_with_stdio(false);
	std::cin >> MAX_OPERATION;
	char p = std::cin.get();

	while (isspace(p))
		p = std::cin.get();

	std::cin.unget();


	std::cin.getline(temped, 1000);

	toPrint = string(temped);


	while (isspace(p))
		p = std::cin.get();

	std::cin.unget();

	while (std::cin.good())
	{
		std::cin.getline(temped, 1000);

		input += '\n';
		input+=(temped);
	}

	vector<string> result;
	result = split(toPrint);
	for (int i = 0; i<result.size(); i++)
		varContainer.add(Int(), result[i]);

	Lexer lexer(input);
	Parser parser(lexer);
	Interpreter interpreter(parser);
	interpreter.interpret();

	std::cout << CURRENT_OPERATION;

	for (int i = 0; i<result.size(); i++)
		std::cout << std::endl << result[i] << ' ' << *varContainer.find(result[i]);

	return 0;
}
