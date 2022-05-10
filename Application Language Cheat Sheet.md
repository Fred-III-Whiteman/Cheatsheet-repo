# Application Language Cheat Sheet
[Official Documentation](https://docs.microsoft.com/en-us/dynamics365/business-central/dev-itpro/developer/devenv-dev-overview)

## Declaring Variables
```al-language
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
    logic;

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

**While loop**
``` al

```