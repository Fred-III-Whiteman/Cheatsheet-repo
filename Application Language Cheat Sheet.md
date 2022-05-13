# Application Language Cheat Sheet
[Official Documentation](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/devenv-dev-overview)

## Table of Contents
1. [Declaring Variables](#declaring-variables)
2. Data Types
    - [Fundamental Data Types](#fundamental-data-types)
    - [Complex Data Types](#complex-data-types)
    - [Collection Types](#collection-types)
3. [Operators](#operators)
4. [XML Docs and Comments](#xml-documentation-comments)
5. [Conditional Statements](#conditional-statements)
6. [Loops](#loops)
7. Built in Functions
    - ["Interactive" Functions](#"interactive"-functions)
    - [String Functions](#string-functions)
    - [Date Functions](#date-functions)
    - [Numeric Functions](#numeric-functions)
    - [Array Functions](#array-functions)
    - [List Functions](#list-functions)
    - [System Functions](#system-functions)
    - [Field Functions](#field-functions)
    - [Variable Functions](#variable-functions)
    - [Data Access Functions](#data-access-functions)
    - [Modifying Data](#modifying-data)
8. [Custom Functions or Procedures](#custom-functions-or-procedures)
9. [Code Units](#code-units)
10. [Triggers](#triggers)
11. [Interfaces](#interfaces)
12. Tables
    - [ExtendedDatatype Property](#extendeddatatype-property)
    - [Table Relations](#table-relations)
    - [Calculated Fields](#calculated-fields)
    - [Table Extensions](#table-extensions)
13. Pages
    - [Page Types](#page-types)
    - [Page Parts](#page-parts)
    - [Page Properties](#page-properties)
    - [Field Properties](#field-properties)
    - [Page Extensions](#page-extensions)
    

## Declaring Variables
[back to the top](#application-language-cheat-sheet)
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
## Data Types
[All Data Types](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/library)

### Fundamental data types
[back to the top](#application-language-cheat-sheet)
<details>
    <summary>
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
### Complex Data Types
[back to the top](#application-language-cheat-sheet)
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
### Collection Types
[back to the top](#application-language-cheat-sheet)

- [Array](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods/devenv-array-methods)
    
    In Application language arrays start at an index of 1 instead of the standard 0
    ![Dimensional Arrays](https://docs.microsoft.com/en-ca/learn/modules/intro-basics-al-programming/media/multi-dimensional-array-c.png)

- [List](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/list/list-data-type)
- [Dictionary](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/methods-auto/dictionary/dictionary-data-type)

---
## Operators
[back to the top](#application-language-cheat-sheet)

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
[back to the top](#application-language-cheat-sheet)
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
[back to the top](#application-language-cheat-sheet)

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
[back to the top](#application-language-cheat-sheet)

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
[back to the top](#application-language-cheat-sheet)

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
[back to the top](#application-language-cheat-sheet)

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
[back to the top](#application-language-cheat-sheet)

- `Today` will return the current date and `Time` will return the current time from the system.
- `WorkDate` will return the work date set in BC.

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
[back to the top](#application-language-cheat-sheet)

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
[back to the top](#application-language-cheat-sheet)

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
[back to the top](#application-language-cheat-sheet)

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
[back to the top](#application-language-cheat-sheet)

**UserID and CompanyName**

You can use `UserId();` and `CompanyName();` to return the user id and company name of whoever is logged in and running code.

---
### Field Functions
[back to the top](#application-language-cheat-sheet)

**CalcFields and SetAutoCalcFields**
These are used to run calculations on specified fields. `myRecord.CalcFields(attribute);` only runs one calculation per call while, `myRecord.SetAutoCalcFields(attribute);` will always run the calculations while in the funcion scope.

---
**CalcSums**
This is used to calculate a total for a specified attribute based on the filters in the dataset.

---
**FieldError**
This is used to throw an error for a specified field if it does not meet the specified criteria.
``` al
if myRecord.field > 100 & < 0 then
    myRecord.FieldError(field, 'Must be between 0 and 100');
```
---
**Init**
This is used to instantiate a new record of a specified type with all of it attributes being set to the default value, unless an `InitValue` is specified on the table, in which case the attribute will be set to that value.

---
**TestField**

This is used to check weather a field has a value or has been left blank. If it is empty it will throw a run-time error.
``` al
myRecord.TestField(field, [value]);
```
The value is optional and can be used to check if the field has a specified value.

---
**Validate**

This is used to run the `OnValidate` trigger on a specified field.
``` al
myRecord.Validate(field, [value]);
```
The optional value can be used to assign that value then run the `OnValidate` trigger.

---
### Variable Functions
[back to the top](#application-language-cheat-sheet)

**Clear and ClearAll**

- `Clear(myVar);` will reset the specified variable to its default of initialized value. A string will return to an empty string, and a int will return to 0.
- `ClearAll();` does the same thing as clear, but does it to everything including any keys and filters, with the expection of the Rec variable.

---
**Evaluate**

Evaluate is used to convert a variable of type (code or text) into a different data type (that isn't code or text). It returns a boolean.
``` al
boolean := Evaluate(variable, varToConvert);
```

---
**Format**

`Format` can also be used to convert variables to the text data type.
``` al
myString := Format(myInt);
```

---
### Data Access Functions
[back to the top](#application-language-cheat-sheet)

**Get**

The `Get` function retrives a record via the Primary Key. If the PK is a combination key you need to specify all keys.
``` al
var
    myRecord: Record databaseRecord;
begin
    // It is advisable to use an if statement like a "try/Catch"
    If myRecord.get('PrimaryKey') then
        Message('Record Found!');
    else
        Error('Record Not Found D:');
end;
```
---
**Find**

There are two "Find" functions: `FindFirst` and `FindLast`, which call an SQL query for `SELECT TOP 1`.

Some code still uses the deprecated functions `Find('-')` and `Find('+')`, These have bad performance and should be avoided.

``` al
var
    myRecord: Record databaseRecord;
begin
    myRecord.FindFirst(); // Queries SQL for the first record via SELECT TOP 1 * FROM myRecord

    myRecord.FindLast(); // Queries SQL for the last record via SELECT TOP 1 * FROM myRecord ORDER BY No. DESC
end;
```
To retrive all records use `FindSet();`
``` al
var
    myRecord: Record databaseRecord;
begin
    myRecord.FindSet(); // Queries SQL for all records via SELECT * FROM myRecord
end;
```

---

**Next**

To get the next record from a serires of records use the `Next();` function
``` al
var
    myRecord: Record databaseRecord;
begin
    myRecord.FindSet();

    repeat
        Message(myRecord.attribute);
    until myRecord.Next() = 0;
end;
```
---
**IsEmpty**

`IsEmpty();` is used to check if a record exists.

---
### Sorting Functions
[back to the top](#application-language-cheat-sheet)

**SetCurrentKey**

To change the attribute that the find functions will sort by call the `SetCurrentKey` function
``` al
var
    myRecord: Record databaseRecord'
begin
    myRecord.SetCurrentKey(attribute);

    myRecord.FindFirst(); // this is now sorted by the specified attribute
end;
```
---
**SetRange and SetFilter**

To filter the results by a range use `SetRange`, which takes three arguments:
``` al
SetRange(Attribute, [FromValue], [ToValue]);
```
`FromValue` and `ToValue` are both optional and if you leave both out you will remove that filter from the query. If you only leave `ToValue` out, it will search for all records that equal the `FromValue`.

In order to search for records that have values larger or smaller then a specified value, you should use `SetFilter`.

`SetFilter` accepts all relational expressions (comparison operators) as well as `&` (and) and `|` (or).
``` al
SetFilter(attribute, String, [value1], [value2]);
```
`value1` and `value2` represent valuse for placeholders, the actual filter goes into the string.
``` al
myRecord.SetFilter("No.", '> 10 & < 100');
// or
myRecord.SetFilter("No.", '> %1 & < %2', myVar1, myVar2);
```
Now would be a good time to consider using `IsEmpty();`
``` al
var
    myRecord: Record databaseRecord;
begin
    myRecord.SetFilter(attribute1, '*@banana* | *@apple*'); // searching for any record with the words "banana" or "apple" in the specified attribute

    if (myRecord.IsEmpty()) then
        Message('No Records Found.');
    else
        Message('%1 records found.', myRecords.Count());
end;
```
---
### Modifying Data
**Insert**

Before inserting data you must set values for each attribute for that entity.
``` al
var
    myRecord : Record databaseRecord;
begin
    myRecord.Init(); // Create a new empty record
    // Set values
    myRecord.attribute1 := value1;
    myRecord.attribute2 := value2;
    // etc..
    myRecord.Insert(true); // true denotes if the "OnInsert" trigger should run
end;
```
---
**Modify and ModifyAll**
``` al
var
    myRecord: Record databaseRecord;
begin
    myRecord.Get(primaryKey); // get the record to update
    // update the values
    myRecord.attribute2 := value1;
    myRecord.attribute5 := value2;
    // etc...
    myRecord.Modify(true); // true decides if the "OnModify" trigger should run
end;
```
`ModifyAll` will update a specified collection of records
``` al
var
`myRecord: Record databaseRecord;
begin
    myRecord.SetRange("No.", 500, 550); // get the records to update
    // update the values
    myRecord.ModifyAll(attribute, newValue, true); // true decides if the "OnModify" trigger should run
end;
```
---
**Delete and DeleteAll**
``` al
var
`myRecord: Record databaseRecord;
begin
    myRecord.Get(primaryKey); // get the record to delete
    myRecord.Delete(true); // true decides if the "OnDelete" trigger should run

    // or

    myRecord.SetRange("No.", 500, 550); // get the records to delete
    myRecord.DeleteAll(true); // true decides if the "OnDelete" trigger should run
end;
```
**NOTE:** Both `Delete` and `DeleteAll` do not ask for confirmation and will remove the records without notice.

---
## Custom Functions or Procedures
[back to the top](#application-language-cheat-sheet)

``` al
trigger myTrigger()
begin
    myFunction();
    // or
    myVar = myFunction();
    // or
    myVar = myVar2 * myFunction();
end;

// local - can only be accessed from within the same object
// internal - can only be accessed from within the same extension
// protected - can only be accessed from within the defining and host object

[local, internal, protected] procedure myFunction(param1: dataType; param2: dataType) : returnType
var
    myLocalVar: dataType;
begin
    // code goes here
    Exit(toBeReturned); // same as return in 90% of other languages
end;
```

By default paramaters are passed by value, meaning that the value of the variable does not change when the value of the paramater is changed.

To pass a variable by reference, which *will* change its value when the value of the paramater is changed, add `var` in-front of the paramater.
``` al
trigger myTrigger()
begin
    myProcedure(myVar);
end;

procedure myProcedure(var param1: integer)
begin
    param1 := 20; // this will change the value of myVar
end;
```
---
## Code Units
[back to the top](#application-language-cheat-sheet)
### Subtypes
> "Normal - The default value for every new codeunit. This subtype is a regular codeunit. It has only one trigger: OnRun".

> "Install - This type of codeunit will only be run during the installation of the extension package. This subtype provides access to two extra triggers".

> "Upgrade - This type of codeunit will only be run during the upgrade process of an extension package. This subtype gives access to five extra triggers".

> "Test - This subtype enables you to write unit test functions. You don't create normal functions in this codeunit because it can only run during unit testing".

> "TestRunner - This subtype will run one or more Test codeunits".
---
### Syntax
``` al
codeunit id(50100) name(myCodeunit)
{
    Access = Public;
    Subtype = Normal;

    trigger OnRun()
    begin

    end;

    procedure myProcedure()
    begin

    end;
}
```
---

### Accessing Code units
using `RunObject`
``` al
actions
{
    area(Processing)
    {
        action(actionName)
        {
            ApplicationArea = All;
            Image = NewSum;

            RunObject = codeUnit MyCodeUnit; // This will only use the OnRun trigger
        }
    }
}
```

Accessing other function inside your code unit
``` al
actions
{
    area(processing)
    {
        action(actionName)
        {
            ApplicationArea = All;
            Image = NewSum;

            trigger OnAction()
            var
                myCodeunitReference: Codeunit myCodeunit;
            begin
                myCodeunitReference.myFunction();
            end;
        }
    }
}
```
---
## Triggers
[back to the top](#application-language-cheat-sheet)

[All Triggers](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/devenv-event-types#trigger-events)

### Table Triggers
- `OnInsert` will run just before a new record is inserted into a table.
- `OnModify` will run just before a record is modified or updated.
- `OnDelete` will run just before a record is removed from a table.
- `OnRename` will run just before a record is renamed.

### Field Triggers
- `OnValidate` will run after a user clicks away from a modified field.
- `OnLookup` will run when after a different table is queried.
- `OnAssistEdit` will run when a user uses the "Assist Edit" button.
- `OnDrillDown` will run when a user opens a "drill-down" field.

### Page Triggers
 - `OnInit` will run when the page is loaded, but before the user has access.
 - `OnOpenPage` will run after the page is initialized and the user has access.
 - `OnAfterGetRecord` will run after a record is retrived, but before it is displayed.
 - `OnAfterGetCurrRecord` will run after the current record has been retrived from the table.
 - `OnAction` will run when a user selects a button. This trigger has the potential to conflict with `RunObject`, so it is advisable to use only one. If more logic is needed then is available with `RunObject` then `OnAction` should be used.

 ---
 ## Custom Events
 [back to the top](#application-language-cheat-sheet)

You can write your own custom events that will allow future integrations to be made without modifying original code.

There are two levels of custom events:
- "Bussiness Events" - Which are made by Microsoft and other ISVs. These come with the guaranty that their signature will never change.
- "Integration Events" - These can be made by anyone and do not come with the same guarantee as Bussiness events.

There are three parts to custom events:
- the **event**
- a **Publisher**
    - This is where the event is declared and where people can subscribe.
- a **Subscriber**
    - This listens for the event and runs the custom logic (ie a trigger).

**Declaring an Integration Event**

To decclare an Integration event simply add the following annotation to an empty procedure:
``` al
[IntegrationEvent(IncludeSender, false)]
```
`IncludeSender` will allow subscribers to access the publishing object so that they can access other function in the same instance.

The second paramater `GlobalVarAccess` is deprecated and should *always* be set to false.

**Subscribing to an event**

To subscribe to an event add the following annotation to a procedure:
``` al
[EventSubscriber(ObjectType::Codeunit, Codeunit::codeunitName, 'eventName', '', SkipOnMissingLicense, SkipOnMissingPermission)]
```

In order to subscribe to an event you must tell it where the event publisher is located and its name, which are the first three paramaters.

The fourth paramater is for subscribing to `OnBeforeValidate` or `OnAfterValidate`, and you need to define the field to use the validation event on.

`SkipOnMissingLicense` and `SkipOnMissingPermissions` define wheather the event should be skipped if you don't have the correct license or permission (true - skip, false - will throw an error). If these are set to false and they throw an error, all other subscribers will stop or be rolled back.

---
## Interfaces
[back to the top](#application-language-cheat-sheet)

[Interfaces](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/devenv-interfaces-in-al)

![Interface1](https://docs.microsoft.com/en-us/learn/modules/business-central-interfaces/media/interface-example.png)

an example of using interfaces to provide both backwards compatability and new versions.
![interface2](https://docs.microsoft.com/en-us/learn/modules/business-central-interfaces/media/interface-example-2.png)

---
## Tables
### Table properties
[back to the top](#application-language-cheat-sheet)
**LookupPageId and DrillDownPageId**

When a table is called from a lookup it will use `LookupPageId` property to run a page that will populate the dropdown list.
``` al
table 50100 myTable
{
    LookupPageId = myPage;

    // ...
}
```
Similarly the `DillDownPageId` property is used to define the page that should run when a drill-down action is selected.
``` al
table 50100 myTable
{
    DrillDownPageId = myPage;

    // ...
}
```
You can use the page's ID but it is recommended to use its name instead.

---
### Fields
[back to the top](#application-language-cheat-sheet)

Fields are how you define the columns of a table or the attributes of an entity. A field takes three paramaters: ID, name, and datatype. In the field you can also declare several properties, such as: `Caption`, `ExtendedDataType`, `TableRelation`, `FieldClass`, `OptionMembers`, and many [more](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/properties/devenv-table-properties).
``` al
fields
{
    field(id; myAttribute; datatype)
    {
        // properties go here
    }

    field(10; Code; Code[10])
    {
        DataClassification = CustomerContent;
        Caption = 'Code';
    }

    field(20; myOptions; Option)
    {
        DataClassification = CustomerContent;
        Caption = 'Type';
        OptionMembers = option1, "option 2", option3;
        OptionCaption = 'optionCaption1, Option Caption 2, optionCaption3';
    }

    field(30; "My Table Relation"; Code[20])
    {
        DataClassification = CustomerContent;
        Caption = 'Lookup in another table.';
        TableRelation = otherTable where(otherAttribute = someCondition);
    }

    field(40; myCalculatedField; Text[100])
    {
        Caption = 'My Calculated Field';
        Editable = false;
        FieldClass = FlowField;
        CalcFormula = lookup(otherTable.myAttribute where(otherTablePK = field("My Table FK"))); // This is a table join
    }
}
```
---
**FieldGroups**

If you want to have more columns appear when a dropdown list is called, or define a "Brick" (A carousel of card summaries) you can use a `FieldGroup`. Fields groups are declared after the `Key` section of your table, and are just a list of fields or columns you want to display.
``` al
fieldgroups
{
    fieldgroup(DropDown; column1, column2, column3, etc...) // The PK and name are included by default
    {
    }

    fieldgroup(Brick; field1, field2, field3, field4, field5, field6)
    {
    }
}
```
To show an image on a brick you must include a field of type `Media`, `MediaSet`, or `BLOB` as the last field.
The layout of a brick is generated automatically based off of the number of fields:

![brick layout](https://docs.microsoft.com/en-us/learn/modules/work-with-tables/media/brick-fieldgroup-positions-ss.png)

---
### ExtendedDatatype Property
[back to the top](#application-language-cheat-sheet)

This property allows you to give fields special formatting.

- **None** - Default
- **PhoneNo** - The field will handle a phone number and display a hyperlink when not editable.
- **URL** - The field will handle links and display as a hyperlink when not editable.
- **EMail** - The field will handle emails and display as a hyperlink when not editable.
- **Ratio** - The field will act like a progress bas, but is not supported on the web client.
- **Masked** - The characters in the field will display as dots.
- **Person** - The field will act as media representing a person. When left blank it will display a silhouette.

---
### Table Relations
[back to the top](#application-language-cheat-sheet)

These are used to create a lookup in a different table via a dropdown menu.
``` al
field(1; myAttribute; Code[10])
{
    Caption = 'looking up "myAttribute" from "myTable"';

    TableRelation = myTable;

    // You can also filter
    TableRelation = myTable WHERE (myAttribute = filter(< 10000));
}
```
---
### Calculated fields
[back to the top](#application-language-cheat-sheet)

To create a calculated field change the `FieldClass` to a type `FlowField`. Then you must define the `CalcFormula` property with one of the following values:

- **Sum** - The sum of a specified column (Datatype: Decimal).
- **Lookup** -  Looks up a value in a different table (Datatype: any).
- **Count** - Counts the number of records from a specified collection (Datatype: integer).
- **Exist** - Indicates if a record exists in a specified collection (Datatype: boolean).
- **Average** - Averages the values from a specified collection (Datatype: Decimal).
- **Min** - Finds the smallest value in a specified collection (Datatype: any).
- **Max** - Finds the largest value from a specified collection (Datatype: any).

``` al
field(id; myAttribute; datatype)
{
    Caption = 'calculated field';
    Editable = false;
    FieldClass = FlowField;
    CalcFormula = Count ("myAttribute" Where (someCondition));
}
```
---
### Table Extensions
[back to the top](#application-language-cheat-sheet)

If you want to add functionality to an existing table you need to make a table extension. You can add more fields, modify existing fields, add new secondary keys, and add or modify triggers.

To modify a field you use `Modify(originalField){ }`.

To add new keys you define them the same as you would a secondary key but, there are some limitations. A new key *cannot* contain fields from the base table and the extension but you can have fields from the base table and the extension in different keys. Additionally, you can add a key with the same name as a key on the base table as long as the new key doesn't have fields from the base table.

---
## Pages
### Page Types
[back to the top](#application-language-cheat-sheet)

 - **Card** - A card page is used for every master table and is an editable form and will only display one record at a time.
 - **List** - A list page is usually read-only and displays a list of records in a list form.
 - **Document** - A document page is similar to a card page but is used to enter document data (like a sales order). Because pages can only be linked to one table, these pages are usually linked to a join table.
 - **ListPart** - A list part page is used to have a list of records on a different page (like the sales lines on a sales order). These pages are typically linked to a "list" table to maintain the one table per page rule.
  - **CardPart** - Similarly to a `ListPart` a `CardPart` is used to display information that might be usefull from a table that is not linked to the page that the `CardPart` is displayed on (often used in the "factbox area").
 - **HeadlinePart** - A head line part is displayed at the top of a `RoleCenter` and is used to show important insights.
 - **RoleCenter** - A rolecenter page is the main page for a user in BC, it is used as their starting point or dashboard. Rolecenters are not linked to any table, but use page parts to display their information.
 - **Worksheet** -  A worksheet is where a user will enter information into a list of records (like journals).
 - **ConfirmationDialog** - These are used to display a message to the user that requires a yes/no response.
 - **StandardDialog** - A regular dialog popup that the user can cancel, sometimes used to start a process or task.
 - **ListPlus** - A `ListPlus` is a named collection of `ListParts`.
 - **Navigate** - Navigate pages are typically used to create wizards.
 - **API** - These pages are used to create RESTFUL services and are not displayed in any user interface, more information [here](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/devenv-api-pagetype).

 ---
 ### Page Properties
 [back to the top](#application-language-cheat-sheet)

 - **PageType** - This is used to define the layout and thus the role of your page. See the [Page Types](#page-types) for a list of the available page types.
 - **CardPageId** - This is used to define the page that will open when a user selects a record from a list.
 - **SourceTable and SourceTableView** - `SourceTable` is used to define the table that the page is linked to and will display information from. `SourceTableView` allows you to sort and filter the records that will be displayed.
 - **InsertAllowed, ModifyAllowed, and DeleteAllowed** - These properties define wheather you want the user to be able to perform those specific operations. The default for these properties is `yes`.
 - **DataAccessIntent** - Is used for performance reasons and defines wheather the accessed records should be sent as a `ReadOnly` replica. This can only be used on `Page`, `Report`, and `Query` type pages. If a insert, delete, or modify operation is attempted on a replica it will throw an error. The two values are: `ReadOnly` and `ReadWrite` which specify the intent to the server.
 - **UsageCategory** - This is used to allow a user to be able to search for your page. You can use the following values: `Administration`, `Documents`, `History`, `Lists`, `None`, `ReportsAndAnalysis`, and `Tasks` depending on your usecase. List pages usually have a `UsageCategory` set and the `ApplicationArea` should be set at the page level. Card pages should have the `UsageCategory` set to **`None`** as you most likely want the user to access this page from a list page.

 ---
 ### Page Parts
 [back to the top](#application-language-cheat-sheet)

 To link page parts to a page use `Part(partName; partSource)`:
 ``` al
part(myPart; myPartPage)
{
    SubPageLink = "No." = FIELD("No."),
                  myTableField = FIELD(myPageField),
                  etc...;

    SubPageView = myFilter | mySort;
}
```
`SubPageLink` is used to link the fields from the table on the pagePart to the fields on the page the part is displayed on.
`SubPageView` is used to define any filters or sorting.

---
### Field Properties
[back to the top](#application-language-cheat-sheet)

- **NotBlank and ShowMandatory** - `NotBlank` is used to define a field as required and will display an error if that field is left blank. `ShowMandatory` displays a visual indication that a field is required but will not display an error if that field is left blank.
- **UpdatePropagation** - This property is used to define what should happen when a subpage is modified. It has two values `Subpage` which will only modify the subpage and `Both`, which will modify both the subpage and the main page.
- **ApplicationArea** - This property is found in various other places throughout the code and defines weather or not a control (in this case) should be shown or hidden, based off of the users license. If there are multiple application areas enabled in a session, any controls that do *not* have the `ApplicationArea` property defined will *not* be shown.

---
### Page Extensions
[back to the top](#application-language-cheat-sheet)

Just like you can extend tables you can extend pages. In a page extension you can add new fields and modify some properties of existing fields as well as some of the pages properties.

In the layout section of the extension you can use several keywords:
- **addfirst(area|group)** - Allows you to define the control(s) that will be positioned first in the specified area or group.
- **addlast(area|group)** - Allows you to define the control(s) that will be positioned last in the specified area or group.
- **addafter(group|control)** - Allows you to define the control(s) that will be added directly after the specified group or control.
- **addbefore(group|control)** - Allows you to define the control(s) that will be added directly before the specified group or control.
- **modify(control)** - Used to modify the properties of an existing control.
- **movefirst(area|group; control(s))** - Used to move the specified controls to the start of the specified area or group.
- **movelast(area|group; control(s))** - Used to move the specified controls to the end of the specified area or group.
- **moveafter(group|control; control(s))** - Used to move the specified controls directly behind the specified group or control.
- **movebefore(group|control; control(s))** - Used to move the specified controls directly before the specified group or control.

The following is a list of page properties that can be modified with a page extension:
<details>
    <summary>
        click to show
    </summary>

- AdditionalSearchTerms
- Caption
- DataCaptionExpression
- Description
- Editable
- InstructionalText
- PromotedActionCategories
</details>

The following is a list of field properties that can be modified with a page extension:
<details>
    <summary>
        click to show
    </summary>

- ApplicationArea
- AssistEdit
- BlankZero
- Caption
- CaptionClass
- ClosingDates
- Description
- Enabled
- Editable
- Visible
- Width
- HideValue
- Importance
- ShowCaption
- ShowMandatory
- QuickEntry
- ToolTip
- Style
- StyleExpr
</details>

The following is a list of action and actionGroup properties that can be modified with a page extension
<details>
    <summary>
        click to view
    </summary>

- Caption
- Tooltip
- Description
- Enabled
- Visible
- ApplicationArea
- Promoted
- PromotedIsBig
- PromotedOnly
- PromotedCategory
- ShortcutKey
</details>

---
