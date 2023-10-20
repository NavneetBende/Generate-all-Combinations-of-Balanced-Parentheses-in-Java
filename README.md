# Generate-all-Combinations-of-Balanced-Parentheses-in-Java

All Combinations of Balanced Parentheses in Java
Today in this article we will discuss the program to generate all combinations of balanced parentheses in Java programming language. We are given an integer N representing the number of pairs of parentheses, the task is to generate all combinations of well-formed(balanced) parentheses.

Factorial of a Number using Recursion in Java
Method 1:
Create a recursive function that accepts a string say s, count of opening brackets say, o and count of closing brackets say, c and the value of n.
If the value of opening bracket and closing bracket is equal to n then print the string and return.
If the count of opening bracket is greater than count of closing bracket then call the function recursively.
If the count of opening bracket is less than n then call the function recursively.
All Combinations of Balanced Parentheses
Run
import java.io.*;
 
class Main {

    static void _printParenthesis(char str[], int pos, int n, int open, int close)
    {
        if (close == n) {
            for (int i = 0; i < str.length; i++)
                System.out.print(str[i]);
            System.out.println();
            return;
        }
        else {
            if (open > close) {
                str[pos] = '}';
                _printParenthesis(str, pos + 1, n, open, close + 1);
            }
            if (open < n) {
                str[pos] = '{';
                _printParenthesis(str, pos + 1, n, open + 1, close);
            }
        }
    }
 
    static void printParenthesis(char str[], int n)
    {
        if (n > 0)
            _printParenthesis(str, 0, n, 0, 0);
        return;
    }
 
  
    public static void main(String[] args)
    {
        int n = 3;
        char[] str = new char[2 * n];
        printParenthesis(str, n);
    }
}
Output :
{{{}}}
{{}{}}
{{}}{}
{}{{}}
{}{}{}
Method 2:
In this method we write the simple code for the above algorithm.

Method 2 : Code in Java
Run
import java.util.*;
 
class Main{
 
    public static void generateParenthesis(int n, int open, int close, String s, ArrayList ans)
    {
        if (open == n && close == n) {
            ans.add(s);
            return;
        }
       
        if (open < n) {
            generateParenthesis(n, open + 1, close, s + "{", ans);
        }
       
        if (close < open) {
            generateParenthesis(n, open, close + 1, s + "}",ans);
        }
    }
 
    public static void main(String[] args)
    {
        int n = 3;
       
        ArrayList<String> ans = new ArrayList<>();
       
        generateParenthesis(n, 0, 0, "", ans);
        for (String s : ans) {
            System.out.println(s);
        }
    }
}   
Output :
{{{}}}
{{}{}}
{{}}{}
{}{{}}
{}{}{}
