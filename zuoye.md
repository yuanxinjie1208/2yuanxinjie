###9.1

(a)list，因为可能需要在容器的中间位置插入元素

(b)deque，因为需要在头部进行元素的删除，deque效率更高

(c)vector，无具体的删除插入操作，未知数量，vector是个不错的选择

###9.20

```
#include<iostream>

#include<fstream>

#include<sstream>

#include<string>

#include<vector>

#include<list>

#include<deque>

using namespace std;

int main(int argc, char**argv)

{	

    list<int> list1(5,7);	
    
    deque<int> deque1;	
    
    deque<int> deque2;	
    
    list<int>::iterator it1 = list1.begin();	
    
    for (it1; it1 != list1.end(); it1++)
    
    {		
    
        if ((*it1)%2 == 0)
        
        {			
        
            deque1.push_back(*it1);	
            
        } 	
        
        else
        
        {		
        
            deque2.push_back(*it1);		
            
        }	
        
    } 	
    
    deque<int>::iterator it2 = deque1.begin();
    
    deque<int>::iterator it3 = deque2.begin();	
    
    cout<<"偶数为：";	
    
    for (it2; it2 != deque1.end(); it2++)	
    
    {		
    
        cout<<*it2<<" ";	
        
    }	
    
    cout<<endl;	cout<<"奇数为：";	
    
    for (it3; it3 != deque2.end(); it3++)	
    
    {		
    
        cout<<*it3<<" ";	
        
    }		
    
    return 0;
    
}
```

###9.29

resize(100)会将其大小改为100个元素的大小，添加新元素并初始化，之后使用resize(10)会将之后的90个元素舍弃

###9.43

```
#include<iostream>
#include<fstream>
#include<sstream>
#include<string>
#include<vector>
#include<forward_list>
using namespace std; 
void func(string &s, string &oldVal, string &newVal)
{	
    int _size = oldVal.size();	
    string::iterator it1 = s.begin();	
    string::iterator it2 = newVal.begin();	
    string::iterator it3 = newVal.end(); 	 
    for (it1; it1 <= (s.end()-oldVal.size()+1); ++it1)	
        {			
            if((s.substr(it1-s.begin(),_size) == oldVal))		
            {			
                it1 = s.erase(it1,it1+_size);
                it1 = s.insert(it1, it2, it3);			
                advance(it1,_size);		
            }	
        }
} 
int main(int argc, char**argv)
{	
    string s = "abcdefg";	
    string oldval = "bc";	
    string newval = "asas";	
    func(s,oldval,newval);	
    cout<<s<<endl;	
    return 0;
}
```

###9.52

```
#include <iostream>
#include <stack>
using namespace std; 
int main(int argc, char *argv[])
{    
    const string expr = "a()a(aaa(aaa(a)))aa()";    
    const char placehold = '#';    
    int num = 0;      
    stack<char> stk;    
    for (auto c : expr)    
    {        
        stk.push(c);        
        if (c == '(')            
                ++num;        
        if (num && c == ')')
        {            
            while (stk.top() != '(')                
                   stk.pop();            
            stk.pop();            
            stk.push(placehold);            
            --num;        
        }    
    }    
    string s;    
    while(!stk.empty())    
    {        
        s.insert(s.begin(),stk.top());        
        stk.pop();    
    }    
    cout << s << endl;    
    return 0;
}
```

###10.3

```
#include<iostream>
#include<string>
#include<vector>
#include<algorithm>
#include<numeric>
using namespace std; 
int main(int argc, char**argv)
{	
    int a[10] = {0,1,2,5,4,5,4,5,4,5};	
    vector<int> vec(a,a+10);	
    cout<<"元素之和为："<<accumulate(vec.begin(),vec.end(),0); 	
    return 0;
}
```

###10.15
int p=10;

auto  f[p](int a){return a+p;}

cout<<f(6)<<endl;

###10.34

```
#include<iostream>
#include<string>
#include<vector>
#include <algorithm>
#include<list>
using namespace std;
int main()
{
vector<int>aa;
    int q=5;
    while(q--)
    {
        int t;cin>>t;
        aa.push_back(t);
    }
    vector<int>::reverse_iterator it1=aa.rbegin();
    vector<int>::reverse_iterator it2=aa.rend();
    while(it1!=it2)
    {
        cout<<*it1<<endl;++it1;
    }
    return 0;
}
```

