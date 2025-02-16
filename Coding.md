### **Arrays**

1. Implement a method to find the subarray with the maximum sum (Kadane’s Algorithm) in a given integer array.
```
using System;

class Program
{

    static void maxSum(int[] arr)
    {
        int max = arr[0];
        int maxEnd = arr[0];

        for (int i = 1; i < arr.Length; i++)
        {
            maxEnd = Math.Max(arr[i], arr[i] + maxEnd);
            max = Math.Max(max, maxEnd);
            // Console.WriteLine("--"+max + "====" + arr[i]);
        }
        Console.WriteLine(max);
    }



    static void Main(string[] args)
    {

        int[] arrr = { 1, 2, 3, 4 };
        maxSum(arrr);
    }
}
```

2. Write a program to find the intersection and union of two unsorted arrays without using built-in functions.
```
using System;

class Program
{
    static int[] getUnion(int[] arr1, int n1, int[] arr2, int n2)
    {
        int[] unionArr = new int[n1 + n2];
        int index = 0;

        for (int i = 0; i < n1; i++)
        {
            if (!checkPresent(unionArr, index, arr1[i]))
            {
                unionArr[index++] = arr1[i];
            }
        }

        for (int i = 0; i < n2; i++)
        {
            if (!checkPresent(unionArr, index, arr2[i]))
            {
                unionArr[index++] = arr2[i];
            }
        }

        return trimArr(unionArr, index);
    }

    static int[] getIntersection(int[] arr1, int n1, int[] arr2, int n2)
    {
        int[] intersectionAyy = new int[Math.Min(n1, n2)];
        int index = 0;

        for (int i = 0; i < n1; i++)
        {
            if (checkPresent(arr2, n2, arr1[i]) && !checkPresent(intersectionAyy, index, arr1[i]))
                intersectionAyy[index++] = arr1[i];
        }

        return trimArr(intersectionAyy, index);
    }

    static bool checkPresent(int[] arr, int length, int value)
    {
        for (int i = 0; i < length; i++)
        {
            if (arr[i] == value)
                return true;
        }
        return false;
    }

    static int[] trimArr(int[] arr, int length)
    {
        int[] result = new int[length];
        for (int i = 0; i < length; i++)
        {
            result[i] = arr[i];
        }
        return result;
    }

    static void Main()
    {
        int[] arr1 = { 1,2,3,4,5,6,};
        int[] arr2 = { 3,4,5,6,7,8,9 };
        int n1 = arr1.Length;
        int n2 = arr2.Length;

        int[] unionArr = getUnion(arr1, n1, arr2, n2);
        int[] intersectionAyy = getIntersection(arr1, n1, arr2, n2);

        foreach (int u in unionArr)
            Console.Write(u + " ");
        Console.WriteLine();

        foreach (int i in intersectionAyy)
            Console.Write(i + " ");
        Console.WriteLine();
    }
}

```

3. Implement a sparse matrix multiplication algorithm using a 2D array in C#.



4. Write a method to find the first missing positive integer in an unsorted array (without sorting).


```
using System;

class Program
{
    static int findPositiveInt(int[] arr)
    {
        for (int i = 0; i < arr.Length; i++)
        {
            while (arr.Length >= arr[i] && arr[i] > 0 && arr[arr[i] - 1] != arr[i])
            {
                int temp = arr[arr[i] - 1];
                arr[arr[i] - 1] = arr[i];
                arr[i] = temp;
            }
        }

        for (int i = 0; i < arr.Length; i++)
        {
            if (i + 1 != arr[i])
                return i + 1;
        }

        return arr.Length + 1;
    }

    static void Main()
    {
        int[] arr = { -1,-3,1,4,3,2,7 };
        Console.WriteLine(findPositiveInt(arr));

    }
}

```


5. Design a method to rotate a 2D matrix (NxN) 90 degrees clockwise in place without using extra space.



```
using System;

class Program
{
    static int matrixRotate90(int[,] matrix, int n)
    {
        if (matrix == null || n <= 0) return -1;
        for (int i = 0; i < n / 2; i++)
        {
            int low = i;
            int high = n - 1 - i;

            for (int j = low; j < high; j++)
            {
                int left = j - low;
                // Console.WriteLine("left"+ left);
                int top = matrix[low, j];
                matrix[low, j] = matrix[high - left, low];
                matrix[high - left, low] = matrix[high, high - left];
                matrix[high, high - left] = matrix[j, high];
                matrix[j, high] = top;
            }
        }
        return 1;
    }

    static void displayMatrix(int[,] matrix, int n)
    {
        for (int i = 0; i < n; i++)
        {
            for (int j = 0; j < n; j++)
            {
                Console.Write(matrix[i, j] + "\t");
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }

    static void Main()
    {
        int[,] matrix = {
            { 1, 2, 3,4 },
            { 5,6,7,8 },
            { 9,10,11,12 },
            { 13,14,15,16 },
        };

        int n = matrix.GetLength(0);

        int output = matrixRotate90(matrix, n);

        if (output == 1)
        {
            displayMatrix(matrix, n);
        }
        else
        {
            Console.WriteLine("Rotation Reeoe");
        }
    }
}

```






### **Classes (Advanced Level)**

1. Create a "StockPortfolio" class that tracks multiple stocks. Implement methods to add stocks, remove stocks, and calculate the total portfolio value dynamically.


2. Design a "SmartHomeSystem" class that contains a list of connected devices. Implement methods to add a device, remove a device, and turn on/off all devices dynamically.



