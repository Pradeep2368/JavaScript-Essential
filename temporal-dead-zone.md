<div align="center">
  <b style="font-size:20px;">"Beware the Temporal Dead Zone: where variables live, but aren't quite ready to be used."</b>
</div>

## Temporal Dead Zone

Definition:

 The *Temporal Dead Zone* is the time between when a variable is declared (using `let` or `const`) and when it is first initialized(assigned a value). <br><br> 

*In simple terms:*

- Temporal Dead Zone (TDZ) is the period when variable exists but can't be used yet.
- It starts from the point the variable is declared and ends when the value is assigned.
<br>

During this time, if you try to access the variable, you'll get a reference error (<span style="color: red;">ReferenceError: Cannot access 'x' before initialization</span>).

### Lets take a simple example illustrating TDZ: 
```javascript
console.log(a); //In you devTool under console tab: ReferenceError: Cannot access 'a' before initialization
let a = 5;
```

Before the line where `a` is declared and initialized, accessing `a` results in a ReferenceError. This is because `a` is in the TDZ from the start of its block until its initialization.

****
<br>
<br>

## Are `let` and `const` declaration hoisted? How is it different from `var`?

- Both `let` and `const` declarations are hoisted, but there's an important difference compared to `var`. <br><br> When a variable is hoisted, it means the declaration is moved to the top of its scope during the compile phase. However, in case of `let` and `const`, even though the declaration are hoisted, they are placed in the `Temporal Dead Zone (TDZ)` until the code execution reaches the line where they are initialized.  


***
