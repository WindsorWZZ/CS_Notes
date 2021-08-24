# C++ Standard Library Cheetsheet
## std::string
### string and integer
```
string str = "123";
// string to int
int num = std::stoi(str);
num = std::atoi(str.c_str());
// int to string
string numStr = to_string(num);
```