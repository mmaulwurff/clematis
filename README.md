# Clematis
Basic ZScript unit test framework for GZDoom

This is inspired by [Lilac](https://github.com/chesko256/Lilac) by [Chesko](https://github.com/chesko256)

## Documentation
### Making Test Suites
```CSharp
class ClematisExample:Clematis{
    override
    void TestSuites(){
        Describe('Testing Player Stats');
            It('MaxHealth', 90>100, ERR_Warning);
            It('Math', 1+1==2, ERR_Fatal);
        EndDescribe();

        Describe('Testing Math');
            It('Calculus', 0*1!=0, ERR_Error);
            It('Math', 1+2==2, ERR_Warning);
        EndDescribe();
    }
}
```
Override TestSuites and put in your own!
Suites are started with `Describe` and end with `EndDescribe`

### How to Run Tests
#### On Instantiation
Tests run on instantiation by default, which can be disabled by overriding `Init()`
##### Factory Method
```CSharp
Clematis.Create('ClematisExample');
```
##### Network Event
```CSharp
EventHandler.SendNetworkEvent('test:ClematisExample');
```
##### Console Command
```
netevent test:ClematisExample
```
#### On Method Call
```CSharp
Clematis Tester=Clematis.Create('ClematisExample');
Tester.Run();
```

### License
Clematis is under the [BSD 3-Clause License](https://github.com/ZippeyKeys12/clematis/blob/master/LICENSE)
