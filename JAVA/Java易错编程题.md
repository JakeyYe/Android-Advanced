# 易错Java编程题
### 一
	public class HelloB {
	    public int add(int a,int b) {
		try {
			return a+b;
		} 
		catch(Exception e){
			System.out.println("here");
		}
		finally {
			// TODO: handle finally clause
			System.out.println("finally");
		}
		return 0;
		
	   }
	   public static void main(String[] args) {
			HelloB test =new HelloB();
			System.out.println("和是："+test.add(9, 34));
	  }
	}
结果为：finally和是：43

	知识点：无论如何try-finally，一定会执行finally中的代码的。

