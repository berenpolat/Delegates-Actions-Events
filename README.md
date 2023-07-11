# Defining A Delegate In CSharp

delegate void my_Delegate();                  //declaration of a Delegate
my_Delegate my_variable;                      //declaration of a Delegate variable

void Awake()
{
    my_variable=your_name;                  //passing the function your_name to Delegate.
}

void your_name()                                //function matching the Delegate Template
{
  Debug.Log("My name is Beren");
}

void Start()
{
    my_variable();                                //calling the Delegate
}



//When we call the delegate, it will in turn call the function stored. In the above code, the delegate will call the your_name function and log the statement “My name is Beren”.
//It’s advised to check if the delegate is not null before calling it.


if (my_variable != null)
            {
                my_variable();
            }
//You can also simplify the if condition into a single line like this

my_variable?.Invoke();

//When you use the ‘=’ operator to assign the function, the delegate is overwritten with the new function. In order to add multiple function to the delegate we need to use the ‘+=’ operator.

delegate void my_Delegate();                  
my_Delegate my_variable;                      

void Awake()
{
    my_variable+=your_name; 
    my_variable+=another_func;                
}

void your_name()                               
{
  Debug.Log("My name is VionixStudio");
}


void another_func()
{
   Debug.Log("Just another Function");
}

void Start()
{
    my_variable();                               
}




#Defining An Action In Unity

namespace DelegateTrial.Actions;

public class Class1
{
    private static Action NewAction;
    
    private static void Start()
    {
        NewAction += Func1;
        NewAction += Func2;
    }

    private static void Recall()
    {
        NewAction?.Invoke();
    }

    private static void Func1()
    {
        Console.WriteLine("You have called func1");
    }

    private static void Func2()
    {
        Console.WriteLine("You have called func2");
    }

    public static void Main()
    {
        Recall();
        Start();
        NewAction();
    }
    
    
}



