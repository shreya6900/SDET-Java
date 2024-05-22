package ThreadDemo;
 
class ThreadDemo extends Thread
{
	private Thread t;
	private String threadName;
 
	//constructor
	ThreadDemo(String name)
	{
		threadName = name;
		System.out.println("Creating "+ threadName);
	}
 
	//run method
	public void run()
	{
		System.out.println("Running "+ threadName);
		try
		{
			for(int i=4;i>0;i--)
			{
				System.out.println("Thread: "+threadName +" Interrupted"+", "+i);
				Thread.sleep(1000);
			}
		}
		catch(InterruptedException e)
		{
			System.out.println("Thread "+threadName+ " interrupted.");	
		}
		System.out.println("Thread "+ threadName+" exiting");
	}
	
	public void start()
	{
		System.out.println("Starting "+threadName);
		if(t==null)
		{
			t = new Thread(this,threadName);
			t.start();
		}
	}
}
 
 
 
public class TestThreadDemo {
 
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		ThreadDemo t1 = new ThreadDemo("Thread-1");
		t1.start();
		ThreadDemo t2 = new ThreadDemo("Thread-2");
		t2.start();
	}
 
}


-------------------------------------------------------------------------------------------------------------------------------------------------------------------

 
package ThreadDemo;
 
class RunnableDemo implements Runnable
{
	private Thread t;
	private String threadName;
 
	//constructor
	RunnableDemo(String name)
	{
		threadName = name;
		System.out.println("Creating "+ threadName);
	}
 
	//run method
	public void run()
	{
		System.out.println("Running "+ threadName);
		try
		{
			for(int i=4;i>0;i--)
			{
				System.out.println("Thread: "+threadName +" Interrupted"+", "+i);
				Thread.sleep(1000);
			}
		}
		catch(InterruptedException e)
		{
			System.out.println("Thread "+threadName+ " interrupted.");	
		}
		System.out.println("Thread "+ threadName+" exiting");
	}
	
	public void start()
	{
		System.out.println("Starting "+threadName);
		if(t==null)
		{
			t = new Thread(this,threadName);
			t.start();
		}
	}
}
 
 
 
public class TestThreadDemo2 {
 
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		RunnableDemo r1 = new RunnableDemo("Thread-1");
		r1.start();
		RunnableDemo r2 = new RunnableDemo("Thread-2");
		r2.start();
	}
 
}
-------------------------------------------------------------------------------------------------------------------------------------------------------------------

package ThreadDemo;
 
class RunnableDemo2 implements Runnable
{
	
	RunnableDemo2()
	{
		System.out.println("Thread: "+Thread.currentThread().getName());
	}
 
	@Override
	public void run() {
		// TODO Auto-generated method stub
		System.out.println("Thread: "+Thread.currentThread().getName());
		for(int i=4;i>0;i--)
		{
			System.out.println("Thread: "+Thread.currentThread().getName()+", "+i);
		}
		System.out.println("Thread: "+Thread.currentThread().getName()+", "+"State:Dead");
	}
	
}
 
public class TestThreadDemo3 {
 
	public static void main(String[] args) throws InterruptedException {
		// TODO Auto-generated method stub
		Thread t1= new Thread(new RunnableDemo2(),"Thread-1");
		Thread t2= new Thread(new RunnableDemo2(),"Thread-2");
		Thread t3= new Thread(new RunnableDemo2(),"Thread-3");
		//start t1 thread
		t1.start();
		t1.join();//join the main thread once t1 has started
		//t2 start when t1 is dead
		t2.start();
		t2.join();
		//t3 will start after t2 is dead
		t3.start();
		
	}	
 
}
 
------------------------------------------------------------------------------------------------------------------------------------------------------------------
