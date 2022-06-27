# maximum-occurence-of-array-element-in-cpp

**PROBLEM STATEMENT**
Given an array, find the most frequent element in it. If there are multiple elements that appear a maximum number of times, print any one of them.

Examples: 

Input : arr[] = {1, 3, 2, 1, 4, 1}

Output : 1

Explanation: 1 appears three times in array which is maximum frequency.

Input : arr[] = {10, 20, 10, 20, 30, 20, 20}

Output : 20

**CODE**
**APPROACH 1**
Brute Force approch  || Time complexity : O(N^2)
```

#include <bits/stdc++.h>

using namespace std;

int main()
{
    int a[]={2,2,2,2,1,1,4,4,5,1};
    int n=sizeof(a)/sizeof(a[0]);
    int max_cnt=0;
    int curr_ele=a[0];
    for(int i=0;i<n-1;i++)
    {
        int cnt=0;
        for(int j=i+1;j<n;j++)
        {
           if(a[i]==a[j])
           {
               cnt++;
           }
           if(cnt>max_cnt)
           {
               max_cnt=cnt;
               curr_ele=a[i];
           }
        }
    }
    cout<<curr_ele;

    return 0;
}

```
**USING HASHING**
Time coplexity: O(N)
```
#include<bits/stdc++.h>
using namespace std;
 int main()
 {
     int a[]={2,2,2,1,1,5,5};
     int n=sizeof(a)/sizeof(a[0]);
     unordered_map<int,int>mp;
     for(int i=0;i<n;i++)
     {
         mp[a[i]]++;
     }
     int cnt=0;
     int curr_ele;
     for(auto i:mp)
     {
         if(i.second>cnt)
         {
             cnt=i.second;
             curr_ele=i.first;
         }
     }
     cout<<curr_ele;
     return 0;
 }
 
 ```
 **BY SORTING THE ARRAY
 TIME COMPLEXITY =O(NLOGN)
 
 ```
 #include<bits/stdc++.h>
using namespace std;
 int main()
 {
     int a[]={3,3,2,2,2,1,5};
     int n=sizeof(a)/sizeof(a[0]);
     sort(a,a+n);
     int max_cnt=1;
     int curr_ele=a[0];
     for(int i=1;i<n;i++)
     {
         int cnt=1;
         if(a[i]==a[i-1])
         {
             cnt++;
         }
         else
         {
             cnt=1;
         }
         if(cnt>max_cnt)
         {
             max_cnt=cnt;
             curr_ele=a[i-1];
         }
     }
     cout<<curr_ele;
     return 0;
 }

```

**MOORE'S VOTING METHOD**
Time complexity: O(N)
```
#include <iostream>
using namespace std;

int maxFreq(int *arr, int n) {
	//using moore's voting algorithm
	int res = 0;
	int count = 1;
	for(int i = 1; i < n; i++) {
		if(arr[i] == arr[res]) {
			count++;
		} else {
			count--;
		}
		
		if(count == 0) {
			res = i;
			count = 1;
		}
		
	}
	
	return arr[res];
}

int main()
{
	int arr[] = {40,50,30,40,50,30,30};
	int n = sizeof(arr) / sizeof(arr[0]);
	int freq = maxFreq(arr , n);
	int count = 0;
	for(int i = 0; i < n; i++) {
		if(arr[i] == freq) {
			count++;
		}
	}
	cout <<"Element " << maxFreq(arr , n) << " occurs " << count << " times" << endl;;
	return 0;
	//This code is contributed by Ashish Kumar Shakya
}

