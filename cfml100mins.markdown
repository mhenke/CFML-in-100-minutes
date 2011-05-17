# CFML in 100 minutes

ColdFusion Markup Language (CFML) is a great programming language for beginners because it was written to make the programmer's job easy and not care if the computer's job is hard. In this brief introduction weâ€™ll look at key language features you need to get started.

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

CFML is thought of by many as an old programming language, but ColdFusion actually has been continuously improved by Allaire, Macromedia, and now Adobe. The term *ColdFusion* is often used synonymously with *CFML*. [ColdFusion][1] originated as proprietary technology, however, it is becoming less closed through the availability of competing open source products like [Railo][2] and [OpenBD][3] . ColdFusion was invented by Jeremy and JJ Allaire in 1995. Their idea for ColdFusion was originally designed to make it easier to connect simple HTML pages to a database, but ColdFusion now includes advanced features for enterprise integration and application development.

When ColdFusion was originally released, it grew an audience quickly in the government and private sector. CFML tag syntax resembles HTML and the CFML script syntax resembles JavaScript. You may want to focus on either the tag or script based examples depending on your comfort level.

And you want to learn CFML so here goes!

## 1. Syntax

There are two ways to write CFML code. You can use tag or script syntax. For the examples, please focus on one or the other so this tutorial is not confusing. CFML includes a set of instructions you use in pages. You will write one or more instructions in a file then run the file through a CFML engine. Three CFML instructions we will use in this tutorial are 'CFSET', 'CFOUTPUT', and 'CFDUMP'. 'CFSET' is used to create a variable and assign it a value. Also 'CFSET' is used to call methods. 'CFOUTPUT' displays a variableâ€™s value. 'CFDUMP' is used to display the contents of simple and complex variables, objects, components, user-defined functions, and other elements.

We might have a file named 'myprogram.cfm' and 'Sample.cfc' like this:

### Tag Syntax

<table>
  <tbody>
    <tr>
      <td>
        myprogram.cfm
      </td>
      
      <td>
        Sample.cfc
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfset</span> <span class="nv">s</span> <span class="o">=</span> <span class="nv">New</span> <span class="nf">Sample</span><span class="p">()</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfoutput&gt;</span><span class="p">#</span><span class="nf">s.hello</span><span class="p">()#</span><span class="nb">&lt;/cfoutput&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfcomponent&gt;</span>
 <span class="nb">&lt;cffunction</span> <span class="nv">name</span><span class="o">=</span><span class="s2">"hello"</span><span class="nb">&gt;</span>
  <span class="nb">&lt;cfreturn</span> <span class="s2">"Hello, World!"</span> <span class="o">/</span><span class="nb">&gt;</span>
 <span class="nb">&lt;/cffunction&gt;</span>
<span class="nb">&lt;/cfcomponent&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

### Script Syntax

<table>
  <tbody>
    <tr>
      <td>
        myprogram.cfm
      </td>
      
      <td>
        Sample.cfc
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span>
<span class="nv">s</span> <span class="o">=</span> <span class="nv">New</span> <span class="nf">Sample</span><span class="p">();</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="nf">s.hello</span><span class="p">());</span>
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre>component {
 public string function hello(){
  return( "Hello, World!" );
 }
}
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

For the script example, 'myprogram.cfm' and 'Sample.cfc' would have beginning/closing '<cfscript>' tags around the instructions.

#### PHP Syntax

<table>
  <tbody>
    <tr>
      <td>
        myprogram.php
      </td>
      
      <td>
        Sample.php
      </td>
      
      <td>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="cp">&lt;?php</span>
<span class="k">require</span><span class="p">(</span><span class="s2">"Sample.php"</span><span class="p">);</span>
<span class="nv">$s</span> <span class="o">=</span> <span class="k">new</span> <span class="nx">Sample</span><span class="p">();</span>
<span class="k">echo</span> <span class="nx">s</span><span class="o">-&gt;</span><span class="na">hello</span><span class="p">();</span>
<span class="cp">?&gt;</span><span class="x"></span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="cp">&lt;?php</span>
<span class="k">class</span> <span class="nc">Sample</span>
<span class="p">{</span>
    <span class="k">public</span> <span class="k">function</span> <span class="nf">hello</span><span class="p">()</span> <span class="p">{</span>
        <span class="k">return</span> <span class="s2">"Hello, World!"</span><span class="p">;</span>
    <span class="p">}</span>
<span class="p">}</span>
<span class="cp">?&gt;</span><span class="x"></span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

#### Ruby Syntax

<table>
  <tbody>
    <tr>
      <td>
        myprogram.rb
      </td>
      
      <td>
        Sample.rb
      </td>
      
      <td>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">require</span> <span class="s1">'Sample.rb'</span>
<span class="n">s</span> <span class="o">=</span> <span class="no">Sample</span><span class="o">.</span><span class="n">new</span>
<span class="nb">puts</span> <span class="n">s</span><span class="o">.</span><span class="n">hello</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="k">class</span> <span class="nc">Sample</span>
  <span class="k">def</span> <span class="nf">hello</span>
    <span class="s2">"Hello, World!"</span>
  <span class="k">end</span>
<span class="k">end</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

For the Ruby syntax, part 1 would be first then followed by part 2 in 'my_program.rb'.

## 2. Variables

Everything needs a name so we can refer to it. A variable, like in math, is just a name for a piece of data. In CFML, variables are very flexible and can be changed at any time. Variables are assigned using a single equals sign ( = ) where the **right** side of the equals sign is evaluated first, then the value is assigned to the variable named on the **left** side of the equals.

Go into a CFML file, enter in these example instructions, and observe the output that CFML gives you back:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfoutput&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nv">a</span> <span class="o">=</span> <span class="m">5</span> <span class="o">/</span><span class="nb">&gt;</span>
a = <span class="p">#</span><span class="nv">a</span><span class="p">#</span><span class="nt">&lt;br/&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nv">b</span> <span class="o">=</span> <span class="m">10</span> <span class="o">+</span> <span class="m">5</span> <span class="o">/</span><span class="nb">&gt;</span>
b = <span class="p">#</span><span class="nv">b</span><span class="p">#</span><span class="nt">&lt;br/&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nv">c</span> <span class="o">=</span> <span class="m">15</span> <span class="o">+</span> <span class="nv">a</span> <span class="o">+</span> <span class="nv">b</span> <span class="o">/</span><span class="nb">&gt;</span>
c = <span class="p">#</span><span class="nv">c</span><span class="p">#</span><span class="nt">&lt;br/&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nv">b</span> <span class="o">=</span> <span class="nv">c</span> <span class="o">-</span> <span class="nv">a</span> <span class="o">/</span><span class="nb">&gt;</span>
b = <span class="p">#</span><span class="nv">b</span><span class="p">#</span><span class="nt">&lt;br/&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nv">d</span> <span class="o">=</span> <span class="s2">"Hello, "</span> <span class="o">/</span><span class="nb">&gt;</span>
d = <span class="p">#</span><span class="nv">d</span><span class="p">#</span><span class="nt">&lt;br/&gt;</span>
<span class="nb">&lt;/cfoutput&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span>
<span class="nv">a</span> <span class="o">=</span> <span class="m">5</span><span class="p">;</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"a = </span><span class="s-Interp">#a#</span><span class="s2">&lt;br/&gt;"</span><span class="p">);</span>
<span class="nv">b</span> <span class="o">=</span> <span class="m">10</span> <span class="o">+</span> <span class="m">5</span><span class="p">;</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"b = </span><span class="s-Interp">#b#</span><span class="s2">&lt;br/&gt;"</span><span class="p">);</span>
<span class="nv">c</span> <span class="o">=</span> <span class="m">15</span> <span class="o">+</span> <span class="nv">a</span> <span class="o">+</span> <span class="nv">b</span><span class="p">;</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"c = </span><span class="s-Interp">#c#</span><span class="s2">&lt;br/&gt;"</span><span class="p">);</span>
<span class="nv">b</span> <span class="o">=</span> <span class="nv">c</span> <span class="o">-</span> <span class="nv">a</span><span class="p">;</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"b = </span><span class="s-Interp">#b#</span><span class="s2">&lt;br/&gt;"</span><span class="p">);</span>
<span class="nv">d</span> <span class="o">=</span> <span class="s2">"Hello, "</span><span class="p">;</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"d = </span><span class="s-Interp">#d#</span><span class="s2">&lt;br/&gt;"</span><span class="p">);</span> 
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