###10.42

```#include<iostream>  
#include<fstream>
#include<string>  
#include<vector> 
#include<list>
#include<algorithm>  
#include<numeric>  
#include<functional>
#include<iterator>
using namespace std;
using namespace placeholders; 
int main(int argc, char**argv)  
{ 	
    string a[10] = {"sdc","sddc","sdec","sfdc","sdec","sdc","sdc","fsdc","sadc","fsdc"};	
    list<string> list1(a,a+10);	
    list1.sort();	
    list1.unique();	
    for (auto it1 = list1.begin(); it1 != list1.end(); ++it1)	
    {		
        cout<<*it1<<" ";	
    } 	
    return 0; 
}
```

###11.12

```
#include<iostream>  
#include<string>  
#include<fstream>
#include<list>
#include<vector>
 #include<map>  
 #include<set>#include<cctype>
 #include<algorithm>
 #include<utility>
 using namespace std; 
 int main(int argc, char**argv)  
 { 	
     vector<pair<string,int>> vec1(12);
     ifstream in1("1.txt");	
     string str;	
     size_t i = 0;	
     while (in1>>str)	
     {		
        vec1[i].first = str;		
        ++i;	
    }	
    ifstream in2("2.txt");	
    int val;	
    size_t j = 0;	
    while (in2>>val)	
    {		
        vec1[j].second = val;		
        ++j;	
    } 	
    vector<pair<string,int>>::iterator it1 = vec1.begin();	
    cout<<"vector中元素为："<<endl;
    for (it1; it1 != vec1.end(); ++it1)	
    {		
        cout<<it1->first<<" "<<it1->second<<endl;	
    } 	
    return 0;  
}  
```

###11.17

第3个调用不合理，back_inserter()需要使用push_back()。

###11.38

```
#include <unordered_map>

#include <set>

#include <string>

#include <iostream>

#include <fstream>

#include <sstream>

 

using std::string;

 

void wordCounting()

{

    std::unordered_map<string, size_t> word_count;

    for (string word; std::cin >> word; ++word_count[word])

        ;

    for (const auto& w : word_count)

        std::cout << w.first << " occurs " << w.second

                  << (w.second > 1 ? "times" : "time") << std::endl;

}

 

void wordTransformation()

{

    std::ifstream ifs_map("../data/word_transformation.txt"),

        ifs_content("../data/given_to_transform.txt");

    if (!ifs_map || !ifs_content) {

        std::cerr << "can't find the documents." << std::endl;

        return;

    }

 

    std::unordered_map<string, string> trans_map;

    for (string key, value; ifs_map >> key && getline(ifs_map, value);)

        if (value.size() > 1)

            trans_map[key] =

                value.substr(1).substr(0, value.find_last_not_of(' '));

 

    for (string text, word; getline(ifs_content, text); std::cout << std::endl)

        for (std::istringstream iss(text); iss >> word;) {

            auto map_it = trans_map.find(word);

            std::cout << (map_it == trans_map.cend() ? word : map_it->second)

                      << " ";

        }

}

 

int main()

{

    // wordCounting();

    wordTransformation();

}
```

###13.12

析构函数执行三次：accum，item1，item2

###13.18

```
#include<iostream>  
#include<string>  
#include<fstream>
#include<list>
#include<vector> 
#include<map>  
#include<set>#include<cctype>
#include<algorithm>#include<utility>
#include<memory>
using namespace std;
class Employee
{
    public:	
        Employee();
        Employee(string& s);	
        Employee(const Employee&) =delete;
        Employee& operator= (const Employee&) =delete;	
        int number(){return _number;}
    private:	
        string employee;	
        int _number;	
        static int O_number
}; 
int Employee::O_number = 0;
Employee::Employee()
{	
    _number = O_number++;
}
Employee::Employee(string& s)
{	
    employee = s;	
    _number = O_number++;
} 
void show(Employee a)
{	
    cout<<a.number()<<endl;
}
int main(int argc, char**argv)  
{	
    Employee a, b, c;	
    show(a);	
    show(b);	
    show(c); 	
    return 0;
} 
```

###13.46

(a)：f()为函数的返回值，临时值，属于右值，&&

(b)：vi[0]为变量，属于左值，&

(c)：r1为变量，属于左值，&

(d)：右侧为表达式，属于右值，&&

###13.49

