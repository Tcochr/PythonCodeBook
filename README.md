# PythonCodeBook
Personal experiments, practice and coding katas in python. Not really meant for public. 



Analysis of Partition() in Quicksort: 

    def partition(a,l,h):
    	p = a[h]
    	i = l - 1
    	for j in range(l,h):
        	if a[j] <= p:
            	i = i+1
            	a[i],a[j] = a[j],a[i]
    	a[i+1],a[h] = a[h],a[i+1]
    	return i + 1
    
    def quicksort(a,l,h):
    	if l < h:
        	pi = partition(a,l,h)
        	quicksort(a,l,pi-1)
        	quicksort(a,pi+1,h)
    
    myArray = {0,1,3,4,2,5}
    
    ----------------------------------------
    
    quicksort1(myArray,l = 0,h = 5)
        pi = p(a,0,5) => in<5>pi1 -> pi = 5
        q_h1(a,l = 0, h = pi=5 -1 = 4)
        q_l1(a,l = pi=5 +1 = 6,h=5)
    
    quicksort_h1(myArray={0,1,3,4,2,5}, l = 0, h = (pi=5 -1 = 4)):
        l<h? -> T
        pi = partition(a={0,1,3,4,2,5}, l = 0, h = 4): in<2>pi_h1 -> = 2
        q_h2(a = {0 1 2 4 3 5}, l = 0, h= pi=2 - 1 = 1)
        q_l2(a = {0 1 2 4 3 5}, l= pi=2 + 1 = 3, h = 4)
        
    quicksort_l1(myArray={0,1,3,4,2,5}, l = (pi=5 +1 = 6), h = 5):
        l<h ? -> X
    
    quicksort_h2(myArray={0,1,3,4,2,5}, l = 0, h = 1):
        l<h ? -> T
        pi = p_h2(a = {0 1 3 4 2 5}, l = 0,  h = 1): in<1>pi_h2 -> = 1
        quicksort(a={0 1 2 4 3 5}, l = 0, h = pi=1 -1 = 0) -> X
        quicksort(a={0 1 2 4 3 5}, l = pi=1 +1 = 2, h = 1) -> X
    
    quicksort_l2(myArray={0,1,3,4,2,5}, l = 3, h = 4):
        l=3 < h=4 ? -> T
    	 pi = p_l2(myArray={0 1 2 4 3 5}, l = 3, h = 4): in<3> -> = 3
        quicksort(a={0 1 2 3 4 5}, l = 3, h = pi=3 + 1 = 4) -> X
        quicksort(a={0 1 2 3 4 5}, l= pi= 3 + 1 = 4, h = 4) -> X
    
    p_1(a,0,5)
        p = a[5] = 5
        i = -1
        for j in range(0,5)
       	 j = 0
       		 a[j=0]=0 <= p=5? -> T -> i = i+1 -> i = 0
       			 a[i=0],a[j=0] = a[j=0],a[i=0] => a = { 0,1,3,4,2,5}
       	 j = 1
       		 a[j=1]=1 <= p=5? -> T -> i = i+1 -> i = 1
       			 a[i=1],a[j=1] = a[j=1],a[j=1] => a = {0,1,3,4,2,5}
       	 j = 2
       		 a[j=2]=3 <= p=5? -> T -> i = i+1 -> i = 2
       			 a[i=2],a[j=2] = a[i=2],a[j=2] => a = {0,1,3,4,2,5}
       	 j = 3
       		 a[j=3]=4 <= p=5? -> T -> i = i+1 -> i = 3
       			 a[i=3],a[j=3] = a[j=3],a[i=3] => a = {0,1,3,4,2,5}
       	 j = 4
       		 a[j=4]=2 <= p=5? -> T -> i = i+1 -> i = 4
       			 a[i=4],a[j=4] = a[j=4],a[i=4] => a = {0,1,3,4,2,5}
        a[i+1=5],a[5] = a[5],a[i+1=5] => a = {0,1,3,4,2,5}
        return i=4 + 1 =5    									 out <5>
    
    p_h1(a={0,1,3,4,2,5}, l = 0, h = 4):
        p = a[h=4] = 2
        i = l=0 - 1 = -1
        for j in range(l=0, h = 4):
       	 j = 0
       		 a[j=0]=0 <= p=2? -> T -> i=-1 +1 -> i = 0
       		      a[i=0],a[j=0] = a[i=0],a[j=0]
       	 j = 1
       		 a[j=1]=1 <= p=2? -> T -> i=0 +1 -> i = 1
       			 a[i=1],a[j=1] = a[j=1],a[i=1] => a = {0,1,3,4,2,5}
       	 j = 2
       		 a[j=2]=3 <= p=2? -> F -> j++
       	 j = 3
       		 a[j=3]=4 <= p=2? -> F -> j++
       	 a[i=1 +1 =2],a[h=4] = a[h=4],a[i=1 +1 =2] => {0 1 2 4 3 5}
       	 return i=1 + 1 =2   									 out<2>->q_h1
     		 
    p_h2(a = {0 1 3 4 2 5}, l = 0, h = 1):
        p = a[h=1] = 1
        i = l=0 -1 = -1
        for j in range(l=0,h=1):
       	 j = 0
       		 a[j=0]=0 <= p=1? -> T -> i=-1++ -> i=0
        a[i=0+1=1],a[h=1] = a[h=1],a[i=0+1=1]
        return i=0+1 = 1    										 out<1>->q_h2
    
    p_l2(myArray={0 1 2 4 3 5}, l = 3, h = 4):
        p = a[h=4] = 3
        i = l=3 - 1 = 2
        for j in range(l=3,h=4)
       	 j = 3
       		 a[j=3]=4 <= p=3 ? -> F
        a[i=2 +1 = 3],a[h=4] = a[h=4],a[i=2 +1 = 3] => a={0 1 2 3 4 5}
        return i=2 + 1 = 3    									 out<3>->q_l2
    a = {0 1 2 3 4} -> [FuckYeah]
    