In this second example, we assume the first example is present.

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfoutput&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nv">e</span> <span class="o">=</span> <span class="s2">"World!"</span> <span class="o">/</span><span class="nb">&gt;</span>
e = <span class="p">#</span><span class="nv">e</span><span class="p">#</span><span class="nt">&lt;br/&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nv">f</span> <span class="o">=</span> <span class="nv">d</span> <span class="o">&</span> <span class="nv">e</span> <span class="o">/</span><span class="nb">&gt;</span>
f = <span class="p">#</span><span class="nv">f</span><span class="p">#</span><span class="nt">&lt;br/&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nv">g</span> <span class="o">=</span> <span class="nv">d</span> <span class="o">&</span> <span class="nv">a</span> <span class="o">&</span> <span class="nv">e</span> <span class="o">/</span><span class="nb">&gt;</span>
g = <span class="p">#</span><span class="nv">g</span><span class="p">#</span><span class="nt">&lt;br/&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nv">b</span> <span class="o">=</span> <span class="s2">"hi!"</span> <span class="o">/</span><span class="nb">&gt;</span>
b = <span class="p">#</span><span class="nv">b</span><span class="p">#</span><span class="nt">&lt;br/&gt;</span>
<span class="nb">&lt;/cfoutput&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span>
<span class="nv">e</span> <span class="o">=</span> <span class="s2">"World!"</span><span class="p">;</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"e = </span><span class="s-Interp">#e#</span><span class="s2">&lt;br/&gt;"</span><span class="p">);</span>
<span class="nv">f</span> <span class="o">=</span> <span class="nv">d</span> <span class="o">&</span> <span class="nv">e</span><span class="p">;</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"f = </span><span class="s-Interp">#f#</span><span class="s2">"</span><span class="o">&lt;</span><span class="nv">br</span><span class="o">/&gt;</span><span class="s2">");</span>
<span class="s2">g = d & a & e;</span>
<span class="s2">writeOutput("</span><span class="nv">g</span> <span class="o">=</span> <span class="err">#</span><span class="nv">g</span><span class="err">#</span><span class="o">&lt;</span><span class="nv">br</span><span class="o">/&gt;</span><span class="s2">");</span>
<span class="s2">b = "</span><span class="nv">hi</span><span class="o">!</span><span class="s2">";</span>
<span class="s2">writeOutput("</span><span class="nv">b</span> <span class="o">=</span> <span class="err">#</span><span class="nv">b</span><span class="err">#</span><span class="o">&lt;</span><span class="nv">br</span><span class="o">/&gt;</span><span class="s2">");  </span>
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

*The first few lines in the first example are simple if youâ€™ve done any programming language before, but the last few get interesting when combining strings and numbers. The code looks a little messy since after each instruction we output a variable.

## 3. Components, Methods, and Parameters

### Components

In CFML, a ColdFusion component (CFC) file contains data and methods. Components are a building blocks for objects. Objects know information, called 'attributes', and can do actions, called 'methods'. In ColdFusion the 'cffunction' tag is used to define methods within a CFC.

For an example of an object, think about you as a human being. You have attributes like height, weight, and eye color. You have methods like walk, run, wash dishes, and daydream. Different kinds of objects have different attributes and methods. In the next sections weâ€™ll look at a few specific instructions in CFML.

In CFML we define an object using the 'cfcomponent' instruction and save the file as '.cfc'. Hereâ€™s an example defining the object type 'PersonalChef.cfc':

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfcomponent&gt;</span>

<span class="nb">&lt;/cfcomponent&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre>component {

}
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

### Methods

Inside the CFC we usually define one or more methods using the 'cffunction' instruction like this:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfcomponent&gt;</span>
 <span class="nb">&lt;cffunction</span> <span class="nv">name</span><span class="o">=</span><span class="s2">"makeToast"</span><span class="nb">&gt;</span>
  <span class="nb">&lt;cfset</span> <span class="nv">makeToast</span> <span class="o">=</span> <span class="s2">"Making your toast!"</span> <span class="o">/</span><span class="nb">&gt;</span>
 <span class="nb">&lt;/cffunction&gt;</span>
<span class="nb">&lt;/cfcomponent&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre>component {
 public string function makeToast(){
  makeToast = "Making your toast!";
 }
}
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

Inside the 'cffunction' instruction weâ€™d put the code for how the chef should make the toast.

A 'class' is an abstract idea, it defines what all objects of that type can know and do. Think of the chair youâ€™re sitting in. Its not an abstract chair, it is an actual chair. Weâ€™d call this actual chair an 'instance'. It is a *realization* of the idea chair. It has measurable attributes like height, color, weight. The class chair, on the other hand, is *abstract*. The classâ€™s weight, color, and size we canâ€™t determine them ahead of time.

Once we define a class, we create an instance of that class like this:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfset</span> <span class="nv">frank</span> <span class="o">=</span> <span class="nv">New</span> <span class="nf">PersonalChef</span><span class="p">()</span> <span class="o">/</span><span class="nb">&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre>frank = New PersonalChef();
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

Weâ€™re calling the 'New' instruction on the class 'PersonalChef' and storing it into the variable named 'frank'. Once we have the instance, we can set or get its attributes and call its methods. Methods are called by using this syntax: 'object.method_name()'. So if you have a person named 'frank' you would tell him to make toast by calling 'frank.makeToast()'.

The 'New' instruction creates a new instance of the object and calls itâ€™s init() method (if existing). Any arguments supplied to the object will be passed to the init() method. The init() method should return the object instance using '<cfreturn this />' in order to have the same expected behavior as the 'CreateObject' instruction. If no init() method exists, the object will be returned normally.

### Method Parameters

Sometimes methods take one or more *parameters* telling them **how** to do what theyâ€™re suppose to **do**. For instance, I might call 'frank.makeToast('burned')' for him to burn my toast. Or maybe he has another method where I call 'frank.makebreakfast("toast","eggs")' for him to make both toast and eggs. Parameters can be numbers, strings, or any kind of object. When a method takes a parameter we use the 'cfargument' instruction, itâ€™ll look like this:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfcomponent&gt;</span>
 <span class="nb">&lt;cffunction</span> <span class="nv">name</span><span class="o">=</span><span class="s2">"makeToast"</span> <span class="nv">returnType</span><span class="o">=</span><span class="s2">"string"</span><span class="nb">&gt;</span>
  <span class="nb">&lt;cfargument</span> <span class="nv">name</span><span class="o">=</span><span class="s2">"color"</span> <span class="nv">required</span><span class="o">=</span><span class="s2">"yes"</span><span class="nb">&gt;</span>
   <span class="nb">&lt;cfset</span> <span class="nv">makeToast</span> <span class="o">=</span> <span class="s2">"Making your toast </span><span class="s-Interp">#arguments.color#</span><span class="s2">!"</span> <span class="o">/</span><span class="nb">&gt;</span>
 <span class="nb">&lt;/cffunction&gt;</span>
<span class="nb">&lt;/cfcomponent&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre>component {
 public string function makeToast(required String color){
  makeToast = "Making your toast #arguments.color#!";
 }
}
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

The method is requiring us to pass in a 'color' telling it how to do the method 'makeToast'.

### Return Value

In CFML, every time you call a method you wonâ€™t necessarily get a value back. By default, a CFML method returns *nothing*. Weâ€™ll talk about *nothing* and 'null' in the last section of â€œCFML in 100 minutesâ€. If you called 'makeToast' method above like '<cfset result = frank.makeToast('burned') />' or 'set result = frank.makeToast('burned');', and tried to output 'result' you should have seen 'Variable RESULT is undefined'.

To return data, we use 'cfreturn' to instruct the method to return a 'value'. Since that wasnâ€™t in the last instruction before the ending 'cffunction' in your 'makeToast' method, you received *nothing* and tried to putting that into the 'result' variable.

