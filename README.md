# MyRepository
 public static void main(String[] args) {  
        String str = "abcbec";  
        int maxlen = LongestSubseqWithUniqueChars.solve(str);  
        System.out.println(str,maxlen);  
          
        str = "adabcbec";  
        maxlen = LongestSubseqWithUniqueChars.solve(str);  
        System.out.println(str,maxlen);  
          
        str = "abadadabbc";  
        maxlen = LongestSubseqWithUniqueChars.solve(str);  
        System.out.println(str,maxlen);  
          
        str = "ffdeefghff";  
        maxlen = LongestSubseqWithUniqueChars.solve(str);  
        System.out.println(str,maxlen);  
          
        str = "abcbecghijkl";  
        maxlen = LongestSubseqWithUniqueChars.solve(str);  
        System.out.println(str,maxlen);  
          
    }  
public class LongestSubseqWithUniqueChars {  
  
    public static int solve(String str){  
        int n = str.length();  
        int[] prefixlen=new int[n+1];  
        prefixlen[n] = 0;  
        int[] maxlenstart = new int[n+1];  
        maxlenstart[n] = n;  
        int[] maxlenend = new int[n+1];  
        maxlenend[n] = n-1;  
          
        for(int i=n-1;i>=0;i--){  
            char c = str.charAt(i);  
  
            int j=0,k;  
            for(j=0,k=i+1;j<prefixlen[i+1];j++,k++){  
                if(c == str.charAt(k)){                   
                    break;  
                }  
            }  
            prefixlen[i] = j+1;  
              
            
            maxlenstart[i] = maxlenstart[i+1];  
            maxlenend[i] = maxlenend[i+1];  
            if(maxlenstart[i+1] == i+1){  
                if(prefixlen[i] == prefixlen[i+1] + 1){  
                    maxlenstart[i] = i;  
                }  
            }else{  
               
                if(maxlenend[i] - maxlenstart[i] + 1 < prefixlen[i]){  
                    maxlenstart[i] = i;  
                    maxlenend[i] = i + prefixlen[i] - 1;  
                }  
            }             
        }  
        return maxlenend[0] - maxlenstart[0] + 1;  
    }  
   
  
}  
