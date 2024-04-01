# Deleage
Certainly! In C#, **delegates** provide a way to encapsulate and invoke methods. They are similar to function pointers in C and C++, but with added object-oriented features. Let's explore some examples:

1. **Declaring a Delegate**:
    ```csharp
    public delegate void Callback(string message);
    ```
    Here, we've declared a delegate named `Callback` that can encapsulate a method taking a string argument and returning `void`.

2. **Creating a Delegate Instance**:
    You can create a delegate instance by providing the name of the method it will wrap:
    ```csharp
    // Create a method for the delegate.
    public static void DelegateMethod(string message)
    {
        Console.WriteLine(message);
    }

    // Instantiate the delegate.
    Callback handler = DelegateMethod;

    // Call the delegate.
    handler("Hello World");
    ```
    The `handler` delegate now points to the `DelegateMethod`, and invoking it calls the method.

3. **Asynchronous Callbacks**:
    Delegates are powerful for asynchronous callbacks. For example:
    ```csharp
    public static void MethodWithCallback(int param1, int param2, Callback callback)
    {
        callback("The number is: " + (param1 + param2).ToString());
    }

    // Pass the delegate to the method.
    MethodWithCallback(1, 2, handler);
    ```
    The `MethodWithCallback` prepares a string and passes it to another method, allowing the caller's code to become part of the process.

4. **Multicast Delegates**:
    Delegates can also combine multiple methods into a single delegate using the `+=` operator:
    ```csharp
    public delegate void MultiCallback(string message);

    public static void Method1(string msg) { /* ... */ }
    public static void Method2(string msg) { /* ... */ }

    MultiCallback multiHandler = Method1;
    multiHandler += Method2; // Combining two methods

    multiHandler("Hello Multicast!");
    ```
    In this example, both `Method1` and `Method2` are called when `multiHandler` is invoked.

Remember, delegates are type-safe and secure, making them a powerful tool for method encapsulation and callback scenarios. 🚀

For more details, you can explore the [official Microsoft documentation on delegates](https://learn.microsoft.com/en-US/dotnet/csharp/programming-guide/delegates/using-delegates) ¹.


(1) Using Delegates - C# Programming Guide - C# | Microsoft Learn. https://learn.microsoft.com/en-US/dotnet/csharp/programming-guide/delegates/using-delegates.
(2) Delegates - C# Programming Guide - C# | Microsoft Learn. https://learn.microsoft.com/en-US/dotnet/csharp/programming-guide/delegates/.
(3) C# delegates (With Examples) - Programiz. https://www.programiz.com/csharp-programming/delegates.
(4) C# 委托（Delegate） | 菜鸟教程. https://www.runoob.com/csharp/csharp-delegate.html.
# DDD
NEventStore is a persistence library used to abstract different storage implementations when using event sourcing as storage mechanism. This library is developed with a specific focus on DDD/CQRS applications.
# reflection
Certainly! In C#, **reflection** allows us to inspect and manipulate classes, constructors, methods, and fields at runtime. It's a powerful feature that enables dynamic introspection of code. Let's explore some examples:

1. **Declaring a Class for Reflection**:
    Suppose we have a simple `Student` class with a field (`age`) and a method (`score`):
    ```csharp
    class Student
    {
        public int age;
        public void score()
        {
            // ... some code
        }
    }
    ```

2. **Using Reflection to Get Type Information**:
    The `Type` class is the key to reflection. It provides methods and properties to access metadata about a type. For instance:
    ```csharp
    using System;
    using System.Reflection;

    class Program
    {
        static void Main()
        {
            string studentName = "Jack";
            Type studentNameType = studentName.GetType();
            Console.WriteLine("Type is: " + studentNameType);
        }
    }
    // Output: Type is: System.String
    ```
    In this example, we retrieve the type of the `studentName` variable using `GetType()`. The result is `System.String`, indicating the current type of `studentName`.

3. **Getting Assembly Information**:
    The `Assembly` property of the `Type` class provides information about the assembly containing the code:
    ```csharp
    using System;
    using System.Reflection;

    class Program
    {
        static void Main()
        {
            Type programType = typeof(Program);
            Console.WriteLine(programType.Assembly);
        }
    }
    // Output: app, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
    ```
    Here, we obtain the assembly information for the `Program` class.

Reflection is a powerful tool for scenarios like dynamically loading types, inspecting attributes, and creating instances at runtime. Dive deeper into the fascinating world of reflection! 🌟

For more details, you can explore the [official Microsoft documentation on reflection](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/reflection) ¹.


(1) C# Reflection (With Examples) - Programiz. https://www.programiz.com/csharp-programming/reflection.
(2) . https://bing.com/search?q=reflection+c%23+example.
(3) What is Reflection in C#? - GeeksforGeeks. https://www.geeksforgeeks.org/what-is-reflection-in-c-sharp/.
(4) undefined. https://learn.microsoft.com/en-us/dotnet/framework/reflection-and-codedom/reflection.
(5) undefined. https://www.c-sharpcorner.com/UploadFile/009ee3/reflection-in-C-Sharp/.
(6) undefined. https://stackify.com/what-is-c-reflection/.
(7) undefined. https://learn.microsoft.com/en-us/dotnet/csharp/advanced-topics/reflection-and-attributes/.
# func
# BFF
  Backend for fronted API
# .net Core 6
Host/Server/MiddLeware/Appliction

public class Startup
{
    public Startup(IConfiguration configuration)
    {
        Configuration = configuration;
    }

    public IConfiguration Configuration { get; }

    public void ConfigureServices(IServiceCollection services)
    {
        services.AddRazorPages();
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Error");
            app.UseHsts();
        }

        app.UseHttpsRedirection();
        app.UseStaticFiles();
        app.UseRouting();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapRazorPages();
        });
    }
}
1.MiddeWare 中 IApplicationBuilder
  RUN Use Map
https://codepen.io/pen/