For the purposes of our next section Iâ€™m going to return the chef instance itself from the method. If you wanted to picture the metaphor, imagine you are looking at your chef 'frank'. You say, â€œFrank, go make my toastâ€, he tells you heâ€™s making the toast, goes to make it, then comes back to you to receive more instructions. Heâ€™s **returning himself** to you. Hereâ€™s how we implement it in code:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfcomponent&gt;</span>
 <span class="nb">&lt;cffunction</span> <span class="nv">name</span><span class="o">=</span><span class="s2">"makeToast"</span> <span class="nv">returnType</span><span class="o">=</span><span class="s2">"component"</span><span class="nb">&gt;</span>
  <span class="nb">&lt;cfargument</span> <span class="nv">name</span><span class="o">=</span><span class="s2">"color"</span> <span class="nv">required</span><span class="o">=</span><span class="s2">"yes"</span><span class="nb">&gt;</span>
   <span class="nb">&lt;cfset</span> <span class="nv">this.makeToast</span> <span class="o">=</span> <span class="s2">"Making your toast </span><span class="s-Interp">#arguments.color#</span><span class="s2">!"</span> <span class="o">/</span><span class="nb">&gt;</span>
   <span class="nb">&lt;cfreturn</span> <span class="nv">this</span> <span class="o">/</span><span class="nb">&gt;</span>
 <span class="nb">&lt;/cffunction&gt;</span>
<span class="nb">&lt;/cfcomponent&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre>component {
 public component function makeToast(required String color){
  this.makeToast = "Making your toast #arguments.color#!";
  return this;
 }
}
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

## 4. Strings

In CFML a string is defined as a quote ( '"' ) followed by zero or more letters, numbers, or symbols and followed by another quote ( '"' ). Some simple strings would be '"hello"' or '"This sentence is a string!"'. Strings can be anything from '""', the empty string, to really long sets of text. This whole tutorial, for instance, is stored in a string. Strings have a few important instructions that weâ€™ll use.

*   'Len'   
    Call 'Len' on a string to get back the number of characters in the string. For instance 'Len("Hello")' would give you back '5'.
*   'Replace'   
    The 'Replace' instruction replaces occurrences of **substring1** in a string with **substring2**, in a specified scope. The search is case sensitive and the scope default is one. For instance, 'Replace("Hello", "e", "")' would give you back '"hllo"' after replacing the *first* occurrence of '"e"', or 'Replace("Good Morning!", "o", "e", "All")"' would give you '"Geed Merning!"' 
*   'RemoveChars'   
    Call 'RemoveChars' to remove characters from a string. For instance, 'RemoveChars("hello bob", 2, 5)' would give you back '"hbob"'.
*   'Mid'   
    The 'mid' instruction extracts a substring from a string. For instance, I could call 'Mid("Welcome to CFML Jumpstart",4,12)' and it would give you back: 'come to CFML'.

Experiment with the following samples in a CFML file:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfset</span> <span class="nv">tester</span> <span class="o">=</span> <span class="s2">"Good Morning Everyone!"</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfoutput&gt;</span><span class="p">#</span><span class="k">len</span><span class="p">(</span><span class="nv">tester</span><span class="p">)#</span><span class="nt">&lt;br&gt;</span><span class="nb">&lt;/cfoutput&gt;</span>
<span class="nb">&lt;cfoutput&gt;</span><span class="p">#</span><span class="nf">Replace</span><span class="p">(</span><span class="nv">tester</span><span class="p">,</span> <span class="s2">"o"</span><span class="p">,</span> <span class="s2">"e"</span><span class="p">,</span> <span class="s2">"All"</span><span class="p">)#</span><span class="nt">&lt;br&gt;</span><span class="nb">&lt;/cfoutput&gt;</span>
<span class="nb">&lt;cfoutput&gt;</span><span class="p">#</span><span class="nf">RemoveChars</span><span class="p">(</span><span class="nv">tester</span><span class="p">,</span> <span class="m">2</span><span class="p">,</span> <span class="m">5</span><span class="p">)#</span><span class="nt">&lt;br&gt;</span><span class="nb">&lt;/cfoutput&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nv">t2</span> <span class="o">=</span> <span class="s2">"sample,data,from,a,CSV"</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nv">t3</span> <span class="o">=</span> <span class="nf">Mid</span><span class="p">(</span><span class="nv">t2</span><span class="p">,</span><span class="m">8</span><span class="p">,</span><span class="k">len</span><span class="p">(</span><span class="nv">t2</span><span class="p">))</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfoutput&gt;</span><span class="p">#</span><span class="nv">t3</span><span class="p">#</span><span class="nt">&lt;br&gt;</span><span class="nb">&lt;/cfoutput&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span>
<span class="nv">tester</span> <span class="o">=</span> <span class="s2">"Good Morning Everyone!"</span><span class="p">;</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"</span><span class="s-Interp">#len(tester)#</span><span class="s2">&lt;br/&gt;"</span><span class="p">);</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="nf">Replace</span><span class="p">(</span><span class="nv">tester</span><span class="p">,</span> <span class="s2">"o"</span><span class="p">,</span> <span class="s2">"e"</span><span class="p">,</span> <span class="s2">"All"</span><span class="p">)</span> <span class="o">&</span> <span class="s2">"&lt;br/&gt;"</span><span class="p">);</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="nf">RemoveChars</span><span class="p">(</span><span class="nv">tester</span><span class="p">,</span> <span class="m">2</span><span class="p">,</span> <span class="m">5</span><span class="p">)</span> <span class="o">&</span> <span class="s2">"&lt;br/&gt;"</span><span class="p">);</span>
<span class="nv">t2</span> <span class="o">=</span> <span class="s2">"sample,data,from,a,CSV"</span><span class="p">;</span>
<span class="nv">t3</span> <span class="o">=</span> <span class="nf">Mid</span><span class="p">(</span><span class="nv">t2</span><span class="p">,</span><span class="m">8</span><span class="p">,</span><span class="k">len</span><span class="p">(</span><span class="nv">t2</span><span class="p">));</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="nv">t3</span> <span class="o">&</span> <span class="s2">"&lt;br/&gt;"</span><span class="p">);</span>
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

Often a string may store a list like the 't2' variable in the last example. A string for storing a list isnâ€™t the best for performance and usage. Using an array for a list is so much better. We can convert a list into an 'array' using 'ListToArray'. Weâ€™ll discuss arrays in an upcoming section. Try out these next examples in the CFML file assuming we have the code from the last example:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfset</span> <span class="nv">t4</span> <span class="o">=</span> <span class="nf">ListToArray</span><span class="p">(</span><span class="nv">t3</span><span class="p">)</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfoutput&gt;</span>
 <span class="p">#</span><span class="nv">t4</span><span class="p">[</span><span class="m">2</span><span class="p">]#</span>
<span class="nb">&lt;/cfoutput&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span>
<span class="nv">t4</span> <span class="o">=</span> <span class="nf">ListToArray</span><span class="p">(</span><span class="nv">t3</span><span class="p">);</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="nv">t4</span><span class="p">[</span><span class="m">2</span><span class="p">]);</span>
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

The numbers inside the '[]' brackets specify which item of the array you want pulled out. Theyâ€™re numbered starting with 1. So the first example pulls out the '2' array item. This 't4' array contains position '1', the beginning of the list, up to position '4', the ending of the array.

### Combining Strings and Variables

It is extremely common that we want to combine the value of a variable with other strings. For instance, lets start with this example string:

'"Happy Saturday!"'

When we put that into the CFML file, it just spits back the same string. If we were writing a proper program we might want it to greet the user when they start the program by saying '"Happy"' then the day of the week. So we canâ€™t just put a string like '"Happy Saturday!"' or itâ€™d be saying Saturday even on Tuesday.

What we need to do is combine a variable with the string. There are two ways to do that. The first approach is called *string concatenation* which is basically just adding strings together:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfset</span> <span class="nv">today</span> <span class="o">=</span>  <span class="s2">"Saturday"</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nv">message</span> <span class="o">=</span>  <span class="s2">"Happy "</span> <span class="o">&</span> <span class="nv">today</span> <span class="o">&</span> <span class="s2">"!"</span> <span class="o">/</span><span class="nb">&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span>
<span class="nv">today</span> <span class="o">=</span>  <span class="s2">"Saturday"</span><span class="p">;</span>
<span class="nv">message</span> <span class="o">=</span> <span class="s2">"Happy "</span> <span class="o">&</span> <span class="nv">today</span> <span class="o">&</span> <span class="s2">"!"</span><span class="p">;</span>
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

