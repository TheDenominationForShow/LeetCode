>create by jzf@2018/08/29
## 190. 颠倒二进制位@2018/08/29
```c++
class Solution {
public:
    uint32_t reverseBits(uint32_t n) {
        uint32_t tmp=n;
        size_t i=31;
        size_t j=0;
        while(i>j)
        {
            uint32_t t= (1u<<i)&tmp;
            uint32_t r= (1u<<j)&tmp;
           
            if(t >0 && r>0)
            {
                 i--;
                j++;
               continue;
            }
            if(t==0&& r==0)
            {
                 i--;
                 j++;
                continue;
            }
            
            if(t==0)
            {
                tmp =(1u<<i)|tmp;
                tmp =(~r)&tmp;
            }
            else
            {
                tmp =(1u<<j)|tmp;
                tmp =(~t)&tmp;
            }
            i--;
            j++;
            
        }
        return tmp;
    }
};
```

### 优解
```c++
class Solution {
public:
    uint32_t reverseBits(uint32_t n) {
        uint32_t ans=0;
        for( int i=0; i<32; i++ )
        {
            ans <<= 1;
            ans = ans|(n&1);
            n >>= 1;
        }
        return ans;
    }
};
```