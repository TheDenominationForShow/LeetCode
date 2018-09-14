
>create by jzf@2018/09/14
## 191. 位1的个数@2018/09/14
```c++
class Solution {
public:
    int hammingWeight(uint32_t n) {
      int ret =0;
      for(size_t i=0;i<32;i++)   
      {
          uint32_t tmp =(1<<i);
          if(tmp>n)
          {
              break;
          }
          if(tmp&n)
          {
              ret ++;
          }
      }
        return ret;
    }
};
```

### 优解
```c++
class Solution {
public:
    int hammingWeight(uint32_t n){
       int res = 0;
       for(int i=0;i<32;++i)
       {
           res+=(n&1);
           n = n>>1;
       }
       return res;
    }
};
```
### 总结
1，本质上没啥问题，但是没说不能修改n啊