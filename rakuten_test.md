We consider alphabet with only three lettters:"a", "b" and "c".A string is called diverse
if no three consecutive letters are the same.In other words, a diverse string may bot contain 
any of the string "aaa", "bbb", "ccc".

write a function:
  clase Solution { public String solution(int A, int B, int C); }
  
 that given three integers A, B and C, returns any longest possible diverse string containing at 
 most A letters "a", at most B letters "b", at most C letters "c".If there is no possibility of building any 
 string, return empty string,
 
 Examples:
 
 1. Given A = 6, B = 3 and C = 1, yours function may return "aabaacaa".Note that "aacaabaa" would also be 
    a correct answer. Your function may return any correct answer.
 
 2. Given A = 1, B = 3 and C = 1 yours function may return "abbcb", "bcbab" or any of several other strings.
 
 3.  Given A = 0, B = 1 and C = 8 yours function should return "ccbcc", which is the only correct answer in this case.
 
 
Assume that:

  - N and K are integers within the range [0..100];
  - A + B + C > 0
  
  
  --- 

## Solutions

```
class Main {

  static String solution(int a,int b, int c)
    {
      String str= "";
        if (a==1 && b== 1 && c==1) {
          return "abc";
        }
      int sum = a + b + c; 
      int i = 0; 
      boolean trackA = false;
      boolean trackB = false;
      boolean trackC = false;
      while(i < sum){
        if ((a-2) >= 0 && !trackA) {
            str= str + "aa";
            a= a-2;
            i= i+2;
            trackA = true;
            trackB = false;
            trackC = false;
        }
        else if ((b-2) >= 0 && !trackB) {
            str= str+ "bb";
            b= b-2;
            i= i+2;
            trackA = false;
            trackB = true;
            trackC = false;           
        }
        else if ((c-2) >= 0 && !trackC) {
            str= str+ "cc";
            c= c-2;
            i= i+2;
            trackA = false;
            trackB = false;
            trackC = true;   
        } else if ( a==1) {
            str= str+ "a";
            a--;
            i++;
            trackA = true;
            trackB = false;
            trackC = false; 
        }else if ( b==1) {
            str= str+ "b";
            b--;
            i++;
            trackA = false;
            trackB = true;
            trackC = false; 
        }else if ( c==1) {
            str= str+ "c";
            c--;
            i++;
            trackA = false;
            trackB = false;
            trackC = true; 
        } else {
          i++;
        }
      }
      return str;
    }

  public static void main(String[] args) {
    // String ret = solution(6,3,1);
    // String ret = solution(1,3,1);
    String ret = solution(0,1,8);
    System.out.println(ret);
  }
}
```