In the first line we setup a variable to hold the day of the week. Then weâ€™ll printed the string *Happy* combined with the value of the variable 'today' and the string *!*. You might be thinking, â€œWhat was the point of that since we still wrote *Saturday* in the first line?â€ Ok, well, if you were writing a real program youâ€™d use CFMLs built-in date instructions like this:

'today = DayOfWeek(Now());'

'Now()' gets the current date and time of the computer running the ColdFusion server. 'DayOfWeek' returns an integer in the range 1 (Sunday) to 7 (Saturday) for the day of the week. We still donâ€™t have the day of week as string. Try this:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfset</span> <span class="nv">today</span> <span class="o">=</span> <span class="nf">DayOfWeekAsString</span><span class="p">(</span><span class="nf">DayOfWeek</span><span class="p">(</span><span class="nf">Now</span><span class="p">()))</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nv">message</span> <span class="o">=</span> <span class="s2">"Happy "</span> <span class="o">&</span> <span class="nv">today</span> <span class="o">&</span> <span class="s2">"!"</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfoutput&gt;</span>
 <span class="p">#</span><span class="nv">message</span><span class="p">#</span>
<span class="nb">&lt;/cfoutput&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span>
<span class="nv">today</span> <span class="o">=</span> <span class="nf">DayOfWeekAsString</span><span class="p">(</span><span class="nf">DayOfWeek</span><span class="p">(</span><span class="nf">Now</span><span class="p">()));</span>
<span class="nv">message</span> <span class="o">=</span> <span class="s2">"Happy "</span> <span class="o">&</span> <span class="nv">today</span> <span class="o">&</span> <span class="s2">"!"</span><span class="p">;</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="nv">message</span><span class="p">);</span>
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

Great, no errors and our output looks correct. 'DayOfWeekAsString' did the trick. There is another string combination called *string interpolation*.

**String interpolation** is the process of sticking data into the middle of strings. We use the symbols '#' around the 'variable' where in a string the value should be inserted. Inside those hashes we can put any variable and output it in that spot. Our previous example 'message' could be rewritten like this: <table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfset</span> <span class="nv">message</span> <span class="o">=</span> <span class="s2">"Happy </span><span class="s-Interp">#today#</span><span class="s2">!"</span> <span class="o">/</span><span class="nb">&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre>message = "Happy #today#!";
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

If you compare the output youâ€™ll see the second example gives the exact same results. The code itself is a little more compact and, personally, I find it much easier to read.

Basically *interpolating* means evaluate the code inside this '#' wrapper and put it into the string.

## 5. Numbers

There are two basic kinds of numbers in CFML: integers (whole numbers) and real (numbers with a decimal point). For our workshop, weâ€™ll only be dealing with integers. You can use normal math operations with integers including '+', '-', '/', and '*'. The '++' operator can be used to increment a number. It is also the only one we will use to control a loop. We will talk more about Conditional Looping in section 9. Try out this example for the '++' operator:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfset</span> <span class="nv">loop</span> <span class="o">=</span> <span class="m"></span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfoutput&gt;</span>
 <span class="nb">&lt;cfloop</span> <span class="nv">condition</span><span class="o">=</span><span class="s2">"loop LT 5"</span> <span class="nb">&gt;</span>
  <span class="p">#</span><span class="nv">loop</span><span class="p">#</span> Hello, world!<span class="nt">&lt;br&gt;</span>
  <span class="nb">&lt;cfset</span> <span class="nv">loop</span><span class="o">++</span> <span class="o">/</span><span class="nb">&gt;</span>
 <span class="nb">&lt;/cfloop&gt;</span>
 I am here!<span class="nt">&lt;br&gt;</span>
<span class="nb">&lt;/cfoutput&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span>
<span class="nf">for</span><span class="p">(</span><span class="nv">loop</span> <span class="o">=</span> <span class="m"></span> <span class="p">;</span> <span class="nv">loop</span> <span class="o">&lt;</span> <span class="m">5</span> <span class="p">;</span> <span class="nv">loop</span><span class="o">++</span><span class="p">)</span>
 <span class="nf">WriteOutput</span><span class="p">(</span><span class="s2">"</span><span class="s-Interp">#loop#</span><span class="s2"> Hello, world!&lt;br&gt;"</span><span class="p">);</span>
<span class="nf">WriteOutput</span><span class="p">(</span><span class="s2">"I am here&lt;br&gt;"</span><span class="p">);</span>
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

In this next example weâ€™re using the 'cfloop' instruction with a multiple instructions inside the condition. The CFML script syntax looks for the starting '{' and the ending '}'. Each instruction between the beginning '{' and ending '}' will be executed if the condition is true.

In the tag example thereâ€™s no need to manage the index inside the loop if youâ€™re simply stepping through one item at a time. You can use the 'from' and 'to' arguments, and ColdFusion will simply loop from the first value to the second, and automatically increment the variable in the 'index' argument.

Try this example with multiple instructions:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfset</span> <span class="nv">loop</span> <span class="o">=</span> <span class="m"></span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfoutput&gt;</span>
<span class="nb">&lt;cfloop</span> <span class="nv">index</span><span class="o">=</span><span class="s2">"loop"</span> <span class="nv">from</span><span class="o">=</span><span class="s2">"0"</span> <span class="nv">to</span><span class="o">=</span><span class="s2">"4"</span><span class="nb">&gt;</span>
 <span class="p">#</span><span class="nv">loop</span><span class="p">#</span> Good Morning!
 ...is it lunch time yet?<span class="nt">&lt;br&gt;</span>
<span class="nb">&lt;/cfloop&gt;</span>
<span class="nb">&lt;/cfoutput&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span>
<span class="nv">loop</span> <span class="o">=</span> <span class="m"></span><span class="p">;</span> 
<span class="nf">while</span><span class="p">(</span><span class="nv">loop</span> <span class="o">&lt;</span> <span class="m">5</span><span class="p">)</span> <span class="p">{</span> 
 <span class="nf">WriteOutput</span><span class="p">(</span><span class="s2">"</span><span class="s-Interp">#loop#</span><span class="s2"> Good Morning! "</span><span class="p">);</span>
 <span class="nf">WriteOutput</span><span class="p">(</span><span class="s2">"...is it lunch time yet?&lt;br&gt;"</span><span class="p">);</span>
 <span class="nv">loop</span><span class="o">++</span><span class="p">;</span>
<span class="p">}</span>
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

Itâ€™s also possible to go through a loop and step over more than one value at a time. The following examples will step through the loop and increase the 'loop' index by two for each time through the loop.

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfset</span> <span class="nv">loop</span> <span class="o">=</span> <span class="m"></span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfoutput&gt;</span>
<span class="nb">&lt;cfloop</span> <span class="nv">index</span><span class="o">=</span><span class="s2">"loop"</span> <span class="nv">from</span><span class="o">=</span><span class="s2">"0"</span> <span class="nv">to</span><span class="o">=</span><span class="s2">"4"</span> <span class="nv">step</span><span class="o">=</span><span class="s2">"2"</span><span class="nb">&gt;</span>
 <span class="p">#</span><span class="nv">loop</span><span class="p">#</span> Good Morning!
 ...is it lunch time yet?<span class="nt">&lt;br&gt;</span>
<span class="nb">&lt;/cfloop&gt;</span>
<span class="nb">&lt;/cfoutput&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span>
<span class="nv">loop</span> <span class="o">=</span> <span class="m"></span><span class="p">;</span>
<span class="nf">while</span><span class="p">(</span><span class="nv">loop</span> <span class="o">&lt;</span> <span class="m">5</span><span class="p">)</span> <span class="p">{</span>
 <span class="nf">WriteOutput</span><span class="p">(</span><span class="s2">"</span><span class="s-Interp">#loop#</span><span class="s2"> Good Morning! "</span><span class="p">);</span>
 <span class="nf">WriteOutput</span><span class="p">(</span><span class="s2">"...is it lunch time yet?&lt;br&gt;"</span><span class="p">);</span>
 <span class="nv">loop</span> <span class="o">=</span> <span class="nv">loop</span> <span class="o">+</span> <span class="m">2</span><span class="p">;</span>
<span class="p">}</span>
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

