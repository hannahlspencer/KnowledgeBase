# Comments and Formatting

### Comments

Proper use of comments is to compensate for our failure to express ourself in code. Comments lie: the older they are, the further they probably are from the code they describe, and the more likely they are wrong. So explain yourself in code, eg.&#x20;

`// Check if employee is eligible for benefits`&#x20;

`if((employee.flags && HOURLY_FLAG) && employee.age > 65)`

vs.

`if(employee.isEligibleForBenefits())`

### Formatting

Formatting is about communicating the care that's gone into the code. Aim for small, concise files containing small, concise methods. Related concepts should be vertically close, with spaces between unrelated concepts to naturally break up the file. Variables should be declared as close to their use as possible, but instance variables should be declared at the top of the class they're in (presuming they are used by many methods in the class)

If one function calls another it should be vertically close, and the caller should be above the callee.