3. Implement a "TaskScheduler" class with priority-based task execution using a queue-based approach.



4. Create a "BlockchainTransaction" class with cryptographic hashing of transactions using SHA256. Implement methods for validating transactions.



5. Build a "MusicPlaylist" class with a doubly linked list structure to efficiently add, remove, and play songs.

### **Polymorphism (Advanced Level)**

1. Create an "ExpressionEvaluator" class using operator overloading to evaluate mathematical expressions dynamically.


2. Implement a "DatabaseConnector" base class with different derived classes for SQL, MongoDB, and Firebase that override a `Connect()` method.

```



abstract class DatabaseConnector
{
    public abstract void Connect();
}


class SQL : DatabaseConnector
{
    public override void Connect()
    {
        Console.WriteLine("Connecting to SQL Server...");
    }
}

class MongoDB : DatabaseConnector
{
    public override void Connect()
    {
        Console.WriteLine("Connecting to MongoDB Database...");
    }
}
class Firebase : DatabaseConnector
{
    public override void Connect()
    {
        Console.WriteLine("Connecting to FireBase Database...");
    }
}


class X
{
    static void Main(string[] args)
    {
        DatabaseConnector sql = new SQL();
        sql.Connect();
        DatabaseConnector mongo = new MongoDB();
        mongo.Connect();
        DatabaseConnector firebase = new Firebase();
        firebase.Connect();

    }
}
```

3. Develop a "FileCompressor" class with overloaded `Compress()` methods that handle text, images, and videos differently.


4. Design an "AIModel" class with multiple versions (BasicAI, NeuralNet, DeepLearning) that override a `TrainModel()` method for different complexity levels.


5. Create a "GamePhysicsEngine" base class with different implementations for 2D and 3D games using runtime polymorphism.

---

### **Inheritance (Advanced Level)**

1. Implement a "MultiLevelBankingSystem" where "CentralBank" is the parent class, "NationalBank" is the child, and "LocalBank" is a subclass of "NationalBank". Override an `InterestRate()` method at each level.

```



class CentralBank
{
    public virtual void intrestRate()
    {
        Console.WriteLine("Intrest Rate is 10%");
    }
}

class NationalBank : CentralBank
{
    public override void intrestRate()
    {
        Console.WriteLine("Intrest Rate is 8%");
    }
}

class NocalBank : NationalBank
{
    public override void intrestRate()
    {
        Console.WriteLine("Intrest Rate is 5%");

    }
}

class X
{
    static void Main(string[] args)
    {
        CentralBank c = new CentralBank();
        c.intrestRate();
        NationalBank n = new NationalBank();
        n.intrestRate();
        NocalBank l = new NocalBank();
        l.intrestRate();

    }
}
```

2. Develop a "SmartVehicle" inheritance hierarchy where a "Vehicle" class has electric and gas-powered subclasses, and further derived classes like "SelfDrivingCar" and "HybridCar". Implement an overridden `Drive()` method in each.

```



class Vehicle
{
    public virtual void Drive()
    {
        Console.WriteLine("ElectricVehicle Veichle Driving.....");
    }
}

class ElectricCar : Vehicle
{
    public override void Drive()
    {
        Console.WriteLine("Electric Veichle Driving.....");
    }
}

class GasPoweredCar : Vehicle
{
    public override void Drive()
    {
        Console.WriteLine("Gas Powered Car Driving.....");

    }
}

class SelfDrivingCar : ElectricCar
{
    public override void Drive()
    {
        Console.WriteLine("Self Driving Car is using Electricity.....");
    }
}

class HybridCar : GasPoweredCar
{
    public override void Drive()
    {
        Console.WriteLine("Gas Powered Car Using CNG...");
    }
}
class X
{
    static void Main(string[] args)
    {
        Vehicle vv = new Vehicle();
        vv.Drive();
        ElectricCar e = new ElectricCar();
        e.Drive();
        GasPoweredCar g = new GasPoweredCar();
        g.Drive();
        SelfDrivingCar s = new SelfDrivingCar();
        s.Drive();
        HybridCar h = new HybridCar();
        h.Drive();

    }
}
```

3. Create an "EmployeeHierarchy" where "Employee" is the base class, inherited by "Manager" and "Director". Implement a `CalculateBonus()` method differently for each.

```



class Employee
{
    public virtual void CalculateBonus(int salary)
    {
        Console.WriteLine("Employee Salary " + salary);
    }
}

class Manager : Employee
{
    public override void CalculateBonus(int salary)
    {
        double MBonus = salary * 10 / 100;
        Console.WriteLine("Manager Bonus.... " + (salary + MBonus));
    }
}



class Director : Employee
{
    public override void CalculateBonus(int salary)
    {
        double DBonus = salary * 15 / 100;
        Console.WriteLine("Direector Bonus.... " + (salary + DBonus));
    }
}

class X
{
    static void Main(string[] args)
    {
        int salary = 10000;
        Employee e = new Employee();
        e.CalculateBonus(salary);
        Manager m = new Manager();
        m.CalculateBonus(salary);
        Director d = new Director();
        d.CalculateBonus(salary);

    }
}
```

4. Design a "SecureMessagingSystem" where "Message" is a base class with encrypted and non-encrypted message types, overriding a `Send()` method with encryption logic in the subclass.

```
```

5. Develop an "ECommercePlatform" class structure with multiple levels of inheritance where "Product" is the base class, extended by "Electronics" and "Clothing", with further derived classes like "Laptop" and "T-Shirt". Implement a method to calculate discounts dynamically.