## 6. Queries

A query is a request to a database. The query can ask for information from the database, write new data to the database, update existing information in the database, or delete records from the database. Each time you query a database with CFML, you get the data (the recordset) and the query variables; together they make up the query object. 'cfquery' passes SQL statements to the 'datasource'. The 'datasource' is set in the ColdFusion administrator.

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nt">&lt;cfquery</span> <span class="na">name=</span><span class="s">"GetBreakfastItems"</span> <span class="na">datasource=</span><span class="s">"pantry"</span><span class="nt">&gt;</span> 
 SELECT QUANTITY, ITEM 
 FROM CUPBOARD 
 ORDER BY ITEM 
<span class="nt">&lt;/cfquery&gt;</span> 
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span>
<span class="nv">queryService</span> <span class="o">=</span> <span class="nv">new</span> <span class="nf">Query</span><span class="p">();</span>

<span class="nf">queryService.setName</span><span class="p">(</span><span class="s2">"GetBreakfastItems"</span><span class="p">);</span> 
<span class="nf">queryServ.setDatasource</span><span class="p">(</span><span class="s2">"pantry"</span><span class="p">);</span> 
<span class="nf">queryService.setSQL</span><span class="p">(</span><span class="s2">"</span>
<span class="s2">SELECT QUANTITY, ITEM </span>
<span class="s2">FROM CUPBOARD </span>
<span class="s2">ORDER BY ITEM</span>
<span class="s2">"</span><span class="p">);</span>
 
<span class="nv">GetBreakfastItems</span> <span class="o">=</span> <span class="nf">queryService.execute</span><span class="p">().</span><span class="nf">getResult</span><span class="p">();</span> 
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

In order to display the data from our query, we need to loop through the rows, and display each row. This is usually done in a '<cfoutput>' tag like so:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfoutput query="GetBreakfastItems"&gt;</span>
 There are <span class="p">#</span><span class="nv">GetBreakfastItems.Quantity</span><span class="p">#</span> <span class="p">#</span><span class="nv">GetBreakfastItems.Item</span><span class="p">#</span> in the pantry<span class="nt">&lt;br</span> <span class="nt">/&gt;</span>
<span class="nb">&lt;/cfoutput&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

While itâ€™s not strictly necessary to prepend the recordset name before the column name inside the '<cfoutput>', itâ€™s strongly recommended that you do in order to prevent referencing the wrong variable scope.

You can also loop through a query using standard loop constructs, though they differ when using tags and script.

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfloop</span> <span class="nv">query</span><span class="o">=</span><span class="s2">"GetBreakfastItems"</span><span class="nb">&gt;</span>
 <span class="nb">&lt;cfoutput&gt;</span>There are <span class="p">#</span><span class="nv">GetBreakfastItems.Quantity</span><span class="p">#</span> <span class="p">#</span><span class="nv">GetBreakfastItems.Item</span><span class="p">#</span> in the pantry<span class="nt">&lt;br</span> <span class="nt">/&gt;</span><span class="nb">&lt;/cfoutput&gt;</span>
<span class="nb">&lt;/cfloop&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span> 
<span class="nf">for</span><span class="p">(</span><span class="nv">x</span> <span class="o">=</span> <span class="m">1</span><span class="p">;</span> <span class="nv">x</span> <span class="o">&lt;=</span> <span class="nv">GetBreakfastItems</span><span class="p">;</span> <span class="nv">x</span><span class="o">=</span><span class="nv">x</span><span class="o">+</span><span class="m">1</span><span class="p">)</span> <span class="p">{</span> 
 <span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"There are </span><span class="s-Interp">#GetBreakfastItems.Quantity[x]#</span><span class="s2"> </span><span class="s-Interp">#GetBreakfastItems.Item[x]#</span><span class="s2"> in the pantry&lt;br /&gt;"</span><span class="p">)</span>
<span class="p">}</span> 
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

When looping through a query with '<cfloop>', you need to make sure that you have a '<cfoutput>' tag around your content (or around the loop) to ensure the ColdFusion instructions are recognized.

When looping through a query in 'cfscript', youâ€™ll need to reference the query just like you would a multidimensional array, using the counter set up in in your for statement to pick up the correct row from the recordset. So the syntax becomes 'recordsetName.ColumnName[rowNumber]'.

## 7. Arrays

Often we need to organize a group and put them into a *collection*. There are two main types of collections: **arrays** and **structures**.

An **array** is a number-indexed list. Picture a city block of houses. Together they form an array and their addresses are the **indices**. Each house on the block will have a unique address. Some addresses might be empty, but the addresses are all in a specific order. The **index** is the address of a specific element inside the array. In CFML the index always begins with '1'. An array is defined in CFML as an opening '[' then zero or more elements, and a closing ']'. Try out this code:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfset</span> <span class="nv">favorite_colors</span> <span class="o">=</span> <span class="p">[</span><span class="s2">"red"</span><span class="p">,</span><span class="s2">"blue"</span><span class="p">,</span><span class="s2">"green"</span><span class="p">,</span><span class="s2">"black"</span><span class="p">,</span><span class="s2">"brown"</span><span class="p">]</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfdump</span> <span class="k">var</span><span class="o">=</span><span class="s2">"</span><span class="s-Interp">#favorite_colors#</span><span class="s2">"</span> <span class="o">/</span><span class="nb">&gt;</span><span class="nt">&lt;br&gt;</span>
<span class="nb">&lt;cfdump</span> <span class="k">var</span><span class="o">=</span><span class="s2">"</span><span class="s-Interp">#favorite_colors[2]#</span><span class="s2">"</span> <span class="o">/</span><span class="nb">&gt;</span><span class="nt">&lt;br&gt;</span>
<span class="nb">&lt;cfdump</span> <span class="k">var</span><span class="o">=</span><span class="s2">"</span><span class="s-Interp">#favorite_colors[ArrayLen(favorite_colors)]#</span><span class="s2">"</span> <span class="o">/</span><span class="nb">&gt;</span><span class="nt">&lt;br&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span>
<span class="nv">favorite_colors</span> <span class="o">=</span> <span class="p">[</span><span class="s2">"red"</span><span class="p">,</span><span class="s2">"blue"</span><span class="p">,</span><span class="s2">"green"</span><span class="p">,</span><span class="s2">"black"</span><span class="p">,</span><span class="s2">"brown"</span><span class="p">];</span>
<span class="nf">writeDump</span><span class="p">(</span><span class="nv">favorite_colors</span><span class="p">);</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"&lt;br&gt;"</span><span class="p">);</span>
<span class="nf">writeDump</span><span class="p">(</span><span class="nv">favorite_colors</span><span class="p">[</span><span class="m">2</span><span class="p">]);</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"&lt;br&gt;"</span><span class="p">);</span>
<span class="nf">writeDump</span><span class="p">(</span><span class="k">var</span><span class="o">=</span><span class="nv">favorite_colors</span><span class="p">[</span><span class="nf">ArrayLen</span><span class="p">(</span><span class="nv">favorite_colors</span><span class="p">)]);</span>
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

