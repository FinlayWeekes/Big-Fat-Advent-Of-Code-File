using System;
using System.IO;
using System.Reflection.Metadata;
using System.Runtime.InteropServices;
using Microsoft.VisualBasic;

public class Functions
{
    public static string Reverse(string s)
    {
        string temp = "";
        for(int i = s.Length-1; i >= 0; i--)
        {
            temp += Convert.ToString(s[i]);
        }
        return temp;
    }
    public static string Replace(string s, string old, string cur)
    {
        int dif = cur.Length - old.Length;
        if (dif < 0)
            dif = 0;
        for (int i = 0; i < s.Length-old.Length+1; i++)
        {
            bool flag = false;
            int j = 0;
            while (j < old.Length && !flag)
            {
                if (s[i+j] != old[j])
                {
                    flag = true;
                }
                j++;
            }
            
            if (!flag)
            {
                string newS = "";
                for (j = 0; j < s.Length; j++)
                {
                    if (j < i || j > old.Length+i-1)
                    {
                        newS += Convert.ToString(s[j]);
                    } 
                    else if (j == i)
                    {
                        newS += cur;
                    }
                }
                
                s = newS;
                i += dif;
            }
        }

        return s;
    }
    public static List<int> Contains(string s, string old)
    {
        List<int> found = new List<int>();
        for (int i = 0; i < s.Length-old.Length+1; i++)
        {
            bool flag = false;
            int j = 0;
            while (j < old.Length && !flag)
            {
                if (s[i+j] != old[j])
                {
                    flag = true;
                }
                j++;
            }
            
            if (!flag)
            {
                found.Add(i);
            }
        }

        return found;
    }
    public static string[] Group(string s, int am)
    {
        string[] group = new string[s.Length-am+1];

        for (int i = 0; i < s.Length-am+1; i++)
        {
            group[i] = "";
            for (int j = 0; j < am; j++)
            {
                group[i] += Convert.ToString(s[i+j]);
            }
        }
        return group;
    }
    public static string GetLine(int am, int total)
    {
        int i = 0;
        using (StreamReader sr = new StreamReader("text.txt"))
        {
            while (i < am)
            {
                sr.ReadLine();
                i++;
            }
            string line = sr.ReadLine();
            if (line == null)
            {
                Console.WriteLine(total);
                Console.ReadLine();
            }
            return line;
        }
    }
}

public class Program
{
    public static void Main(string[] args)
    {
        int total = 0;
        string line = "";
        int lCount = 0;
        const char split = ' ';

        while ((line = Functions.GetLine(lCount, total)) != null)
        {   
            lCount++;
            string[] lineA = line.Split(split);

            for (int i = 0; i < lineA.Length; i++)
            {
                switch(lineA[i])
                {
                    
                }
            }
        }

        Console.WriteLine(total);
        Console.ReadLine();
    }
}
