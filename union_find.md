## Union Find



```c++
class UnionFind {
    public:
        UnionFind(int n) {
            parent = vector<int>(n, -1);
            for (int i = 0; i < n; i++) {
                parent[i] = i;
            }
            size = vector<int>(n, 1);
            count = n;
        }
        
        bool connected(int p, int q) {
            return getParent(p) == getParent(q);
        }
        
        void merge(int p, int q) {
            int pRoot = getParent(p);
            int qRoot = getParent(q);
            
            if (pRoot == qRoot) 
                return;
            
            if (size[pRoot] > size[qRoot]) {
                parent[qRoot] = pRoot;
                size[pRoot] += size[qRoot];
            } else {
                parent[pRoot] = qRoot;
                size[qRoot] += size[pRoot];
            }
            count --;
        }
        
        int getParent(int q) {
            while (parent[q] != q) {
                parent[q] = parent[parent[q]];
                q = parent[q];
            }
            return q;
        }
        
        int getNumGroup() {
            return count;
        }
        
    private:
        vector<int> parent;
        vector<int> size;
        int count;
};
```