Keep going with these, but try to understand what each instruction is doing before we explain them:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfset</span> <span class="nf">ArrayAppend</span><span class="p">(</span><span class="nv">favorite_colors</span><span class="p">,</span> <span class="s2">"orange"</span><span class="p">)</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nv">favorite_colors</span><span class="p">[</span><span class="m">3</span><span class="p">]</span><span class="o">=</span><span class="s2">"yellow"</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfdump</span> <span class="k">var</span><span class="o">=</span><span class="s2">"</span><span class="s-Interp">#favorite_colors#</span><span class="s2">"</span> <span class="o">/</span><span class="nb">&gt;</span><span class="nt">&lt;br&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nf">ArraySort</span><span class="p">(</span><span class="nv">favorite_colors</span><span class="p">,</span><span class="s2">"text"</span><span class="p">)</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nf">ArrayDeleteAt</span><span class="p">(</span><span class="nv">favorite_colors</span><span class="p">,</span> <span class="m">2</span><span class="p">)</span> <span class="o">/</span><span class="nb">&gt;</span> 
<span class="nb">&lt;cfdump</span> <span class="k">var</span><span class="o">=</span><span class="s2">"</span><span class="s-Interp">#favorite_colors#</span><span class="s2">"</span> <span class="o">/</span><span class="nb">&gt;</span><span class="nt">&lt;br&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span>
<span class="nf">ArrayAppend</span><span class="p">(</span><span class="nv">favorite_colors</span><span class="p">,</span> <span class="s2">"orange"</span><span class="p">);</span>
<span class="nv">favorite_colors</span><span class="p">[</span><span class="m">3</span><span class="p">]</span> <span class="o">=</span> <span class="s2">"yellow"</span><span class="p">;</span>
<span class="nf">writeDump</span><span class="p">(</span><span class="nv">favorite_colors</span><span class="p">);</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"&lt;br&gt;"</span><span class="p">);</span>
<span class="nv">set</span> <span class="o">=</span> <span class="nf">ArraySort</span><span class="p">(</span><span class="nv">favorite_colors</span><span class="p">,</span><span class="s2">"text"</span><span class="p">);</span>
<span class="nf">ArrayDeleteAt</span><span class="p">(</span><span class="nv">favorite_colors</span><span class="p">,</span> <span class="m">2</span><span class="p">);</span>
<span class="nf">writeDump</span><span class="p">(</span><span class="k">var</span><span class="o">=</span><span class="nv">favorite_colors</span><span class="p">);</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"&lt;br&gt;"</span><span class="p">);</span> 
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

In order to get add an element in the array you use the syntax 'ArrayAppend(array,"value")' or 'arrayname[index] = "value"'. The first example of adding an array element is **with an instruction**. The second is updating an array element is **by assignment**. So looking at the final 'favorite_colors' array:

*   Whatâ€™s the index of '"brown"' ?
*   What did the 'ArraySort' instuction do to the collection?
*   What does 'ArrayLen' instruction return?

There are lots of cool things to do with an array. You can rearrange the order of the elements using the 'ArraySort' instruction like we did in the last example. You can iterate through each element using the 'cfloop' instruction. You can find the address of a specific element by using the 'arrayName[index]' instruction. You can ask an array if an element is present with the 'ArrayIsDefined' instruction. Try out this example that brings a bunch of things together:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfoutput&gt;</span>
 <span class="nt">&lt;ul&gt;</span>
 <span class="nb">&lt;cfloop</span> <span class="nv">array</span><span class="o">=</span><span class="s2">"</span><span class="s-Interp">#favorite_colors#</span><span class="s2">"</span> <span class="nv">index</span><span class="o">=</span><span class="s2">"target"</span> <span class="nb">&gt;</span>
  <span class="nt">&lt;li&gt;</span><span class="p">#</span><span class="nv">target</span><span class="p">#</span> is <span class="p">#</span><span class="k">len</span><span class="p">(</span><span class="nv">target</span><span class="p">)#</span> letters long.<span class="nt">&lt;/li&gt;</span>
 <span class="nb">&lt;/cfloop&gt;</span>
 <span class="nt">&lt;/ul&gt;</span>
 <span class="nb">&lt;cfdump</span> <span class="k">var</span><span class="o">=</span><span class="s2">"</span><span class="s-Interp">#ArrayIsDefined(favorite_colors,4)#</span><span class="s2">"</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;/cfoutput&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"&lt;ul&gt;"</span><span class="p">);</span>
<span class="nv">index</span> <span class="o">=</span> <span class="nf">favorite_colors.iterator</span><span class="p">();</span>
<span class="nf">while</span><span class="p">(</span><span class="nf">index.hasNext</span><span class="p">()){</span>
 <span class="nv">target</span> <span class="o">=</span> <span class="nf">index.next</span><span class="p">();</span>
 <span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"&lt;li&gt;</span><span class="s-Interp">#target#</span><span class="s2"> is </span><span class="s-Interp">#len(target)#</span><span class="s2"> letters long.&lt;/li&gt;"</span><span class="p">);</span>
<span class="p">}</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"&lt;/ul&gt;"</span><span class="p">);</span> 
<span class="nf">writeDump</span><span class="p">(</span><span class="k">var</span><span class="o">=</span><span class="nf">ArrayIsDefined</span><span class="p">(</span><span class="nv">favorite_colors</span><span class="p">,</span><span class="m">4</span><span class="p">));</span>
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

We use arrays whenever we need a list where the elements are in a specific order.

## 8. Structures

A structure is a *collection of data* where each element of data is addressed by a name. As an analogy, think about a classroom of children. Under ideal circumstances, each student has a name and can be found by using that name. We might look in a science classroom for a child named Joey and that would result in finding an actual student. We could write this like 'science["Joey"]' which could be read as â€œlook in the collection named 'science' and find the thing named 'Joey'â€.

A structure is an unordered collection, its just a bunch of data collected together where each one has a unique name/key. Structures have a slightly more complicated syntax:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfset</span> <span class="nv">ages</span> <span class="o">=</span> <span class="p">{</span><span class="nv">jack</span> <span class="o">=</span> <span class="m">11</span><span class="p">,</span> <span class="nv">brian</span> <span class="o">=</span> <span class="m">12</span><span class="p">,</span> <span class="nv">tracy</span> <span class="o">=</span> <span class="m">11</span><span class="p">}</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nv">ages.joey</span> <span class="o">=</span> <span class="m">12</span> <span class="o">/</span><span class="nb">&gt;</span> 
<span class="nb">&lt;cfset</span> <span class="nv">ages</span><span class="p">[</span><span class="s2">"jill"</span><span class="p">]</span> <span class="o">=</span> <span class="m">14</span> <span class="o">/</span><span class="nb">&gt;</span> 

<span class="nb">&lt;cfdump</span> <span class="k">var</span><span class="o">=</span><span class="s2">"</span><span class="s-Interp">#ages#</span><span class="s2">"</span> <span class="o">/</span><span class="nb">&gt;</span>

<span class="nb">&lt;cfoutput&gt;</span>
Joey is <span class="p">#</span><span class="nv">ages</span><span class="p">[</span><span class="s1">'joey'</span><span class="p">]#</span> years old.
<span class="nb">&lt;/cfoutput&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span>
<span class="nv">ages</span> <span class="o">=</span> <span class="p">{</span><span class="nv">jack</span> <span class="o">=</span> <span class="m">11</span><span class="p">,</span> <span class="nv">brian</span> <span class="o">=</span> <span class="m">12</span><span class="p">,</span> <span class="nv">tracy</span> <span class="o">=</span> <span class="m">11</span><span class="p">};</span>
<span class="nv">ages.joey</span> <span class="o">=</span> <span class="m">12</span><span class="p">;</span>
<span class="nv">ages</span><span class="p">[</span><span class="s2">"jill"</span><span class="p">]</span> <span class="o">=</span> <span class="m">14</span><span class="p">;</span>

<span class="nf">writeDump</span><span class="p">(</span><span class="k">var</span><span class="o">=</span><span class="nv">ages</span><span class="p">);</span>
<span class="nf">writeOutput</span><span class="p">(</span><span class="s2">"Joey is </span><span class="s-Interp">#ages['joey']#</span><span class="s2"> years old."</span><span class="p">);</span>
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

Here we create a structure named 'ages'. Structures are made up what are called key-value pairs.The **key** is used as the address and the **value** is the object at that address. In the 'ages' structure we have keys including '"joey"' and '"jill"' and values including '12' and '14'. When creating a structure using '{}' the key and value are linked by the '=' symbol. So to create a structure, the structures start with a curly bracket '{', have zero or more entries made up of a *key*, '=', and a *value* separated by commas, then end with a closing curly bracket '}'.

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfset</span> <span class="nv">ages</span><span class="p">[</span><span class="s2">"jimmy"</span><span class="p">]</span> <span class="o">=</span> <span class="m">14</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfset</span> <span class="nv">ages</span><span class="p">[</span><span class="s2">"joey"</span><span class="p">]</span> <span class="o">=</span> <span class="m">9</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfdump</span> <span class="k">var</span><span class="o">=</span><span class="s2">"</span><span class="s-Interp">#ages#</span><span class="s2"> /</span><span class="nb">&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cfscript&gt;</span>
<span class="nv">ages</span><span class="p">[</span><span class="s2">"jimmy"</span><span class="p">]</span> <span class="o">=</span> <span class="m">14</span><span class="p">;</span>
<span class="nv">ages</span><span class="p">[</span><span class="s2">"joey"</span><span class="p">]</span> <span class="o">=</span> <span class="m">9</span><span class="p">;</span>
<span class="nf">writeDump</span><span class="p">(</span><span class="k">var</span><span class="o">=</span><span class="nv">ages</span><span class="p">);</span>
<span class="nb">&lt;/cfscript&gt;</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

