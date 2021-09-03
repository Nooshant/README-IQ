```
import java.util.concurrent.locks.ReentrantLock;
import java.util.concurrent.locks.ReentrantReadWriteLock;
import java.util.concurrent.locks.ReentrantReadWriteLock.ReadLock;
import java.util.concurrent.locks.ReentrantReadWriteLock.WriteLock;

public class Shared {
	
	ReentrantReadWriteLock readWriteLock = new ReentrantReadWriteLock();
	public void m1() {
		//readWriteLock.lock()
		ReadLock lock = readWriteLock.readLock();
		lock.lock();
		//
		
			WriteLock lock1 = readWriteLock.writeLock();
			lock1.lock();
		    //
			lock1.unlock();
			
		lock.unlock();
		
	}
	
	public void m2() {
		
	}
	
   public synchronized void m3() {
		
	}
   
   public static synchronized void m4() {
		
  	}
   
   // shared -> obj
   // t1, t2
   //t1-> s.m1()
   //t2 -> s.m3()
   //  t2 Shared.m4()

}

```

- Min swap to sort the number
```

public class MinSwapToOrder {
	
	public static void minSwap(int arr[]) {
		int count =0;
		
		for(int i=0;i<arr.length;i++) // 4 3 1 2 // 1 3 4 2 // 1 2 4 3 // 1234
		{
			int min = arr[i];//1
			boolean minChanged = false;
			int index = i;
			for(int j = i+1;j<arr.length;j++)
			{
				if(min>arr[j])
				{
					min = arr[j]; //1
					index=j; //2
					minChanged = true;
				}
			}
			if(minChanged)
			{
				int temp= arr[i];
				arr[i]= arr[index];
				 arr[index] = temp;
				 count++;
			}
		}
		System.out.println(count);		
	}
	public static void main(String[] args) {
		int arr[] ={4,3,1,2};// {7,1,3,2,4,5,6};
		minSwap(arr);
	}
}

```