Analysis of Recursive Word Combinations: 

    key = "a b c"
    people = 3
    list = []
    
    function(key,length,list,word=""):
      if length == 0:
          list.append(word)
      for i in key:
          new = word + key[i]
          function(key,length-1,list,new)
    
    f(key,people,list):
    
    f("a b c", 3, [],"")  
        for i in key:
        
       	 i = 0:
       		 new = "" + key[i=0='a'] = 'a'
       		 f(key,3-1=2,[],new='a')

          
       			 i = 0:
       				 new = "a" + key[i=0='a'] = 'aa'
       				 f(key,2-1=1,[],new='aa')
       					 i = 0:
       						 new = "aa" + key[i=0='a']
       						 f(key,1-1=0,new="aaa")
       							 len == 0 ? -> T
       								 out = [aaa]
       					 i = 1:
       						 new = "aa" + key[i=1='b']
       						 f(key,1-1=0,new='aab')
       							 len == 0 ? -> T
       								 out = [aab]
       					 i = 2:
       						 new = "aa" + key[i=2='c']
       						 f(key,1-1=0,new='aac')
       							 len == 0 ? -> T
       								 out = [aac]
                
       			 i = 1:
       				 new = "a" + key[i=1='b'] = 'ab'
       				 f(key,2-1=1,[],new='ab'
       					 i = 0:
       						 new = 'ab' + key[i=0='a']
       						 f(key,1-1=0,new='aba')
       							 len == 0 ? -> T
       								 out = [aba]
       					 i = 1:
       						 new = 'ab' + key[i=1='b']
       						 f(key,1-1=0,new='abb')
       							 len == 0 ? -> T
       								 out = [abb]
       					 i = 2:
       						 new = 'ab' + key[i=2='c']
       						 f(key,1-1=0,new='abc')
       							 len == 0 ? -> T
       								 out = [abc]
                
       			 i = 2:
       				 new = "a" + key[i=2='c'] = 'ac'
       				 f(key,2-1=1,[],new='ac')
       					 i = 0:
       						 new = 'ac' + key[i=0='a']
       						 f(key,1-1=0,new='aca')
       							 len == 0 ? -> T
       								 out = [aca]
       					 i = 1:
       						 new = 'ac' + key[i=1='b']
       						 f(key,1-1=0,new='acb')
       							 len == 0 ? -> T
       								 out = [acb]
       					 i = 2:
       						 new = 'ac' + key[i=2='c']
       						 f(key,1-1=0,new='acc')
       							 len == 0 ? -> T
       								 out = [acc]

                
       	 i = 1:
       		 new = "" + key[i=1='b'] = 'b'
       		 f(key,2-1=1,[],new='b')
          
       			 i = 0:
       				 new = 'b' + key[i=1='a'] = 'ba'
       				 f(key,2-1=1,[],new='ba')
       					 i = 0:
       						 new = 'ba' + key[i=0='a']
       						 f(key,1-1=0,new='baa')
       							 len == 0 ? -> T
       								 out = [baa]
       					 i = 1:
       						 new = 'ba' + key[i=1='b']
       						 f(key,1-1=0,new='bab')
       							 len == 0 ? -> T
       								 out = [bab]
       					 i = 2:
       						 new = 'ba' + key[i=2='c']
       						 f(key,1-1=0,new='bac')
       							 len == 0 ? -> T
       								 out = [bac]
                
       			 i = 1:
       				 new = 'b' + key[i=2='b'] = 'bb'
       				 f(key,2-1=1,[],new='bb')
       					 i = 0:     
       						 new = 'bb' + key[i=0='a']
       						 f(key,1-1=0,new='bba')
       							 len == 0 ? -> T
       								 out = [bba]
       					 i = 1:
       						 new = 'bb' + key[i=1='b']
       						 f(key,1-1=0,new='bbb')
       							 len == 0 ? -> T
       								 out = [bbb]
       					 i = 2:
       						 new = 'bb' + key[i=2='c']
       						 f(key,1-1=0,new='bbc')
       							 len == 0 ? -> T
       								 out = [bbc]
  
       			 i = 2:
       				 new = 'b' + key[i=3='c'] = 'bc'
       				 f(key,2-1=1,[].new='bc')
       					 i = 0:     
       						 new = 'bc' + key[i=0='a']
       						 f(key,1-1=0,new='bca')
       							 len == 0 ? -> T
       								 out = [bca]
       					 i = 1:
       						 new = 'bc' + key[i=1='b']
       						 f(key,1-1=0,new='bcb')
       							 len == 0 ? -> T
       								 out = [bcb]
       					 i = 2:
       						 new = 'bc' + key[i=2='c']
       						 f(key,1-1=0,new='bcc')
       							 len == 0 ? -> T
       								 out = [bcc]

                
       	 i = 2:
       		 new = "" + key[i=2='c'] = 'c'
       		 f(key,1-1=0,[],new='c')
          
       			 i = 0:
       				 new = 'c' + key[i=0='a'] = 'ca'
       				 f(key,2-1=1,[],new='ca')
       					 i = 0:
       						 new = 'ca' + key[i=0='a']
       						 f(key,1-1=0,new='caa')
       							 len == 0 ? -> T
       								 out = [cca]
    
       					 i = 1:
       						 new = 'ca' + key[i=1='b']
       						 f(key,1-1=0,new='cab')
       							 len == 0 ? -> T
       								 out = [cab]
       					 i = 2:
       						 new = 'ca' + key[i=2='c']
       						 f(key,1-1=0,new='cac')
       							 len == 0 ? -> T
       								 out = [cac]
       			 i = 1:
       				 new = 'c' + key[i=1='b'] = 'cb'
       				 f(key,2-1=1,[],new='cb')
       					 i = 0:     
       						 new = 'cb' + key[i=0='a']
       						 f(key,1-1=0,new='cba')
       							 len == 0 ? -> T     
       								 out = [cba]
    
       					 i = 1:
       						 new = 'cb' + key[i=1='b']
       						 f(key,1-1=0,new='cbb')
       							 len == 0 ? -> T     
       								 out = [cbb]
    
       					 i = 2:
       						 new = 'cb' + key[i=2='c']
       						 f(key,1-1=0,new='cbc')
       							 len == 0 ? ->  T
       								 out = [cbc]
       			 i = 2:  
       				 new = 'c' + key[i=2='c'] = 'cc'
       				 f(key,2-1=1,[],new='cc')
       					 i = 0:
       						 new = 'cc' + key[i=0='a']
       						 f(key,1-1=0,new='cca')
       							 len == 0 ? -> T
       								 out = [cca]
       					 i = 1:
       						 new = 'cc' + key[i=1='b']
       						 f(key,1-1=0,new='ccb')
       							 len == 0 ? -> T    
       								 out = [ccb]
    
       					 i = 2:
       						 new = 'cc' + key[i=2='c']
       						 f(key,1-1=0,new='ccc')
       							 len == 0 ? -> T
       								 out = [ccc]

Quicksort Analysis: 

    *f, let Q be:
       Quicksort(a,p,r)
    1:     if p < r:
    2: 		 q = partition(a,p,r)
    3: 		 quicksort(a,p,q-1)
    4: 		 quicksort(a,q+1,r)
    
    *f, let p be:
      partition(a,p,r)
    5:     x=a[r]
    6:    i=p-1
    7: 	 for j=p to r-1:
    8:    	 if a[j] <= x:
    9: 			 i = i+1
    10:  			 a[i]<->a[j]
    11:     a[i+1]<->a[r]
    12:  	 return i+1
    
    *1: a = 3 2 1 0
    
    Q(a,0,3):
        p < r ? -> T
        q = p0_Q0(a,0,3) -> 0  
        Q1(a,p=0,q-1=-1)
        Q2(a,q+1=1,r=3)
    
    Q1(a,0,-1):
        p < r ? -> F
       	 EXIT
    Q2(a,1,3):
        p < r ? -> T
        q = p1_Q2(a,1,3) -> 1
        Q3(a,1,q-1=1-1=0)
        Q4(a,q+1=1+1=2,r=3)
    Q3(a,1,0):
        p < r ? -> F
       	 EXIT
    Q4(a,2,3):
        p < r ? -> T
        q = p2_Q4(a,2,3) -> 2
        Q5(a,2,q-1= 1) -> EXIT
        Q6(a,q+1=3,3) -> EXIT
    -> EXIT
    
    p2_Q4(a,2,3)
    
       	 *3: a = 0 3 1 2
    
        x = a[3] = 2
        i = q-1 = 1
        for j=2 to 2:
       	 EXIT
        a[i+1] <-> a[r]
    
       	 *4: a = 0 3 2 1
    
        out -> 2
    
    p1_Q2(a,1,3):
    
       	 *2: a = 0 2 1 3
    
        x = a[r] = 3
        i = p-1 = 0
        for j=0 to 2:
       	 a[0] <= x=3 ? -> F
       	 j+=1,j=1
       	 a[1] <= x=3 ? -> F
       	 j+=1, j=2
       	 a[2] <= x=3 ? -> F
        a[i+1=1] <-> a[r=3]
    
       	 *3: a = 0 3 1 2
    
        out -> i+1 = 1
    
    p0_Q0(a,0,3):
        x = a[r=3] = 0
        i = p-1 = 0-1 = -1
        for j=0 to r-1 = 2:
       	 a[0] <= x=0 ? -> F
       	 ->j+=1, j=1
       	 a[1] <= x=0 ? -> F
       	 ->j+=1, j=2
       	 a[2] <= x=0 ? -> F
       	 -> EXIT
        a[i+1=0] <-> a[r=3]
    
       	 *2: a = 0 2 1 3
    
        out -> i+0 = 0
     
    
    TIME ANALYSIS:
    
    Line   	 Cost   	 Time
    1   	 c1(7)   	 n+3
    2   	 c2(3)   	 n-1
    3   	 c3(3)   	 n-1
    4   	 c4(3)   	 n-1
    5   	 c5(3)    	 n-1
    6   	 c6(3)   	 n-1
    7   	 c7   	 sm(j=p->n-1)tj
    8   	 c8   	 sm(j=p->n-1)tj
    9   	 c9   	 sm(j=p->n-1)tj
    10   	 c10    	 sm(j=0->n-1)tj
    11   	 c11(3)   	 n-1
    12   	 c12(3)   	 n-1
    
    T(n) = c1(n+3) + c2(n-1) + c3(n-1) + c4(n-1) + C5(n-1) + C6(n-1)
    + C7sm(j=p->n-1)tj+ C8sm(j=p->n-1)tj + C9sm(j=p->n-1)tj + C10sm(j=p->n-1)tj
    +C11(n-1) + c12(n-1)
    
    Consider thus:
        sm(k=1->n)k = n(n+1)/2
       	 and
        sm(k=1->n)a = an
        
        such that:
       	 sm(j=p->n-1)tj = (n-1)((n-1)+1)/2 - p(p+1)/2 subtracting this to account for j=p
       			 = (n^2-n)/2 - p^2+p/2
       			 = ((n^2-n) + p^2 + p)/2
    
    T(n) = c1(n+3) + c2(n-1) + c3(n-1) + c4(n-1) + C5(n-1) + C6(n-1)
    + C7((n^2-n) + p^2 + p)/2+ C8((n^2-n) + p^2 + p)/2 + C9((n^2-n) + p^2 + p)/2 + C10((n^2-n) + p^2 + p)/2
    +C11(n-1) + c12(n-1)
    
    = n^2(c7+c8+c9+c10/2) - ((p^2+p)(c7+c8+c9+c10/2)) + n(c7+c8+c9+c10/2) + n(c+11+c12+c13) -3(c2+c3+c6+c6+c11+c12+c13)
    -4c4
    =(n^2-p^2-p-n)(c7+c8+c9+c10)/2 + n(c+11+c12+c13) + -3h(c2+c3+c6+c6+c11+c12+c13) + c4
    
    Therefore there exists some function g(n) st f(n) <= c*g(n): n > k given a c and a k where f(n) defines the runtime of the algorithm and g(n) defines some upper bound function which here refers to n^2.
    
    Hence, T(n) is O(n^2) by the above proof

Three Arrays Analysis: 
![ThreeArrays-images-0](https://github.com/Tcochr/PythonCodeBook/assets/29736306/b8392dad-5434-4400-8688-c5a14e032487)
![ThreeArrays-images-1](https://github.com/Tcochr/PythonCodeBook/assets/29736306/f6abc14d-ef89-4868-bafd-aa9fcf81babe)
![ThreeArrays-images-2](https://github.com/Tcochr/PythonCodeBook/assets/29736306/cfe49801-c99f-40b8-bb14-95b8a7fae4a1)
![ThreeArrays-images-3](https://github.com/Tcochr/PythonCodeBook/assets/29736306/9ca3f76a-61bf-48c1-8daf-dfd267d2250e)
![ThreeArrays-images-4](https://github.com/Tcochr/PythonCodeBook/assets/29736306/588f60c1-80fc-43d8-b1d4-6ddabfd6291f)
![ThreeArrays-images-5](https://github.com/Tcochr/PythonCodeBook/assets/29736306/22c09894-c5c2-4142-b7e2-99234556ca11)













