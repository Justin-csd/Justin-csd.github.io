# 代码片段

**由于特别的长，我们只展示一部份。**

**这些内容特别的重要，**~~**对于OIER来说。**~~

---

## 用法说明

如果你想快速读入，可以使用这个函数：

```cpp
inline int read(){
    int x=0,f=1;char ch=getchar();
    while(ch<'0'||ch>'9'){if(ch=='-')f=-1;ch=getchar();}
    while(ch>='0'&&ch<='9'){x=x*10+ch-'0';ch=getchar();}
    return x*f;
}
```

用法是这样的：

```cpp
int n=read();
```

或者也可以使用这个函数：

```cpp
namespace AK_IOI {
    template<class T> void to_read(T &x) {
        char ch=getchar();
        while(ch<'0'||ch>'9') ch=getchar();
        while(ch>='0'&&ch<='9') x=x*10+ch-'0',ch=getchar();
    }
    template<class T> void to_write(T x) {
        if(x<0) putchar('-'),x=-x;
        if(x>9) to_write(x/10);
        putchar(x%10+'0');
    }
}
```

用法如此：

```cpp
int n;
to_read(n);//假设输入了5
to_write(n);//输出的就是5
```

---

下面是其他的实用功能，自行阅览，不多说明。

```cpp
struct tree_Node{ int l,r; int sum; };
struct map_Node{ int x,y; bool operator < (const map_Node &a) const{ return x<a.x; } };
struct cmp{ bool operator ()(const int &a,const int &b){ return a>b; } };
struct cmp2{ bool operator ()(const int &a,const int &b){ return a<b; } };
struct Segment_binary_Tree{ int l,r; int sum; Segment_binary_Tree *lc,*rc; };
struct AVL_Node{ int l,r; int sum; AVL_Node *lc,*rc; int height; };
struct Union_Find_Set{ int fa[1000005]; };
struct Edge_Node{ int u,v,w; int next,to; bool operator < (const Edge_Node &a) const{ return w<a.w; } };
struct Point{ int x,y; };
struct Student{ int id,ch,ma,en; string name; }; //If you want to sort the students by their id, you can use the following code: sort(stu+1,stu+n+1,cmp);
struct BST_Node{ int key; BST_Node *lc,*rc; };//二叉搜索树;

struct Trie_Node{ Trie_Node *next[26]; bool is_end; };//字典树;
struct AC_Automation{ AC_Automation *next[26]; AC_Automation *fail; bool is_end; };//AC自动机;
struct KMP{ int next[1000005]; };//KMP;
struct Manacher{ int p[1000005]; };//Manacher;
struct Suffix_Automation{ int next[26]; int len; int link; };//后缀自动机;
struct Suffix_Array{ int sa[1000005],rk[1000005],height[1000005]; };//后缀数组;
struct Z_Algorithm{ int z[1000005]; };//Z函数;
struct Palindrome_Tree{ int next[26]; int len; int fail; int cnt; };//回文树;
struct Splay_Tree{ int key; Splay_Tree *lc,*rc; };//伸展树;
struct Treap{ int key,priority,size; Treap *lc,*rc; };//平衡树;
struct KD_Tree{ int x,y; KD_Tree *lc,*rc; };//KD树;
struct LCT_Node{ int key; LCT_Node *lc,*rc,*fa; };//Link-Cut树;
struct Segment_Tree{ int l,r; int sum; Segment_Tree *lc,*rc; };//线段树;
struct Heavy_Light_Decomposition{ int l,r; int sum; Heavy_Light_Decomposition *lc,*rc; };//重链剖分;

template<class T> T POW (T b, T p) { T res=1; while(p>0) { if (p&1) res*=b; p >>= (1ll), b*=b; } return res; }
template<class T> T bMOD (T a, T p, T m) { if (p==0) return (T) 1; if (!(p&1)) { T temp=bMOD(a, p/2, m); return ((temp%m)*(temp%m))%m; } return ((a%m)*(bMOD(a, p-1, m)%m))%m; }
template<class T> T inMOD (T a, T m) { return bMOD (a, m-2, m); }
template<class T> bool isPrime (T n) { for (T i=2; i*i<=n; i++) { if (n%i==0) return false; } return true; }
template<class T> T sq (T n) { return (n*n); }
template<class T> T gcd (T a, T b) { return (b==0) ? a : gcd (b, a%b); }
template<class T> T lcm (T a, T b) { return (a/gcd (a, b))*b; }
bool iseq (double a, double b) { return fabs(a-b)<EPS; }
template<class T> T toDeg (T x) { return (180.0*x)/((T)PI); }
template<class T> T toReg (T x) { return (x*(T)PI)/(180.0); }
template<class T> T Inclusion_Exclusion_Principle (T n, T m, T *a) { T res=0; for (T i=1; i<(1<<n); i++) { T cnt=0, temp=1; for (T j=0; j<n; j++) { if (i&(1<<j)) { cnt++; temp*=a[j]; } } if (cnt&1) res+=m/temp; else res-=m/temp; } return res; }
template<class T> double _distance (T x1, T y1, T x2, T y2) { return 1.0*sqrt(sq(x1-x2)+sq(y1-y2)); }
template<class T> void heapify (T *a, int n, int i) { int largest=i; int l=2*i+1; int r=2*i+2; if (l<n && a[l]>a[largest]) largest=l; if (r<n && a[r]>a[largest]) largest=r; if (largest!=i) { swap(a[i], a[largest]); heapify(a, n, largest); } }
template<class T> void heapSort (T *a, int n) { for (int i=n/2-1; i>=0; i--) heapify(a, n, i); for (int i=n-1; i>0; i--) { swap(a[0], a[i]); heapify(a, i, 0); } }//Time Complexity: O(nlogn);
template<class T> void merge (T *a, int l, int m, int r) { int n1=m-l+1; int n2=r-m; T L[n1], R[n2]; for (int i=0; i<n1; i++) L[i]=a[l+i]; for (int i=0; i<n2; i++) R[i]=a[m+1+i]; int i=0, j=0, k=l; while (i<n1 && j<n2) { if (L[i]<=R[j]) a[k++]=L[i++]; else a[k++]=R[j++]; } while (i<n1) a[k++]=L[i++]; while (j<n2) a[k++]=R[j++]; }
template<class T> void mergeSort (T *a, int l, int r) { if (l<r) { int m=l+(r-l)/2; mergeSort(a, l, m); mergeSort(a, m+1, r); merge(a, l, m, r); } }//Time Complexity: O(nlogn);
template<class T> int partition (T *a, int low, int high) { T pivot=a[high]; int i=low-1; for (int j=low; j<high; j++) { if (a[j]<pivot) swap(a[++i], a[j]); } swap(a[i+1], a[high]); return i+1; }
template<class T> void quickSort (T *a, int low, int high) { if (low<high) { int pi=partition(a, low, high); quickSort(a, low, pi-1); quickSort(a, pi+1, high); } }//Time Complexity: O(nlogn);
```

---

## 如果你需要更多或者全部，[点击这个链接。](https://wwm.lanzouq.com/ijUgV2ou6cxi "PressMe")
