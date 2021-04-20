## 정리

-----
* String 특징
    * String객체는 수정불가 
    * ""로 할당하면 안의 값이  같은경우 같은 메모리를 가르킨다
<pre><code>

public class StringEx {
	public static String midStr(String s) {
		String ret;
		int len = s.length();
		int i = len/2;
		if (len%2==0) 
		{
			ret = s.substring(i-1,i+1);
		}else {ret = s.substring(i, i+1);}
		return ret;
	}
	public static String reverseString(String s) {
		int j = s.length();
		char[] ret = new char[j];
		char[] ss = s.toCharArray();
		StringBuffer b = new StringBuffer();
		for(int i =0; i<j;i++) 
		{
			ret[i]=ss[j-i-1];
			
		}
		b.append(ret);
		return b.toString();
	} 
	public static String convertString(String s) {
		int j = s.length();
		char[] ret = new char[j];
		char[] ss = s.toCharArray();
		StringBuffer b = new StringBuffer();
		for(int i =0; i<j;i++) 
		{
			if((int)ss[i]>=97) 
			{
				int buf =(int)ss[i]-32;
				ret[i]=(char)buf;
			}else 
			{
				int buf =(int)ss[i]+32;
				ret[i]=(char)buf;
			
			}
			
		}
		b.append(ret);
		return b.toString();
	}
	
	public static void main(String[] args)
	{ 
		System.out.println(StringEx.midStr("abcd"));
		System.out.println(StringEx.midStr("abcde"));
	    System.out.println(StringEx.reverseString("abcdef")); 
	    System.out.println(StringEx.convertString("aBcd"));
	 }
	}


</code></pre>
