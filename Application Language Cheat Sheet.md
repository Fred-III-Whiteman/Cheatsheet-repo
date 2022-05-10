# Application Language Cheat Sheet
[Official Documentation](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/devenv-dev-overview)

## Declaring Variables
```al
// Global variables
Var
    MyInteger: Integer;
    MySecondInt: Integer;
    MyText: Text[50];

// Protected variables
protected var
    MyProtectedAction: Action;
    MyFirstBool, MySecondBool: Boolean;

// Local variables
trigger MyTrigger() || procedure MyProcedure()
var
    MyOption: Option option1, option2;
    MyOptionEnum: Enum MyEnum;
    MyArray: array[10] of Integer;
    MyList: List of [Text];
    MyDic: Dictionary of [Code[20], List of [Text]];

begin
    // Code goes here

    // Use an Enum instead of an Option for a Global Option
    MyOptionEnum := MyEnum::option1;
    Message('The selected options is: %1', MyOptionEnum)

    // Array assignment
    MyArray[2] := 10; // 1D
    MyArray[2,5] := 5 // 2D ... etc
end;

enum 50100 MyEnum
{
    Extensible = true;

    value(0; option1)
    {
        Caption = 'Option 1';
    }

    value(1; 'option2')
    {
        Caption = 'Option 2';
    }
}
```
### [All Data Types](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/library)
**Fundamental data types**
<details>
    <Summary>
        Click to view
    </summary>

- Numeric
    - [Action](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/action/action-option)
    - [Integer](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/integer/integer-data-type)
    - [BigInteger](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/biginteger/biginteger-data-type)
    - [Decimal](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/decimal/decimal-data-type)
    - [Option](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/option/option-data-type)
    - [Char](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/char/char-data-type)
    - [Byte](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/byte/byte-data-type)
    - Duration
- String
    - [Text](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/text/text-data-type)
    - [Code](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/code/code-data-type)
- Boolean
- [Date](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/date/date-data-type)
- [Time](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/time/time-data-type)
- [DateTime](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/datetime/datetime-data-type)
</details>

---
**Complex Data Types**
<details>
    <summary>
        Click here to view
    </summary>

- [Big Text](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/bigtext/bigtext-data-type)
- [BLOB](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/blob/blob-data-type)
- [Code Unit](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/codeunit/codeunit-data-type)
- [DateFormula](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/dateformula/dateformula-data-type)
- [Dialog](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/dialog/dialog-data-type)
- [File](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/file/file-data-type)
- [Fieldref](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/fieldref/fieldref-data-type)
- [GUID](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/guid/guid-data-type)
- [InStream](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/instream/instream-data-type)
- [OutStream](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/outstream/outstream-data-type)
- [KeyRef](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/keyref/keyref-data-type)
- [Page](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/page/page-data-type)
- [Query](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/query/query-data-type)
- [Record](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/record/record-data-type)
- [RecordID](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/recordid/recordid-data-type)
- [RecordRef](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/recordref/recordref-data-type)
- [Report](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/report/report-data-type)
- [System](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/system/system-data-type)
- [TableFilter](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/properties/devenv-dataitemtablefilter-property)*
- [Variant](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/variant/variant-data-type)
- [List](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/list/list-data-type)
- [Dictionary](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/dictionary/dictionary-data-type)
</details>

---
**Collection Types**