```
String& String::operator=(String&& rhs) NOEXCEPT
{	
    if (this != &rhs) 
    {		
        free();		
        elements = rhs.elements;		
        end = rhs.end;		
        rhs.elements = rhs.end = nullptr;	
    }
    return *this;
}
String::String(String&& s) NOEXCEPT : elements(s.elements), end(s.end)
{	
    s.elements = s.end = nullptr;
}
```

###13.58

```
#include <vector>
#include <iostream>
#include <algorithm>
 using std::vector;
 using std::sort; 
 class Foo 
 {
     public:	
         Foo sorted()&&;	
         Foo sorted() const&; 
     private:	
         vector<int> data;
 }; 
 Foo Foo::sorted() &&
 {	
     sort(data.begin(), data.end());	
     std::cout << "&&" << std::endl; 	
     return *this;
 } 
 Foo Foo::sorted() const &
 {	 	
     std::cout << "const &" << std::endl;     
     return Foo(*this).sorted(); 
 } 
 int main()
 {	
     Foo().sorted(); 	
     Foo f;	
     f.sorted(); 
 }
```

###14.3

(a)应用了C++内置版本的==，比较两个指针

(b) 应用了string版本的==

(c)应用了vector版本的==

(d)应用了string版本的==

###14.20

```
class Sales_data
{	
    friend Sales_data operator+(const Sales_data &lhs, const Sales_data &rhs);
    public:	
        Sales_data& operator+=(const Sales_data &rhs);	
};
Sales_data operator+(const Sales_data &lhs, const Sales_data &rhs)
{	
    Sales_data sum = lhs;	
    sum += rhs;	return sum;
}
Sales_data& Sales_data::operator+=(const Sales_data &rhs)
{	
    units_sold += rhs.units_sold;	
    revenue += rhs.revenue;
    return *this;
}
```

###14.38

```
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
using std::istream;
using std::cout;
using std::cin;
using std::endl;
using std::vector;
using std::string; 
class StrLenIs
{
    public:	
        StrLenIs(int len) : len(len) { }	
        bool operator()(const string &str) 
        { 
            return str.length() == len; 
        } 
    private:	
        int len;
}; 
void readStr(istream &is, vector<string> &vec)
{
    	string word;	
    	while (is >> word)	
        {		
            vec.push_back(word);	
        }
} 
int main()
{	
    vector<string> vec;	
    readStr(cin, vec);	
    const int minLen = 1;	
    const int maxLen = 10;	
    for (int i = minLen; i <= maxLen; ++i)	
    {		
        StrLenIs slenIs(i);		
        cout << "len: " << i << ", cnt: " << count_if(vec.begin(), vec.end(), slenIs) << endl;	
    } 	
    return 0;
}
```

###14.52

```
struct longDouble 
{		
    longDouble operator+(const SmallInt&);	
};
longDouble operator+(longDouble&, double);
SmallInt si;
longDouble ld;
ld = si + ld;
ld = ld + si;
```

###15.12

override是表示对其基类函数的覆盖，final是表示此函数不能再被其他的函数所覆盖

###15.16

```
class limit_quote : public Disc_quote
{
    public:	limit_quote();	
    limit_quote(const string&book, double price, size_t qty,double disc):Disc_quote(book,price,qty,disc){}	
    double net_price(size_t n) const	
    {		
        if (n > quantity)		
        {			
            return quantity*(1-_discount)*price+(n-quantity)*price;		
        } 		
        else		
        {			
            return quantity*(1-_discount)*price;		
        }	
    }
};
```

###15.30

```
class Basket
{
    public:	
        void add_item(const std::shared_ptr<Quote> &sale) 
        { 
            items.insert(sale); 
        }	
        double total_receipt(std::ostream&) const;
    private:	
        static bool compare(const std::shared_ptr<Quote> &lhs, const std::shared_ptr<Quote> &rhs)	
        {		
            return lhs->isbn() < rhs->isbn();	
        }	
        std::multiset<std::shared_ptr<Quote>, decltype(compare)*> items{compare};
}; 
double Basket::total_receipt(ostream &os) const
{	
    double sum = 0.0;	
    for(auto iter = items.cbegin(); iter != items.cend(); iter = items.upper_bound(*iter))	
    {		
        sum += print_total(os, **iter, items.count(*iter));	
    }	
    os << "Total Sale: " << sum << endl;	
    return sum;
}
```









