coding convention
==============

* [The Zen of Python](https://www.python.org/dev/peps/pep-0020/)
* keep in mind about others.
  - respect people, but be strict about code.
* readability.
* comment also important.
* as possible as simple for easily understand.
* must write namespace.
* make a time for code review.

## Comment

* TODO
* HACK
* NOTE
* ref

``` csharp

TODO(pyoung): need to implement this.

HACK(pyoung): hard coding some.

NOTE(pyoung): I know this code is durty but i don't have a time to refactoring that.

ref: https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions

```

## You do this

* Using ( 4 ) Space instead of Tab.

## sample

``` csharp
namespace Hello.World
{
    public class Bob
    {
        // private member
        int _privateMember;

        // public member -> using public Property

        // ppublic Property
        public int PropertyCamelCase { get; private set; } = 0;

        // about ui connection.???
        [ComponentPath]
        public Button btn_category4 { get; private set; }

        // event
        event Action<int> onBtnCategory;

        // sample function.
        public int HelloWorld(int niceWorld)
        {
            // do bracket even single if statement.
            if (niceWorld == 10)
            {
                return 10;
            }

            throw new HelloException();

            // using this for setting private member.
            this._privateMember = 10;

            // boolean using `is`
            bool isBool = false;

            if (IsAttackable())
            {
                Debug.Log($"Attack {player}");
            }

            return 10;
        }
    }

    // using Customized Exception Class.
    [Serializable]
    public class HelloException : Exception
    {
        // ref: https://docs.microsoft.com/en-us/dotnet/standard/exceptions/best-practices-for-exceptions
        // ref: https://blog.gurock.com/articles/creating-custom-exceptions-in-dotnet/
    }

    // enum `E_UNDER_SCORE`
    public enum E_ENUM
    {
        HELLO_WORLD,
    }
}
```


## DON'T

* don't leave compile warning. warning is error!
* Alought you can be better, why you coding like amateur.

``` csharp
// you don't need to align column.
public static string Version          { get { return “version”; } }
public static string CreateUser       { get { return “users”; } }

int wTF(int a = 10) {

    // inline return.
    if (a == 10) return 10;

    // throw non customized exception.
    throw new Exception();

    // combine complex operator.
    return a = (true == true) ? 10 : 20;

    // don't leave useless code commented out.
    // int a = 10;
}
```


# ref
* [refactoring](https://www.amazon.com/Refactoring-Improving-Design-Existing-Code/dp/0201485672)
