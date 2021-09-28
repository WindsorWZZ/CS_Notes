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

## std::algorithm
### comparator
Write a custom comparator for different class, using in sort().  
```C++
struct Node {
    int i;
    double d;
    Node(int I, int D): i(I), d(D) {}
};

Class Solution {
    static bool compare(const Node* a, const Node* b) {
        // Increasing order in sort();
        return a->i < b->i;
    }

    // For pq, implement a type and overload "()" as compare function
    // () implements "greater", pq is min-heap
    struct comp {
        bool operator()(Node* a, Node* b) {
            return a->i > b->i;
        }
    }

    void mySort(vector<int>& ivec, vector<double>& dvec) {
        vector<Node*> res(ivec.size(), nullptr);
        for (int i = 0; i < ivec.size(); ++i) {
            Node* node = new Node(ivec[i], dvec[i]);
            res[i] = node;
        }
        sort(res.begin(), res.end(), compare);
        for (Node* node : res) {
            cout << node->i << " " << node->d << endl;
        }
    }

    void pqSort(vector<int>& ivec, vector<double>& dvec) {
        priority_queue<Node*, vector<Node*>, comp> pq;
        for (int i = 0; i < ivec.size(); ++i) {
            Node* node = new Node(ivec[i], dvec[i]);
            pq.push(node);
        }
        while (!pq.empty()) {
            cout << pq.top()->i << " " << pq.top()->d << endl;
            pq.pop();
        }
    }
}

int main() {
    Solution s;
    vector<int> ivec = {1,2,5,8,0};
    vector<double> dvec = {9,2,1,3,6};
    s.mySort(ivec, dvec);
    s.pqSort(ivec,dvec);
}
```