In the second chunk of the example, we add a new key and value to the structure. Since the '"jimmy"' key wasnâ€™t in the original structure, itâ€™s added with the value of '14'. If the key '"jimmy"' already existed then the value would be replaced by '14'. Every key in a structure must be unique! In the second line we reference the key '"joey"' which already exists, so the value gets replaced with the '9'. Then, just to show you the state of the structure, we dump out the list of keys and the list of values.

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre>students = ages.keys.sort 
students.each do |student| 
puts "#{student} is #{ages[student]} years old." 
end
 
<span class="nb">&lt;cfset</span> <span class="nv">student</span> <span class="o">=</span> <span class="p">{</span><span class="nv">firstName</span><span class="o">=</span><span class="s2">"joey"</span><span class="p">,</span> <span class="nv">age</span><span class="o">=</span><span class="nv">ages.joey</span><span class="p">,</span> <span class="nv">grades</span><span class="o">=</span><span class="p">[</span><span class="m">91</span><span class="p">,</span> <span class="m">78</span><span class="p">,</span> <span class="m">87</span><span class="p">]}</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;cfdump</span> <span class="k">var</span><span class="o">=</span><span class="s2">"</span><span class="s-Interp">#student#</span><span class="s2">"</span> <span class="o">/</span><span class="nb">&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre>SCRIPT EXAMPLE
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

The last chunk of the example calls the 'keys' method on the structure 'ages'. 'keys' gives back an array holding all the key values inside the structure. We then called 'sort' on that array to put them in alphabetical order before storing the array into the variable 'students'. We then iterated through the array 'students' using the method 'each', gave each element of the list the name 'student', then printed out one line with that student name and the students age from 'ages'.

While that last part probably seemed complicated, its just to illustrate that although structures are by nature unordered, you can still manipulate and output the data in ordered, meaningful ways.

## 9. Conditionals

Conditional statements evaluate to 'true' or 'false' only. The most common conditional operators are '==' (equal), '!=' (not equal), '>' (greater than), '>=' (greater than or equal to), '<' (less than), and '<=' (less than or equal to). You can also define the operators as abbreviations: 'EQ', 'NEQ', 'GT', 'GTE', 'LT', and 'LTE'.

Some instructions return a 'true' or 'false', so theyâ€™re used in conditional statements. For example, 'IsArray' which is 'true' only when the variable is an 'array'. Structures have an instruction named 'StructKeyExists' which returns 'true' if a key is present in a structure.

### 9. 1. If, Else If, & Else

Why do we have conditional statements? Most often its to control conditional instructions, especially 'if' / 'else if' / 'else' structures. Lets write an example by adding a method to our 'PersonalChef' class:

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cffunction</span> <span class="nv">name</span><span class="o">=</span><span class="s2">"water_boiling"</span> <span class="nv">returnType</span><span class="o">=</span><span class="s2">"component"</span><span class="nb">&gt;</span>
 <span class="nb">&lt;cfargument</span> <span class="nv">name</span><span class="o">=</span><span class="s2">"minutes"</span> <span class="nv">type</span><span class="o">=</span><span class="s2">"numeric"</span> <span class="nv">required</span><span class="o">=</span><span class="s2">"yes"</span><span class="nb">&gt;</span>

 <span class="nb">&lt;cfif</span> <span class="p">(</span><span class="nv">arguments.minutes</span> <span class="o">LT</span> <span class="m">7</span><span class="p">)</span><span class="nb">&gt;</span>
  <span class="nb">&lt;cfset</span> <span class="nv">this.status</span> <span class="o">=</span> <span class="s2">"The water is not boiling yet."</span> <span class="o">/</span><span class="nb">&gt;</span>
 <span class="nb">&lt;cfelseif</span> <span class="p">(</span><span class="nv">arguments.minutes</span> <span class="o">EQ</span> <span class="m">7</span><span class="p">)</span><span class="nb">&gt;</span> 
  <span class="nb">&lt;cfset</span> <span class="nv">this.status</span> <span class="o">=</span> <span class="s2">"It's just barely boiling."</span> <span class="o">/</span><span class="nb">&gt;</span>
 <span class="nb">&lt;cfelseif</span> <span class="p">(</span><span class="nv">arguments.minutes</span> <span class="o">EQ</span> <span class="m">8</span><span class="p">)</span><span class="nb">&gt;</span>
  <span class="nb">&lt;cfset</span> <span class="nv">this.status</span> <span class="o">=</span> <span class="s2">"It's boiling!"</span> <span class="o">/</span><span class="nb">&gt;</span>
 <span class="nb">&lt;cfelse&gt;</span>
  <span class="nb">&lt;cfset</span> <span class="nv">this.status</span> <span class="o">=</span> <span class="s2">"Hot! Hot! Hot!"</span> <span class="o">/</span><span class="nb">&gt;</span> 
 <span class="nb">&lt;/cfif&gt;</span>
 <span class="nb">&lt;cfreturn</span> <span class="nv">this</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;/cffunction&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre>public component function water_boiling(numeric minutes){
 if (arguments.minutes <span class="nt">&lt; 7</span><span class="err">)</span> 
  <span class="na">this</span><span class="err">.</span><span class="na">status =</span><span class="err"> </span><span class="s">"The water is not boiling yet."</span><span class="err">;</span>
 
 <span class="na">else</span> <span class="na">if</span> <span class="err">(</span><span class="na">arguments</span><span class="err">.</span><span class="na">minutes =</span><span class="s">=</span> <span class="na">7</span><span class="err">)</span> 
  <span class="na">this</span><span class="err">.</span><span class="na">status =</span><span class="err"> </span><span class="s">"It's just barely boiling."</span><span class="err">;</span>
 
 <span class="na">else</span> <span class="na">if</span> <span class="err">(</span><span class="na">arguments</span><span class="err">.</span><span class="na">minutes =</span><span class="s">=</span> <span class="na">8</span><span class="err">)</span>
  <span class="na">this</span><span class="err">.</span><span class="na">status =</span><span class="err"> </span><span class="s">"It's boiling!"</span><span class="err">;</span>
 
 <span class="na">else</span> 
  <span class="na">this</span><span class="err">.</span><span class="na">status =</span><span class="err"> </span><span class="s">"Hot! Hot! Hot!"</span><span class="err">;</span>
 
 <span class="na">return</span> <span class="na">this</span><span class="err">;</span>
<span class="err">}</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

Try this example using '5', '7', '8' and '9' for the values of 'minutes'.

When the 'minutes' is 5, here is how the execution goes: Is it 'true' that 5 is less than 7? Yes, it is, so print out the line 'The water is not boiling yet.'.

When the 'minutes' is 7, it goes like this: Is it 'true' that 7 is less than 7? No. Next, is it 'true' that 7 is equal to 7? Yes, it is, so print out the line 'It's just barely boiling'.

When the 'minutes' is 8, it goes like this: Is it 'true' that 8 is less than 7? No. Next, is it 'true' that 8 is equal to 7? No. Next, is it 'true' that 8 is equal to 8? Yes, it is, so print out the line 'It's boiling!'.

Lastly, when total is 9, it goes:" Is it 'true' that 9 is less than 7? No. Next, is it 'true' that 9 is equal to 7? No. Next, is it 'true' that 9 is equal to 8? No. Since none of those are true, execute the 'else' and print the line 'Hot! Hot! Hot!'.

An 'if' block has

*   One 'if' statement whose instructions are executed only if the statement is true
*   Zero or more 'else if' statements whose instructions are executed only if the statement is true
*   Zero or one 'else' statement whose instructions are executed if no 'if' nor 'else if' statements were true

Only *one* section of the 'if' / 'else if' / 'else' structure can have its instructions run. If the 'if' is 'true', for instance, CFML will never look at the 'else if'. Once one block executes, thats it.

### 9. 2. Looping

