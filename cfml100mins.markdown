# CFML in 100 minutes

ColdFusion Markup Language (CFML) is a web programming language, which is especially suited for new developers as it was written to make a programmer's job easy and not care if the computer's job is hard. In this brief introduction we'll look at key language features you need to get started.

1.  Syntax
2.  Variables
3.  Components, Methods, and Parameters
4.  Strings
5.  Numbers
6.  Queries
7.  Arrays
8.  Structures
9.  Conditionals
    1.  If, Else If, & Else
    2.  Looping

10. Nothingness & Null

## CFML History

Although many people think of ColdFusion, or CFML, as an old programming language, Allaire, Macromedia, and Adobe have all devoted resources to its continued improvement. [ColdFusion](http://www.adobe.com/coldfusion) originated as proprietary technology, however, the availability of competing open source products like [Railo](http://www.getrailo.com/) and [OpenBD](http://www.openbluedragon.org/) has made CFML more widely available. 

In 1995 Jeremy and JJ Allaire invented ColdFusion to make it easier to connect simple HTML pages to a database. ColdFusion now includes advanced features for enterprise integration and application development. When ColdFusion was originally released, it was adopted in both the government and private sector. 

CFML tag syntax resembles HTML and the CFML script syntax, CFScript, resembles ECMAScript (JavaScript). You may want to focus on either the tag or script based examples depending on your comfort level.

And you want to learn CFML so here goes!

## 1. Syntax

There are two ways to write CFML code. You can use tag or script syntax. For the examples, please focus on one or the other so this tutorial is not confusing. 

CFML includes a set of instructions you use in pages. You will write one or more instructions in a file then run the file through a CFML engine. Three CFML instructions we will use in this tutorial are ```CFSET```, ```CFOUTPUT```, and ```CFDUMP```. ```CFSET``` is used to create a variable and assign it a value. Also ```CFSET``` is used to call methods. ```CFOUTPUT``` displays a variable's value. ```CFDUMP``` is used to display the contents of simple and complex variables, objects, components, user-defined functions, and other elements.

We might have a file named _myprogram.cfm_ and _Sample.cfc_ like this:

### Tag Syntax

#### myprogram.cfm

```cfm
<cfset s = New Sample() />
<cfoutput>#s.hello()#</cfoutput>
```

#### Sample.cfc

```cfm
<cfcomponent>
 <cffunction name="hello">
  <cfreturn "Hello, World!" />
 </cffunction>
</cfcomponent>
```

### Script Syntax

#### myprogram.cfm

```cfm
<cfscript>
s = New Sample();
writeOutput(s.hello());
</cfscript>
```

#### Sample.cfc

```cfm
component {
 public string function hello(){
  return( "Hello, World!" );
 }
}
```

For the script example, _myprogram.cfm_ would have beginning/closing ```<cfscript>``` tags around the instructions, however, the script-based _Sample.cfc_ does not require ```<cfscript>``` tags around the instructions.

### PHP Syntax

#### myprogram.php

```php
<?php
 require("Sample.php");
 $s = new Sample();
 echo $s->hello();
?>
```

#### Sample.php

```php
<?php
 class Sample
 {
  public function hello() {
  return "Hello, World!";
  }
 }
?>
```

### Ruby Syntax

#### myprogram.rb

```rb
class Sample
 def hello
 "Hello, World!"
end

s = Sample.new
puts s.hello
```

## 2. Variables

Everything needs a name so we can refer to it. A variable, like in math, is just a name for a piece of data. In CFML, variables are very flexible and can be changed at any time. Variables are assigned using a single equals sign ( = ) where the **right** side of the equals sign is evaluated first, then the value is assigned to the variable named on the **left** side of the equals.

Go into a CFML file, enter in these example instructions, and observe the output that CFML gives you back:

#### Tag

```cfm
<cfoutput>
<cfset a = 5 />
a = #a#<br/>
<cfset b = 10 + 5 />
b = #b#<br/>
<cfset c = 15 + a + b />
c = #c#<br/>
<cfset b = c * a />
b = #b#<br/>
<cfset d = "Hello, " />
d = #d#<br/>
</cfoutput>
```

#### Syntax

```cfm
<cfscript>
a = 5;
writeOutput("a = #a#<br/>");
b = 10 + 5;
writeOutput("b = #b#<br/>");
c = 15 + a + b;
writeOutput("c = #c#<br/>");
b = c * a;
writeOutput("b = #b#<br/>");
d = "Hello, ";
writeOutput("d = #d#<br/>"); 
</cfscript>
```

In this second example, we assume the first example is present.

#### Tag

```cfm
<cfoutput>
<cfset e = "World!" />
e = #e#<br/>
<cfset f = d & e />
f = #f#<br/>
<cfset g = d & a & e />
g = #g#<br/>
<cfset b = "hi!" />
b = #b#<br/>
</cfoutput>
```

#### Syntax

```cfm
<cfscript>
e = "World!";
writeOutput("e = #e#<br/>");
f = d & e;
writeOutput("f = #f#<br/>");
g = d & a & e;
writeOutput("g = #g#<br/>");
b = "hi!";
writeOutput("b = #b#<br/>");  
</cfscript>
```

*The first few lines in the first example are simple if you've done any programming language before, but the last few get interesting when combining strings and numbers. The code looks a little messy since after each instruction we output a variable.

## 3. Components, Methods, and Parameters

### Components (aka Objects or Classes)

In CFML, a ColdFusion component (CFC) is a file that contains data and methods. Components are the building blocks for objects in CFML. Objects know information, called "attributes", and can do actions, called "methods". In ColdFusion the ```cffunction``` tag is used to define methods within a tag-based CFC. In a script-based CFC, you use the ```function``` keyword to define a method.

For an example of an object, think about you as a human being. You have attributes like height, weight, and eye color. You have methods like walk, run, wash dishes, and daydream. Different kinds of objects have different attributes and methods. In the next sections we'll look at a few specific instructions in CFML.

In CFML we define an object using the ```cfcomponent``` instruction (```component``` in script-based CFCs) and save the file as _.cfc_. Here's an example defining the object type _PersonalChef.cfc_:

#### Tag

```cfm
<cfcomponent>

</cfcomponent>
```

#### Syntax

```cfm
component {

}
```

### Methods

Inside the CFC we usually define one or more methods using the ```cffunction``` or ```function``` instruction like this:

#### Tag

```cfm
<cfcomponent>
 <cffunction name="makeToast">
  <cfset makeToast = "Making your toast!" />
 </cffunction>
</cfcomponent>
```

#### Syntax

```cfm
component {
 public string function makeToast(){
  makeToast = "Making your toast!";
 }
}
```

Inside the ```cffunction```/```function``` instruction we would put the code for how the chef should make the toast.

### Classes

A "class" is an abstract idea, it defines what all objects of that type can know and do. Think of the chair you're sitting in. It’s not an abstract chair, it is an actual chair. While a "Chair" class would represent a chair in the abstract sense, we would call the actual chair an "instance" of the "Chair" class. It is a *realization* of the idea of the Chair. It has measurable attributes like height, color, and weight. The class Chair, on the other hand, is *abstract*. It is abstract in the sense that the class's attributes, such as height, color, and weight, cannot be determined ahead of time.

Once we define a class, we create an instance of that class like this:

#### Tag

```cfm
<cfset frank = New PersonalChef() />
```

#### Syntax

```cfm
frank = New PersonalChef();
```

We're calling the ```New``` instruction on the class ```PersonalChef``` and storing it into the variable named _frank_. Once we have the instance, we can set or get its attributes and call its methods. Methods are called by using this syntax: ```object.method_name()```. So if you have a person named "frank" you would tell him to make toast by calling ```frank.makeToast()```.

The ```New``` instruction creates a new instance of the object and calls its ```init()``` method (if existing). Any arguments supplied to the object will be passed to the ```init()``` method. The ```init()``` method should return the object instance using ```<cfreturn this />``` in order to have the same expected behavior as the ```CreateObject``` instruction. If no ```init()``` method exists, the object will be returned normally.

### Method Parameters

Sometimes methods take one or more *parameters* telling them **how** to do what they're supposed to **do**. For instance, I might call ```frank.makeToast("burned")``` for him to burn my toast. Or maybe he has another method where I call ```frank.makebreakfast("toast","eggs")``` for him to make both toast and eggs. Parameters can be numbers, strings, or any kind of object. When a method takes a parameter we use the ```cfargument``` instruction, it'll look like this:

#### Tag

```cfm
<cfcomponent>
 <cffunction name="makeToast" returnType="string">
  <cfargument name="color" required="yes">
  <cfset makeToast = "Making your toast #arguments.color#!" />
 </cffunction>
</cfcomponent>
```

#### Syntax

```cfm
component {
 public string function makeToast(required String color){
  makeToast = "Making your toast #arguments.color#!";
 }
}
```

The method is requiring us to pass in a "color" telling it how to do the method "makeToast".

### Return Value

In CFML, every time you call a method you won't necessarily get a value back. By default, a CFML method returns *nothing*. We'll talk about *nothing* and "null" in the last section of "CFML in 100 minutes". If you called ```makeToast``` method above like ```<cfset result = frank.makeToast("burned") />``` or ```set result = frank.makeToast("burned");```, and tried to output "result" you should have seen "Variable RESULT is undefined".

To return data, we use ```cfreturn``` to instruct the method to return a "value". Since that wasn't in the last instruction before the ending ```cffunction``` in your ```makeToast``` method, you received *nothing* and tried to putting that into the "result" variable.

For the purposes of our next section I’m going to return the chef instance itself from the method. If you wanted to picture the metaphor, imagine you are looking at your chef "frank". You say, "Frank, go make my toast", he tells you he's making the toast, goes to make it, then comes back to you to receive more instructions. He's **returning himself** to you. Here's how we implement it in code:

#### Tag

```cfm
<cfcomponent>
 <cffunction name="makeToast" returnType="component">
  <cfargument name="color" required="yes">
   <cfset this.makeToast = "Making your toast #arguments.color#!" />
   <cfreturn this />
 </cffunction>
</cfcomponent>
```

#### Syntax

```cfm
component {
 public component function makeToast(required String color){
  this.makeToast = "Making your toast #arguments.color#!";
  return this;
 }
}
```

## 4. Strings

In CFML a string is defined as a quote ( **'** or **"** ) followed by zero or more letters, numbers, or symbols and followed by another quote ( **'** or **"**  ). Some simple strings would be **hello** or **This sentence is a string!**. Strings can be anything from "", the empty string, to really long sets of text. This whole tutorial, for instance, is stored in a string. Strings have a few important instructions that we'll use.

### Len
* Call ```Len``` on a string to get back the number of characters in the string. For instance ```Len("Hello")``` would give you back **5**.

### Replace
* The ```Replace``` instruction replaces occurrences of **substring1** in a string with **substring2**, in a specified scope. The search is case sensitive and the scope default is one. For instance, ```Replace("Hello", "e", "")``` would give you back **hllo** after replacing the _first occurrence of e_, or ```Replace("Good Morning!", "o", "e", "All")``` would give you **Geed Merning!** 

### RemoveChars 
* Call ```RemoveChars``` to remove characters from a string. For instance, ```RemoveChars("hello bob", 2, 5)``` would give you back **hbob**. 

### Mid
 
* The ```mid``` instruction extracts a substring from a string. For instance, I could call ```Mid("Welcome to CFML Jumpstart",4,12)``` and it would give you back: **come to CFML**.

Experiment with the following samples in a CFML file.

#### Tag

```cfm
<cfset tester = "Good Morning Everyone!" />
<cfoutput>#len (tester)#<br></cfoutput>
<cfoutput>#Replace (tester, "o", "e", "All")#<br></cfoutput>
<cfoutput>#RemoveChars (tester, 2, 5)#<br></cfoutput>
<cfset t2 = "sample,data,from,a,CSV" />
<cfset t3 = Mid(t2,8,len(t2)) />
<cfoutput>#t3#<br></cfoutput>
```

#### Syntax

```cfm
<cfscript>
tester = "Good Morning Everyone!";
writeOutput ("#len (tester)#<br/>");
writeOutput (Replace (tester, "o", "e", "All") & "<br/>");
writeOutput (RemoveChars (tester, 2, 5) & "<br/>");
t2 = "sample,data,from,a,CSV";
t3 = Mid (t2,8,len (t2));
writeOutput (t3 & "<br/>");
</cfscript>
```

Often a string may store a list like the *t2* variable in the last example. A string for storing a list isn't the best for performance and usage. Using an array for a list is so much better. We can convert a list into an *array* using *ListToArray*. We'll discuss arrays in an upcoming section. Try out these next examples in the CFML file assuming we have the code from the last example:

#### Tag

```cfm
<cfset t4 = ListToArray(t3) />
<cfoutput>
#t4[2]#
</cfoutput>
```

#### Syntax

```cfm
<cfscript>
t4 = ListToArray(t3);
writeOutput(t4[2]);
</cfscript>
```

The numbers inside the "[]" brackets specify which item of the array you want pulled out. They're numbered starting with 1. So the first example pulls out the "2" array item. This "t4" array contains position "1", the beginning of the list, up to position "4", the ending of the array.

### Combining Strings and Variables

It is extremely common that we want to combine the value of a variable with other strings. For instance, lets start with this example string:

**Happy Saturday!**

When we put that into the CFML file, it just spits back the same string. If we were writing a proper program we might want it to greet the user when they start the program by saying **Happy** then the day of the week. So we can't just put a string like **Happy Saturday!** or it'd be saying Saturday even on Tuesday.

What we need to do is combine a variable with the string. There are two ways to do that. The first approach is called *string concatenation* which is basically just adding strings together:

In the first line we setup a variable to hold the day of the week. Then we'll printed the string *Happy* combined with the value of the variable "today" and the string *!*. You might be thinking, "What was the point of that since we still wrote *Saturday* in the first line?" Ok, well, if you were writing a real program you'd use CFMLs built-in date instructions like this:

```cfm
today = DayOfWeek(Now());
```

```Now()``` gets the current date and time of the computer running the ColdFusion server. "DayOfWeek" returns an integer in the range 1 (Sunday) to 7 (Saturday) for the day of the week. We still don't have the day of week as string. Try this:

#### Tag

```cfm
<cfset today = DayOfWeekAsString(DayOfWeek(Now())) />
<cfset message = "Happy " & today & "!" />
<cfoutput>
#message#
</cfoutput>
```

#### Syntax

```cfm
<cfscript>
today = DayOfWeekAsString(DayOfWeek(Now()));
message = "Happy " & today & "!";
writeOutput(message);
</cfscript>
```

Great, no errors and our output looks correct. "DayOfWeekAsString" did the trick. There is another string combination called *string interpolation*.

**String interpolation** is the process of sticking data into the middle of strings. We use the symbols ```#``` around the "variable" where in a string the value should be inserted. Inside those hashes we can put any variable and output it in that spot. Our previous example "message" could be rewritten like this:

#### Tag

```cfm
<cfset message = "Happy #today#!" />
```

#### Syntax

```cfm
message = "Happy #today#!";
```

If you compare the output you'll see the second example gives the exact same results. The code itself is a little more compact and, personally, I find it much easier to read.

Basically *interpolating* means evaluate the code inside this ```#``` wrapper and put it into the string.

## 5. Numbers

There are two basic kinds of numbers in CFML: integers (whole numbers) and real (numbers with a decimal point). For our workshop, we'll only be dealing with integers. You can use normal math operations with integers including "+", "-", "/", and "*". The "++" operator can be used to increment a number. It is also the only one we will use to control a loop. We will talk more about Conditional Looping in section 9. Try out this example for the "++" operator:

#### Tag

```cfm
<cfset loop = 0 />
<cfoutput>
 <cfloop condition="loop LT 5" >
  #loop# Hello, world!<br>
  <cfset loop++ />
 </cfloop>
 I am here!<br>
</cfoutput>
```

#### Syntax

```cfm
<cfscript>
for (loop = 0 ; loop < 5 ; loop++)
 WriteOutput("#loop# Hello, world!<br>");
WriteOutput("I am here<br>");
</cfscript>
```

In this next example we're using the ```cfloop``` instruction with a multiple instructions inside the condition. The CFML script syntax looks for the starting ```{``` and the ending ```}```. Each instruction between the beginning ```{```and ending ```}``` will be executed if the condition is true.

In the tag example there's no need to manage the index inside the loop if you're simply stepping through one item at a time. You can use the ```from``` and ```to``` arguments, and ColdFusion will simply loop from the first value to the second, and automatically increment the variable in the ```index``` argument.

Try this example with multiple instructions:

#### Tag

```cfm
<cfset loop = 0 />
<cfoutput>
<cfloop index="loop" from="0" to="4">
 #loop# Good Morning!
 ...is it lunch time yet?<br>
</cfloop>
</cfoutput>
```

#### Syntax

```cfm
<cfscript>
loop = 0; 
while (loop < 5) { 
 WriteOutput("#loop# Good Morning! ");
 WriteOutput("...is it lunch time yet?<br>");
 loop++;
}
</cfscript>
```

It's also possible to go through a loop and step over more than one value at a time. The following examples will step through the loop and increase the "loop" index by two for each time through the loop.

#### Tag

```cfm
<cfset loop = 0 />
<cfoutput>
<cfloop index="loop" from="0" to="4" step="2">
 #loop# Good Morning!
 ...is it lunch time yet?<br>
</cfloop>
</cfoutput>
```

#### Syntax

```cfm
<cfscript>
loop = 0;
while (loop < 5) {
 WriteOutput("#loop# Good Morning! ");
 WriteOutput("...is it lunch time yet?<br>");
 loop++;
}
</cfscript>
```

## 6. Queries

A query is a request to a database. The query can ask for information from the database, write new data to the database, update existing information in the database, or delete records from the database. Each time you query a database with CFML, you get the data (the recordset) and the query variables; together they make up the query object. ```cfquery``` passes SQL statements to the "datasource". The "datasource" is set in the ColdFusion administrator.

#### Tag

```cfm
<cfquery name="GetBreakfastItems" datasource="pantry"> 
 SELECT QUANTITY, ITEM 
 FROM CUPBOARD 
 ORDER BY ITEM 
</cfquery> 
```

#### Syntax

```cfm
<cfscript>
queryService = new Query ();

queryService.setName("GetBreakfastItems"); 
queryServ.setDatasource("pantry"); 
queryService.setSQL("
SELECT QUANTITY, ITEM 
FROM CUPBOARD 
ORDER BY ITEM
");

GetBreakfastItems = queryService.execute().getResult(); 
</cfscript>
```

In order to display the data from our query, we need to loop through the rows, and display each row. This is usually done in a ```<cfoutput>``` tag like so:

```cfm
<cfoutput query="GetBreakfastItems">
There are #GetBreakfastItems.Quantity# #GetBreakfastItems.Item# in the pantry<br />
</cfoutput>
```

While it's not strictly necessary to prepend the recordset name before the column name inside the ```<cfoutput>```, it's strongly recommended that you do in order to prevent referencing the wrong variable scope.

You can also loop through a query using standard loop constructs, though they differ when using tags and script.

#### Tag

```cfm
<cfloop query="GetBreakfastItems">
 <cfoutput>There are #GetBreakfastItems.Quantity# #GetBreakfastItems.Item# in the pantry<br /></cfoutput>
</cfloop>
```

#### Syntax

```cfm
<cfscript> 
for (x = 1; x <= GetBreakfastItems.RecordCount; x++) { 
 writeOutput("There are #GetBreakfastItems.Quantity[x]# #GetBreakfastItems.Item[x]# in the pantry<br />");
} 
</cfscript>
```

When looping through a query with ```<cfloop>```, you need to make sure you have a ```<cfoutput>``` tag around your content (or around the loop) to ensure the ColdFusion instructions are recognized.

When looping through a query in ```cfscript```, you'll need to reference the query just like you would a multidimensional array, using the counter set up in your for statement to pick up the correct row from the recordset. So the syntax becomes "recordsetName.ColumnName[rowNumber]".

## 7. Arrays

Often we need to organize a group and put them into a *collection*. There are two main types of collections: **arrays** and **structures**.

An **array** is a number-indexed list. Picture a city block of houses. Together they form an array and their addresses are the **indices**. Each house on the block will have a unique address. Some addresses might be empty, but the addresses are all in a specific order. The **index** is the address of a specific element inside the array. In CFML the index always begins with "1". An array is defined in CFML as an opening "[" then zero or more elements, and a closing "]". Try out this code:

#### Tag

```cfm
<cfset favorite_colors = ["red","blue","green","black","brown"] />
<cfdump var="#favorite_colors#" /><br>
<cfdump var="#favorite_colors[2]#" /><br>
<cfdump var="#ArrayLen(favorite_colors)#" /><br>
```

#### Syntax

```cfm
<cfscript>
favorite_colors = ["red","blue","green","black","brown"];
writeDump(favorite_colors);
writeOutput("<br>");
writeDump(favorite_colors[2]);
writeOutput("<br>");
writeDump(var=ArrayLen(favorite_colors));
</cfscript>
```

Keep going with these, but try to understand what each instruction is doing before we explain them:

#### Tag

```cfm
<cfset ArrayAppend(favorite_colors, "orange") />
<cfset favorite_colors[3]="yellow" />
<cfdump var="#favorite_colors#" /><br>
<cfset ArraySort(favorite_colors,"text") />
<cfset ArrayDeleteAt(favorite_colors, 2) /> 
<cfdump var="#favorite_colors#" /><br>
```

#### Syntax

```cfm
<cfscript>
ArrayAppend(favorite_colors, "orange");
favorite_colors[3] = "yellow";
writeDump(favorite_colors);
writeOutput("<br>");
ArraySort(favorite_colors,"text");
ArrayDeleteAt(favorite_colors, 2);
writeDump(var=favorite_colors);
writeOutput("<br>"); 
</cfscript>
```

In order to get add an element in the array you use the syntax ```ArrayAppend(array,"value")``` or ```arrayname[index] = "value"```. The first example of adding an array element is **with an instruction**. The second is updating an array element is **by assignment**. So looking at the final "favorite_colors" array:

* What's the index of **brown** ?
* What did the "ArraySort" instruction do to the collection?
* What does "ArrayLen" instruction return?

There are lots of cool things to do with an array. You can rearrange the order of the elements using the ```ArraySort``` instruction like we did in the last example. You can iterate through each element using the ```cfloop``` instruction. You can find the address of a specific element by using the "arrayName[index]" instruction. You can ask an array if an element is present with the "ArrayIsDefined" instruction. Try out this example that brings a bunch of things together: 

#### Tag

```cfm
<cfoutput>
<ul>
 <cfloop array="#favorite_colors#" index="target" >
 <li>
 #target# is #len(target)# letters long.
 </li>
 </cfloop>
</ul>
<cfdump var="#ArrayIsDefined(favorite_colors,4)#" />
</cfoutput>
```

#### Syntax

```cfm
<cfscript>
writeOutput ("<ul>");
index = favorite_colors.iterator ();
while (index.hasNext ()){
 target = index.next ();
 writeOutput ("<li>#target# is #len (target)# letters
long.</li>");
}
writeOutput ("</ul>"); 
writeDump (var=ArrayIsDefined (favorite_colors,4));
</cfscript>
```

We use arrays whenever we need a list where the elements are in a specific order.

## 8. Structures

A structure is a *collection of data* where each element of data is addressed by a name. As an analogy, think about a classroom of children. Under ideal circumstances, each student has a name and can be found by using that name. We might look in a science classroom for a child named Joey and that would result in finding an actual student. We could write this like "science["Joey"]" which could be read as "look in the collection named "science" and find the thing named "Joey**.

A structure is an unordered collection, it’s just a bunch of data collected together where each one has a unique name/key. Structures have a slightly more complicated syntax:

#### Tag

```cfm
<cfset ages = {jack = 11, brian = 12, tracy = 11} />
<cfset ages.joey = 12 /> 
<cfset ages["jill"] = 14 />

<cfdump var="#ages#" />

<cfoutput>
Joey is #ages["joey"]# years old.
</cfoutput>
```

#### Syntax

```cfm
<cfscript>
ages = {jack = 11, brian = 12, tracy = 11};
ages.joey = 12;
ages["jill"] = 14;

writeDump (var=ages);
writeOutput ("Joey is #ages["joey"]# years old.");
</cfscript>
```

Here we create a structure named "ages". Structures are made up what are called key-value pairs. The **key** is used as the address and the **value** is the object at that address. In the "ages" structure we have keys including **joey** and **jill** and values including "12" and "14". When creating a structure using "{}" the key and value are linked by the ```=``` symbol. So to create a structure, the structures start with a curly bracket ```{```, have zero or more entries made up of a *key*, ```=```, and a *value* separated by commas, then end with a closing curly bracket ```}```.

#### Tag

```cfm
<cfset ages["jimmy"] = 14 />
<cfset ages["joey"] = 9 />
<cfdump var="#ages#" />
```

#### Syntax

```cfm
<cfscript>
ages["jimmy"] = 14;
ages["joey"] = 9;
writeDump (var=ages);
</cfscript>
```

In the second chunk of the example, we add a new key and value to the structure. Since the **jimmy** key wasn't in the original structure, it's added with the value of "14". If the key **jimmy** already existed then the value would be replaced by "14". Every key in a structure must be unique! In the second line we reference the key **joey** which already exists, so the value gets replaced with the "9". Then, just to show you the state of the structure, we dump out the list of keys and the list of values.

#### Tag

```cfm
<cfset StructSort(ages)>

<cfloop collection="#ages#" item="student">
 <cfoutput>"#student# is #ages[student]# years old."<br />
 </cfoutput>
</cfloop>
```

#### Syntax

```cfm
<cfscript>
StructSort(ages);
for(student in ages) {
 WriteOutput ("#student# is #ages[student]# years old.<br />");
}
</cfscript>
```

The last chunk of the example used StructSort to get the sorted array "students" from "ages". Then, it iterated through the "students" array using a loop and gave each element of the array the name "student". It then printed out one line with that student’s name and age from "ages".

While that last part probably seemed complicated, it's just to illustrate that structures are unordered.

## 9. Conditionals

Conditional statements evaluate to "true" or "false" only. The most common conditional operators are ```==``` (equal), ```!=``` (not equal), ```>``` (greater than), ```>=``` (greater than or equal to), ```<``` (less than), and ```<=``` (less than or equal to). You can also define the operators as abbreviations: ```EQ```, ```NEQ```, ```GT```, ```GTE```, ```LT```, and ```LTE```.

Some instructions return a "true" or "false", so they're used in conditional statements, for example, "IsArray" which is "true" only when the variable is an "array". Structures have an instruction named ```StructKeyExists``` which returns "true" if a key is present in a structure.

### 9. 1. If, Else If, & Else

Why do we have conditional statements? Most often its to control conditional instructions, especially "if" / "else if" / "else" structures. Lets write an example by adding a method to our **PersonalChef** class:

#### Tag

```cfm
<cffunction name="water_boiling" returnType="component">
 <cfargument name="minutes" type="numeric" required="yes">

 <cfif (arguments.minutes LT 7)>
  <cfset this.status = "The water is not boiling yet." />
  <cfelseif (arguments.minutes EQ 7)> 
  <cfset this.status = "It's just barely boiling." />
 <cfelseif (arguments.minutes EQ 8)>
  <cfset this.status = "It's boiling!" />
 <cfelse>
  <cfset this.status = "Hot! Hot! Hot!" /> 
 </cfif>
 <cfreturn this />
</cffunction>
```

#### Syntax

```cfm
public component function water_boiling(numeric minutes){
 if (arguments.minutes < 7) 
  this.status = "The water is not boiling yet.";
 
 else if (arguments.minutes == 7) 
  this.status = "It's just barely boiling.";
 
 else if (arguments.minutes == 8)
  this.status = "It's boiling!";
 
 else 
  this.status = "Hot! Hot! Hot!";
 
 return this;
}
```

Try this example using *5*, *7*, *8* and *9* for the values of *minutes*.

* When the *minutes* is 5, here is how the execution goes: Is it *true* that 5 is less than 7? Yes, it is, so print out the line *The water is not boiling yet.*.

* When the *minutes* is 7, it goes like this: Is it *true* that 7 is less than 7? No. Next, is it *true* that 7 is equal to 7? Yes, it is, so print out the line *It's just barely boiling*.

* When the *minutes* is 8, it goes like this: Is it *true* that 8 is less than 7? No. Next, is it *true* that 8 is equal to 7? No. Next, is it *true* that 8 is equal to 8? Yes, it is, so print out the line *It's boiling!*.

Lastly, when total is 9, it goes:" Is it "true" that 9 is less than 7?

No. Next, is it "true" that 9 is equal to 7? No. Next, is it "true" that 9 is equal to 8? No. Since none of those are true, execute the "else" and print the line "Hot! Hot! Hot!".

An "if" block has:

*   One "if" statement whose instructions are executed only if the
    statement is true
*   Zero or more "else if" statements whose instructions are executed
    only if the statement is true
*   Zero or one "else" statement whose instructions are executed if no
    "if" nor "else if" statements were true

Only *one* section of the "if" / "else if" / "else" structure can have its instructions run. If the "if" is "true", for instance, CFML will never look at the "else if". Once one block executes, that’s it.

### 9. 2. Looping

Another time we use conditional statements is when we want to repeat a set of instructions. Try out this simple example by adding it to your _PersonalChef.cfc_:

#### Tag

```cfm
<cffunction name="countdown" returnType="component">
 <cfargument name="counter" type="numeric">
 <cfset this.timer = "" />
 <cfloop condition="#arguments.counter# GT 0">
  <cfset this.timer &= "The counter is #arguments.counter#.<br>" />
  <cfset arguments.counter-* />
 </cfloop>
 <cfreturn this />
</cffunction>
```

#### Syntax

```cfm
public component function countdown (numeric counter){
 this.timer = "";
 while (counter GT 0) { 
  this.timer &= "The counter is #arguments.counter#.<br>";
  arguments.counter-;
 }
 return this;
}
```

See how that works? The "counter" starts out as whatever parameter we
pass in. The "while" instruction evaluates the conditional statement
"arguments.counter GT 0" and finds that yes, the counter is greater than
zero. Since the condition is true, execute the instructions inside the
loop. First print out **The counter is #Arguments.counter#** then take
the value of "Arguments.counter" and subtract one from it. Next, we overwrite the previous value of "Arguments.counter" with the new value. Then the loop goes back to the
"condition" / "while" statement. Is it still true? If so, print the line
and subtract one again. Keep repeating until the condition is false.

You can also combine conditional statements using logical operators. The
most common are known as "logical and" and "logical or". In CFML you can
write a "logical and" with either the word "and" or with double
ampersands like this: "&&". You can write a "logical or" with the word
"or" or with double pipes like this: "||". For each operation, the
symbolic representation ( "&&" and "||" ) is more common.

The #1 mistake people encounter when writing conditional statements is
the difference between ```=``` and ```==```.

*   ```=``` is an *assignment*. It means "take what's on the right side and
    stick it into whatever is on the left side" (or its *telling* not
    *asking*.)
*   ```==``` is a *question*. It means "is the thing on the right equal to
    the thing on the left" (or its *asking* not *telling*.)

## 10. Nothingness & Null

What is *nothingness*? Is there nothingness only in outer space? Really, when we think of *nothing* isn't it just the absence of something? Ok, that's too much philosophy

ColdFusion did not have a way of referring to nothingness until version 9. ColdFusion can receive a "NULL" value from an external source and maintain the "NULL" value until you try to use it. ColdFusion will convert the "NULL" into an empty string (in the case of queries) or potentially destroy the variable altogether. However now with greater support for "NULL" values, ColdFusion allows you to pass in and return a "NULL" value from a method. ```IsNull()``` instruction will test for "NULL" values and return "true" or "false".

If you have three eggs, eat three eggs, then you might think you have *nothing* , but in terms of eggs you have "0". Zero is something, it's a number, and it's *not nothing*.

A large percentage of the errors you encounter while writing CFML code will involve a variable not existing. You thought something was there, you tried to do something to it, and you can't do something to nothing so CFML creates an error. Lets rewrite our ```makeEggs``` method to  illustrate "NULL" :

#### Tag

```cfm
<cffunction name="makeEggs" returnType="component">
 <cfargument name="quantity" type="numeric">
 <cfif (IsNull(arguments.quantity)) />
  <cfset local.makeEggs = "How am I supposed to make nothingness number of eggs?" />
 <cfelse>
  <cfset local.makeEggs = "Making your #arguments.quantity# eggs!" />
  <cfset local.yourEggs = ArrayNew(1) />

  <cfloop condition="#ArrayLen(local.yourEggs)# LT #arguments.quantity#">
   <cfset ArrayAppend(local.yourEggs, "Making an Egg.") />
  </cfloop>
 </cfif>
 <cfreturn local />
</cffunction>
```

#### Syntax

```cfm
public component function makeEggs (numeric quantity){
 if (IsNull (arguments.quantity)) {
 local.makeEggs = "How am I supposed to make nothingness number of
eggs?";
 } else {
  local.makeEggs = "Making your #arguments.quantity# eggs!";
  local.yourEggs = ArrayNew (1);
  while (ArrayLen (local.yourEggs) < arguments.quantity)
   ArrayAppend (local.yourEggs, "Making an Egg.");
 }
 return local;
}
```

Reload the file, call ```frank.makeEggs(3)``` then try ```frank.makeEggs()```.

**TODO: Conclusion**
