# Currency Converter

## Convert Button!
![](https://user-images.githubusercontent.com/114388400/194490909-acca1615-fe8f-4aeb-9151-8c9c04c6c17f.png)

Select currency 1  and convert to currency 2  
## Exchange Button
![](https://user-images.githubusercontent.com/114388400/194491625-36a5c1d6-3cbd-4c51-83f8-23ab0b5132cd.png)

Set Currency 1 as Currency 2 and vice-versa  

## Approach Used

#### Note: We used Dollar as Base currency to do Calculations.

### Created Object with all Currency Shortforms as key.  
Each of these key represent array consist of two items.  
First is a Number which represent how much of that currency will come in 1 Dollar.  
Second is their Full Name.  
		
### Functions to Convert Currency
This function uses simple mathematics to evaluate desired currency.  
which is :  
let y, z be object and n, m be quantity  
1*x = n*y  
1*x = m*z  
then 1*y = m*z/n   
hence k*y = k*m*z/n  

### Function to Exhchange Currency
This function replace the value inside both <selected> and <input>

### Template
we are using v-for to render all <option> of <select> two times using the object created.  
Mapping Currency ref to <select> and val ref to <input> to store their values which is used by functions to perform calculations