Another time we use conditional statements is when we want to repeat a set of instructions. Try out this simple example by adding it to your 'PersonalChef.cfc' :

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cffunction</span> <span class="nv">name</span><span class="o">=</span><span class="s2">"countdown"</span> <span class="nv">returnType</span><span class="o">=</span><span class="s2">"component"</span><span class="nb">&gt;</span>
 <span class="nb">&lt;cfargument</span> <span class="nv">name</span><span class="o">=</span><span class="s2">"counter"</span> <span class="nv">type</span><span class="o">=</span><span class="s2">"numeric"</span><span class="nb">&gt;</span>
 <span class="nb">&lt;cfset</span> <span class="nv">this.timer</span> <span class="o">=</span> <span class="s2">""</span> <span class="o">/</span><span class="nb">&gt;</span>
 <span class="nb">&lt;cfloop</span> <span class="nv">condition</span><span class="o">=</span><span class="s2">"</span><span class="s-Interp">#arguments.counter#</span><span class="s2"> GT 0"</span><span class="nb">&gt;</span>
  <span class="nb">&lt;cfset</span> <span class="nv">this.timer</span> <span class="o">&=</span> <span class="s2">"The counter is </span><span class="s-Interp">#arguments.counter#</span><span class="s2">.&lt;br</span><span class="nb">&gt;</span>" /&gt;
  <span class="nb">&lt;cfset</span> <span class="nv">arguments.counter</span><span class="o">--</span> <span class="o">/</span><span class="nb">&gt;</span>
 <span class="nb">&lt;/cfloop&gt;</span>
 <span class="nb">&lt;cfreturn</span> <span class="nv">this</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;/cffunction&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre>public component function countdown(numeric counter){
 this.timer = "";
 while (counter GT 0) { 
  this.timer <span class="err">&</span>= "The counter is #arguments.counter#.<span class="nt">&lt;br&gt;</span>";
  arguments.counter--;
 }
 return this;
}
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

See how that works? The 'counter' starts out as whatever parameter we pass in. The 'while' instruction evaluates the conditional statement 'arguments.counter GT 0' and finds that yes, the counter is greater than zero. Since the condition is true, execute the instructions inside the loop. First print out '"The counter is #Arguments.counter#"' then take the value of 'Arguments.counter', subtract one from it, and store it back into 'Arguments.counter'. Then the loop goes back to the 'condition'/'while' statement. Is it still true? If so, print the line and subtract one again. Keep repeating until the condition is false.

You can also combine conditional statements using logical operators. The most common are known as 'logical and' and 'logical or'. In CFML you can write a 'logical and' with either the word 'and' or with double ampersands like this: '&&'. You can write a 'logical or' with the word 'or' or with double pipes like this: '||'. For each operation, the symbolic representation ( '&&' and '||' ) is more common.

The #1 mistake people encounter when writing conditional statements is the difference between '=' and '=='.

*   '=' is an *assignment*. It means â€œtake whatâ€™s on the right side and stick it into whatever is on the left sideâ€ (or its *telling* not *asking*.)
*   '==' is a *question*. It means â€œis the thing on the right equal to the thing on the leftâ€ (or its *asking* not *telling*.)

## 10. Nothingness & Null

What is *nothingness*? Is there nothingness only in outer space? Really, when we think of *nothing* isnâ€™t it just the absence of something? Ok, thatâ€™s too much philosophy

ColdFusion did not have a way of referring to nothingness until version 9. ColdFusion can recieve a 'NULL' value from an external source and maintain the 'NULL' value until you try to use it. ColdFusion will convert the 'NULL' into an empty string (in the case of queries) or potentially destroy the variable altogether. However now with greater support for 'NULL' values, ColdFusion allows you to pass in and return a 'NULL' value from a method. 'IsNull()' instruction will test for 'NULL' values and return 'true' or 'false'.

If you have three eggs, eat three eggs, then you might think you have *nothing* , but in terms of eggs you have ''. Zero is something, its a number, and its *not nothing*.

A large percentage of the errors you encounter while writing CFML code will involve a variable not existing. You thought something was there, you tried to do something to it, and you canâ€™t do something to nothing so CFML creates an error. Lets rewrite our 'makeeggs' method to illustrate 'NULL' :

<table>
  <tbody>
    <tr>
      <td>
        <strong>Tag</strong>
      </td>
      
      <td>
        <strong>Script</strong>
      </td>
    </tr>
    
    <tr>
      <td>
        <div class="highlight">
          <pre><span class="nb">&lt;cffunction</span> <span class="nv">name</span><span class="o">=</span><span class="s2">"makeeggs"</span> <span class="nv">returnType</span><span class="o">=</span><span class="s2">"component"</span><span class="nb">&gt;</span>
 <span class="nb">&lt;cfargument</span> <span class="nv">name</span><span class="o">=</span><span class="s2">"quantity"</span> <span class="nv">type</span><span class="o">=</span><span class="s2">"numeric"</span><span class="nb">&gt;</span>
 <span class="nb">&lt;cfif</span> <span class="p">(</span><span class="nf">IsNull</span><span class="p">(</span><span class="nv">arguments.quantity</span><span class="p">))</span> <span class="o">/</span><span class="nb">&gt;</span>
  <span class="nb">&lt;cfset</span> <span class="nv">this.makeEggs</span> <span class="o">=</span> <span class="s2">"How am I supposed to make nothingness number of eggs?"</span> <span class="o">/</span><span class="nb">&gt;</span>
 <span class="nb">&lt;cfelse&gt;</span>
  <span class="nb">&lt;cfset</span> <span class="nv">this.makeEggs</span> <span class="o">=</span> <span class="s2">"Making your </span><span class="s-Interp">#arguments.quantity#</span><span class="s2"> eggs!"</span> <span class="o">/</span><span class="nb">&gt;</span>
  <span class="nb">&lt;cfset</span> <span class="nv">this.yourEggs</span> <span class="o">=</span> <span class="nf">ArrayNew</span><span class="p">(</span><span class="m">1</span><span class="p">)</span> <span class="o">/</span><span class="nb">&gt;</span>
  <span class="nb">&lt;cfloop</span> <span class="nv">condition</span><span class="o">=</span><span class="s2">"</span><span class="s-Interp">#ArrayLen(this.yourEggs)#</span><span class="s2"> LT </span><span class="s-Interp">#arguments.quantity#</span><span class="s2">"</span> <span class="o">/</span><span class="nb">&gt;</span>
   <span class="nb">&lt;cfset</span> <span class="nf">ArrayAppend</span><span class="p">(</span><span class="nv">this.yourEggs</span><span class="p">,</span> <span class="s2">"Making an Egg."</span><span class="p">)</span> <span class="o">/</span><span class="nb">&gt;</span>
  <span class="nb">&lt;/cfloop&gt;</span>
 <span class="nb">&lt;/cfif&gt;</span>
 <span class="nb">&lt;cfreturn</span> <span class="nv">this</span> <span class="o">/</span><span class="nb">&gt;</span>
<span class="nb">&lt;/cffunction&gt;</span>
</pre>
        </div>
      </td>
      
      <td>
        <div class="highlight">
          <pre>public component function makeeggs(numeric quantity){
 if(IsNull(arguments.quantity)) {
  this.makeEggs = "How am I supposed to make nothingness number of eggs?";
 } else {
  this.makeEggs = "Making your #arguments.quantity# eggs!";
  this.yourEggs = ArrayNew(1);
  while (ArrayLen(this.yourEggs) <span class="nt">&lt; arguments</span><span class="err">.</span><span class="na">quantity</span><span class="err">)</span>
   <span class="na">ArrayAppend</span><span class="err">(</span><span class="na">this</span><span class="err">.</span><span class="na">yourEggs</span><span class="err">,</span> <span class="err">"</span><span class="na">Making</span> <span class="na">an</span> <span class="na">Egg</span><span class="err">.");</span>
  <span class="err">}</span>
 <span class="na">return</span> <span class="na">this</span><span class="err">;</span>
<span class="err">}</span>
</pre>
        </div>
      </td>
    </tr>
  </tbody>
</table>

Reload the file, call 'frank.makeeggs(3)' then try 'frank.makeeggs()'.

**TODO: Conclusion**

 [1]: http://www.adobe.com/coldfusion
 [2]: http://www.getrailo.com/
 [3]: http://www.openbluedragon.org/