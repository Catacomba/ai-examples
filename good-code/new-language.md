# Im a beginner in delphi

In other languages, when you have an if statement it looks somewhat like this:

```python
if someBoolean:
  do_something()
  do_somethingelse()
  this_is_still_being_done_inside_of_if()
```

or something like this:

```csharp
if(someBoolean) 
{
  do_something();
  do_somethingelse();
  this_is_still_being_done_inside_of_if();
}
```

So I first assumed that in delphi it is like this:

```pascal
if Assigned(SomeNode) then
  doSomeStuff();
  doSomeOtherStuff();
  doSomeThirdStuff();
```

Confused why the 

```pascal
  doSomeOtherStuff();
  doSomeThirdStuff();
```

are still being executed even if SomeNode is null. I realized I should ask AI for a concrete example of an if statement with a multiline code blocks inside of it.

it produced this:

```pascal
if SomeCondition then
begin
  DoSomething;
  DoSomethingElse;
  ShowMessage('Condition was true');
end;
```

Which made me realize, that you need `begin` and `end` to encapsulate the code you want to run inside of `if`.
Could I have googled, or turned to the delphi programming manual to find out this incredibly basic and beginner information? Sure, would it probably take longer than to ask ChatGPT, probably.