- [Array](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods/devenv-array-methods)
    
    In Application language arrays start at an index of 1 instead of the standard 0
    ![Dimensional Arrays](https://docs.microsoft.com/en-ca/learn/modules/intro-basics-al-programming/media/multi-dimensional-array-c.png)

- [List](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/list/list-data-type)
- [Dictionary](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/dictionary/dictionary-data-type)

---
## Operators
**Unary Operators**
> "A unary operator only impacts the term that directly follows the operator."

- `+`
- `-`
- `NOT`

---
**Arithmetic Operators**
- Plus `+`
- Minus `-`
- Times `*`
- Divide `/`
- Integer divide `DIV`
    
    Integer divide will round down to the nearest whole number
- Modulus `MOD`

---
**Order of Operations**
- Highest level:

    Unary operators
- Second Level:
    - `*`
    - `/`
    - `DIV`
    - `MOD`
- Lowest level:
    - `+`
    - `-`

Order of operations can be manipulated with the use of subexpressions `()`

---
**Relational Expressions**
- Equal to `=`
- Less than `<`
- Greater than `>`
- Less than or equal to `<=`
- Greater than or equal to `>=`
- Not equal to `<>`
- Included in set `IN`

---
**Logical Expressions**
- `AND`
    > "both values must be True to result in True; otherwise, the value is False."
- `OR`
    > "One of the values must be True to result in True; otherwise, the value is False."
- `XOR`
    > "(Exclusive OR) operator, only one value can be True to result in True; otherwise, the value is False."
- `NOT`
    > "All logical values are reverted. A NOT True results in False, and a NOT False results in True."

![Opperator Summary](https://docs.microsoft.com/en-ca/learn/modules/intro-basics-al-programming/media/operator-precedence-effects-c.png)

---
## [XML Documentation](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/devenv-xml-comments#supported-xml-tags) Comments
``` al
/// <summary>
///     A summary of the object
/// </summary>
/// <param name="paramName">
///     Used to define one or more paramaters in a method. Include a name a description
/// </param>
/// <returns>
///     Used to describe the return value
/// </returns>
/// <example>
///     USed to provide an example of the code in use
/// </example>
/// <remarks>
///     used to add additional comments about the code.
///     You can use "<C></C>" for inline code or <code></code> for a block of code in any of these top level tags.
///     Use "&lt;" or "&gt;" to display angle brackets  
/// </remarks>

#region - You can also use regions!
//code here
#endregion
```

---
## Conditional Statements
**The If Statement**
``` al
// You can only declare one statement this way
If var1 (condition) var2 then
    statement;

var 
    a: Integer;
    b: Integer;
    c: Integer;
begin
    a := 10;
    b := 5;

    if a > b then
        c := a - b;
end;

// To delcare more then one statement
If var1 (condition) var2 then begin
    statement1;
    statement2;
end;

// If then else
If var1 (condition) var2 then begin
    statement1;
    statement2;
end
else begin
    altStatement1;
    altStatement2;
end;
```

---
**Case Statement**
``` al
case "Document Type" of
    "Document Type"::Quote:
        statement;
    "Document Type"::Order:
        statement;
    "Document type"::Invoice:
        begin
            statement1;
            statement2;
        end;
    "Document Type"::"Return Order":
        If Reason = Reason::Return then begin
            statement1;
            statement2;
        end;
    else
        defaultStatement;
end;
```

---
## Loops
**The For Loop**
``` al
// regular for loop
var
    index: Integer;
begin
    for index := 1 to 5 do
        statement;
end;
```

---
**"downto" for loop**
``` al
var
    index: Integer;
    sales: array[5] of Integer;
begin
    for index := 5 downto 1 do begin
        sales[index];
        statement2;
    end;
end;
```

---
**Foreach loop**
``` al
var
    stringList: List of [Text[20]];
    item: Text[20];
begin
    foreach item in stringList do
        Message(stringItem);
end;
```

---
**While loop**
``` al
var
    count: Integer;
begin
    count := 0;

    while count < 8 do begin
        count := count + 1;
        statement2;
    end;
end;
```

---
**"Repeat until" or "do while" Loop**
- This loop runs while the condition is *not* valid, and will always run *at least once*.
- Additionally this loop does not require a `begin` and `end` to contain multipule statements.
``` al
var
    count: Integer;
begin
    count := 0;
    
    repeat
        statement1;
        statement2;
    until count >= 8;
end;

// to iterate over an object (like a table)
var
    myTable: Record MyTable;
begin
    myTable.FindSet();
    repeat
        myTable.Amount := 100;
    until myTable.Next() = 0;
end;
```

---
## Built in Functions
### "Interactive" functions
**Message**

Creates a popup with the message displayed.
``` al
Message('Hello World');
Message(string [,Value1, ...]);
Message('This is a string with %1 placeholder', 'one')
```

---
**Confirm**

Creates a popup with a "yes" and "no" option for the user.
``` al
myConfirm := Dialog.Confirm(messageString [,defaultButton] [,valueForPlaceholder, ...]);

// Confirm can be evaluated in an if statement. "false" is to set the default button to "No" 
If Confirm('messageString', false) then
    Message('Pressed Yes');
else
    Message('Pressed No');
```

---
**StrMenu**

Prompts the user for information or to select from a series of choices.
``` al
OptionNumber := StrMenu(OptionString [,DefaultNumber] [,Instruction]);

var
   Days: Text[50];
   Selection: Integer;
begin
   Days := 'Monday,Tuesday,Wednesday,Thursday,Friday';
   Selection := StrMenu(Days, 1, 'Which day is today?');
   Message('You selected %1.', Selection);
end;
```

---
**Error message**

After an error message is produced the code will stop running.
``` al
Error(String [,Value1, ...]);

Error('This is an error message');
Message('This message will never run');
```

---
### String functions

All of the [.NET sting methods](https://docs.microsoft.com/en-us/dotnet/api/system.string?view=net-6.0#methods) are supported.

**StrPos and indexOf**

These can be used to find the location of a substring within a string. Returns an integer position.
``` al
stringPos := StrPos(string, subString);

Message(%1, StrPos('Hello World!', 'l')); // returns 3

// Alternatively use IndexOf
Position := String.IndexOf(Substring,[StartPosition]);

myString := 'Hello World!";
Message(%1, myString.IndexOf('w')); // returns 7
```

---
**CopyStr and Substring**

These can be used to return a section of a string.
``` al
NewString := CopyStr(String, StartIndex, [Length]); // length is optional

myString := 'Hello World!';
Message(%1, CopyStr(myString, 7)); // returns 'World!'

// Alternativy use Substring()

myString := 'Hello World!';
Message(%1, myString.Substring(7,5)); // returns 'World'
```

Caution should be used with `Substring` as it will error if the "length" value is larger then the number of characters left in the string, while `CopyStr` will not.

---
**SelectStr and Split**

`SelectStr` can be used to get a substring from a comma seperated *string*.
``` al
myString := 'This,is,a,comma seperated,string';
Message(%1, SelectStr(4, myString)); // returns 'comma seperated'
```

Split can be used to split up a string at a certain character. Split returns a list of text.
``` al
myString := 'This,is,a,comma seperated,string';
Message(%1, myString.Split(',', ' ').get(2)); // returns 'is'
```

---
**InStr**

`InStr` will insert a string into an existing string at a specified index.
``` al
myString := 'This is string';
Message(%1, InStr(myString, 'a ', 8)); // returns 'This is a string'
```

---
**StrLen and MaxStrLen**
`StrLen` will return the length of a sting and MaxStrLen will retrun the maximun length a variable can hold.
``` al
var
    myString: Text[30];
begin
    myString := 'Hello World!';
    Message(myString has %1 characters, StrLen(myString)); // returns 'myString has 12 characters'
    Message(myString can hold %1 characters, MaxStrLen(myString)); // returns 'myString can hold 30 characters'
end;
```

---
**Character case functions**

To change to case of a string use `LowerCase` and `UpperCase` or the .NET methods `ToLower` and `ToUpper`

``` al
myString := 'all lowercase';
myStringV2 := 'ALL UPPERCASE';

Message(%1, UpperCase(myString)); // or
Message(%1, myString.ToUpper()); // return 'ALL LOWERCASE'

Message(%1, LowerCase(myStringV2)); // or
Message(%1, myStringV2.ToLower()); // returns 'all uppercase'
```

---
**IncStr**

Used to increment (if positive) or decrement (if negative) a number in a string. If there is more than one number in a string it will only increment the last one.
``` al
myString := 'I am 20 years old';
Message(IncStr(myString)); // returns 'I am 21 years old'

myString := 'It is -30 out today';
Message(IncStr(myString)); // returns 'It is -31 out today'
```

---
### Date Functions
- `Today` and `Time` will return the current date and time.
- `WorkDate` will return the work date set in BC

**Date2DMY** (Date to day, month, or year)
``` al
// 1 - day, 2 - month, 3 - year
Date2DMY(Date, [1,2,3]);

todaysDate := Today(); // returns 05/10/2022 (MM/DD/YYYY)

Message(%1, Date2DMY(todaysDate, 1)); // returns 10
Message(%1, Date2DMY(todaysDate, 2)); // returns 5
Message(%1, Date2DMY(todaysDate, 3)); // returns 2022
```

---
**Date2DWY** (Date to day, weak, or year)
``` al
// 1 - day (1-7), 2 - week (1-53), 3 - year
Date2DMY(Date, [1,2,3]);

todaysDate := Today(); // returns 05/10/2022 (MM/DD/YYYY)

Message(%1, Date2DMY(todaysDate, 1)); // returns 2
Message(%1, Date2DMY(todaysDate, 2)); // returns 18
Message(%1, Date2DMY(todaysDate, 3)); // returns 2022
```
----
**CalcDate**

Used to calculate a new date from a given date or from the system date
``` al
// x - number of units to calculate, can be negative
// D - days, W - Weeks, M - Months, Q - Quarters, Y - Years
// date is optional, default is sysDate
CalcDate([xD, xW, xM, xQ, xY], (date));

myDate := 05/01/2022 (MM/DD/YYYY)
Message(%1, CalcDate('1W', myDate)); // returns 05/08/2022

Message(%1, CalcDate(-1Y)); // Returns the year from your systems date - 1
```

---
### Numeric Functions
**Round**
``` al
// Precision and direction are optional
// Precision: Number of decimal points to round too
// Direction: = - closest whole number, < - Up, > - Down
Round(number, (Precision), (Direction [=, <, >]));

myNumber := 1.34;
Message('%1', Round(myNumber)); // returns 1
Message('%1', Round(myNumber, 0, <)); // returns 2
Message('%1', Round(myNumber, 1, >)): // returns 1.3
```

---
**Abs and Power**

`Abs` will return a positive number or 0
``` al
Message(\'%1\', Abs(-10.45)); // returns 10.45

------------------------------------------------
System.Power(base: decimal, exponent: decimal);

var
    base: Decimal;
    exponent: Decimal;
    MyMessage: Label '%1 raised to the power of %2 = %3';
begin
    Number1 := 3;   
    Power1 := 2;
    Message(myMessage, base, exponent, Power(base, exponent)); // returns '3 raised to the power of 2 = 9'
end;
```

---
**Random and Randomize**

`Random(max)` will create a new random number between one and the specified max number. The max number will treat negative values as positive and if 0 is entered it will always return 1.

`Randomize(seed)` will ensure that `Random` will generate unique numbers when run in a loop. Seed is optional and defaults to the system clock.

---
### Array Functions
**ArrayLen**

`ArrayLen` will only count the number of used indices in the specified array.
``` al
// Dimension is optional and specifies the dimension in a multi-dimensional array to count.
ArrayLen(myArray, (dimension));

myArray: array[10] of Integer;
Message(%1, ArrayLen(myArray)); // returns 0

myArray[1] := 1;
myArray[2] := 2;
myArray[1] := 10;

Message(%1, ArrayLen(myArray)); // returns 2
```

---
**CompressArray**

Moves all empty strings to the end of the array.
``` al
myArray[1] := 'Chocolate';
myArray[2] := '';
myArray[3] := 'Vanilla';

CompressArray(myArray);

/* returns: 
   myArray[1] = 'Chocolate';
   myArray[2] - 'Vanilla';
   myArray[3] = '';
*/
```

---
**CopyArray**

`CopyArray` will copy an existing array from a index position and with an optional new length. If length is left blank it will copy all of the non-empty values starting from the specified position.
``` al
CopyArray(newArray, specifiedArray, position, (length));
```

---
### List Functions
**Add**
``` al
myIntList.Add(5); // adds 5 to the end of the list
myStrList.Add('orange'); // adds 'orange' to the end of the list
```

---
**Contains**

Checks if a value is contained in a list
``` al
myList := (1, 3, 4, 5);
Message(%1, myList.Contains(2)); // returns false
Message(%1, myList.Contains(4)); // returns true
```

---
**Get**

retrives and item from a list at a specified index.
``` al
myList := (1, 2, 3, 6, 7);
Message(%1, myList.Get(4)); // returns 6
```

---
**Set**

Sets the value of an index to the specified value
``` al
myList := ('red', 'blue', 'cyan', 'purple');
myList.Set(4, 'orange'); 
// results in ('red', 'blue', 'cyan', 'orange')
```

---
**Insert**

Inserts a new value into a list at a specified index
``` al
myList := (1, 2, 4, 5);
myList.Insert(3, 3);
// results in (1, 2, 3, 4, 5)
```

---
**Remove**

Removes the first occurrance of a value and returns a boolean
``` al
myList := ('Chocolate', 'Vanilla', 'Strawberry', 'Orange', 'Strawberry');
myList.remove('Strawberry'); // returns true
// results in ('Chocolate', 'Vanilla', 'Orange', 'Strawberry')
```

---
**RemoveAt**

Removes a value at a specified index and returns a boolean.
``` al
myList := ('red', 'orange', 'pink', 'blue');
myList.RemoveAt(2); // returns true
// results in ('red', 'pink', 'blue')
```

---
**Count**

Counts the number of items in a list.
``` al
myList := (1, 4, 2, 6, 8);
Message(%1, myList.Count()); // returns 5
```

---
**AddRange**

`AddRange` is the correct way to add several items to a list.
``` al
// not correct
myList := (1, 2, 3);

// Correct
myList.AddRange(1, 2, 3);
```

---
**GetRange**

Retrieves a list from an existing list, starting from a specified index and taking a specified count.
``` al
myList := (1, 2, 5, 6, 2);
myList.getRange(2, 3); // returns 2, 5, 6
```

---
**RemoveRange**

Removes several items from a list starting from a specified index and for a specified count.
``` al
myList := ('orange', 'purple', 'green', 'yellow');
myList.RemoveRange(2,2);
// results in ('orange', 'yellow')
```

---
**IndexOF**

Returns the index of the first occurrance of a specified item.
``` al
myList = (1, 6, 9, 3, 2, 9);
Message(%1, myList.IndexOf(9)); // returns 3
```

---
**LastIndexOf**

Returns the index of the last occurrance of a specified item.
``` al
myList = (1, 6, 9, 3, 2, 9);
Message(%1, myList.IndexOf(9)); // returns 6
```

---
**Reverse**

Reversed the order of a list
``` al
myList := (1, 2, 3, 4, 5);
myList.Reverse();
// results is (5, 4, 3, 2, 1)
```

---
### System Functions