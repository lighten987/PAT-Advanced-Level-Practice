# PAT-Advanced-Level-Practice
***做一题更新一题，题目顺序比较随机，待全部做完再好好整理***

/*
1001   
A+B Format  
**if else 语句中，用升序去做有个测试点通不过** 

>#include<iostream>  
using namespace std;  
int main()  
{  
	long a,b,c;  
	cin>>a>>b;  
	c=a+b;  
	if(c<0)  
	{  
		cout<<"-";  
		c=-c;  
	}  
	if(c>=1000000){  
        printf("%d,%03d,%03d",c/1000000,c%1000000/1000,c%1000);  
    }else if(c>=1000){  
        printf("%d,%03d",c/1000,c%1000);  
    }else{  
        printf("%d",c);  
    }  
}  
*/  

/*  
1002   
A+B for Polynomials  
**多项式求和，用数组做   注意输出格式**   

>#include<iostream>  
using namespace std;  
int main()  
{  
	float a[1001]={0};  
	int m,n,max1=0,max2=0,max;  
	cin>>m;  
	for(int i=0;i<m;i++)  
	{  
		int zhishu;  
		cin>>zhishu;  
		float temp;  
		cin>>temp;  
		a[zhishu]+=temp;  
		if(zhishu>max1)max1=zhishu;  
	}     
	cin>>n;     
	for(int j=0;j<n;j++)  
	{  
		int zhishu;  
		cin>>zhishu;  
		float temp;  
		cin>>temp;  
		a[zhishu]+=temp;  
		if(zhishu>max2)max2=zhishu;  
	}  
	max=(max1>max2?max1:max2);  
	int count=0;  
	for(int i=0;i<=max;i++)  
	{  
		if(a[i]!=0)count++;  
	}  
	cout<<count;  
	for(int i=max;i>=0;i--)  
	{  
		if(a[i]!=0)  
		printf(" %d %.1f",i,a[i]);  
	}   
	return 0;  
}  
*/  

/*  
1005   
**Spell It Right 给一个数，计算各位数和，用英文输出**   

>#include<iostream>  
using namespace std;  
int main()  
{   
  string s;  
	cin>>s;  
	int sum=0;  
	for(int i=0;i<s.size();i++)  
	{  
		sum+=s[i]-'0';  
	}  
	string spell[10]={"zero","one","two","three","four","five","six","seven","eight","nine"};  
	string res = "";  
    while(sum >= 10){  
        res = " " + spell[sum%10] + res;   //字符串骚操作   一步一步往前走   
        sum /= 10;  
    }  
    if(sum < 10)  
        res = spell[sum] + res;  
    cout << res << endl;  
	return 0;  
}  
*/   

/*  
1006   
**Sign In and Sign Out  输出最早来和最晚走的id**   

>#include<iostream>  
using namespace std;  
int main()  
{  
	int n;  
	cin>>n;  
	string max;  
	string min;  
	int xiao=999999;  
	int da=000000;  
	for(int i=0;i<n;i++)  
	{  
		string num;  
		int a,b,c,d,e,f;  
		int lai,qu;  
		cin>>num;  
		scanf("%d:%d:%d %d:%d:%d",&a,&b,&c,&d,&e,&f);  
		lai=a*10000+b*100+c;  
		qu=d*10000+e*100+f;  
		if(lai<xiao)  
		{  
		min=num;  
		xiao=lai;  
		}  
		if(qu>da){  
	    max=num;  
	    da=qu;  
		}  
	}   
	cout<<min<<" "<<max;  
	return 0;  
}  
*/  

/*  
1008   
Elevator  
 
>#include<iostream>  
using namespace std;  
int main()  
{  
	int count;  
	cin>>count;  
	int a[count]={0};  
	for(int i=0;i<count;i++)  
	{   
		cin>>a[i];  
	}  
	int sum=0;  
	int temp=0;  
	for(int i=0;i<count;i++)  
	{  
		if(a[i]>temp)sum+=(a[i]-temp)*6+5;//上升  
		else sum+=(temp-a[i])*4+5; //下降或原地不动   
		temp=a[i];  
	}  
	cout<<sum;  
	return 0;  
}  
*/  

/*  
1007   
**Maximum Subsequence Sum 求最大子串和 输出和与开始，结束的值**  
 
***思路：遍历开头，再遍历后面的和，有新的大值更新max并更新头尾 ***   
>#include<iostream>  
using namespace std;  
int main()  
{  
	int n;  
	cin>>n;  
	int a[n] = {0};  
	int begin,end;  
	for(int i = 0; i< n; i++)  
	{  
		cin>>a[i];  
	}   
	int max = -1; 	   
    for(int i = 0; i<n-1; i++){  
	    int temp = 0;  
    	for(int j = i; j< n; j++){  
    		temp += a[j];  
    		if(temp > max){  
    			max = temp;  
    			begin = a[i];  
    			end = a[j];  
			}  
		}  
	}  
	if(max<0){  
		max = 0;  
		begin = a[0];  
		end = a[n-1];  
	}  
	cout<<max<<" "<<begin<<" "<<end<<endl;  
	return 0;  
}  
  
//标准答案  
>#include <cstdio>  
int a[10001];  
int main(){  
	int n, sum = -1, tmp, start, end;  
	scanf("%d", &n);  
	for (int i = 0; i < n; i++)  
		scanf("%d", &a[i]);  
	for (int i = 0; i < n; i++){  
		tmp = 0;  
		for (int j = i; j < n; j++){  
			tmp += a[j];  
			if (tmp > sum){  
				sum = tmp;  
				start = a[i];  
				end = a[j];  
			}  
		}  
	}  
	if (sum < 0){  
		printf("0 %d %d\n", a[0], a[n-1]);  
		return 0;  
	}   
	printf("%d %d %d\n", sum, start, end);  
	return 0;  
}   
*/  

/*  
1011   
**World Cup Betting**   

>#include<iostream>  
using namespace std;  
int main()  
{  
	char c[3]={'W','T','L'};  
	double sum=1.0,max=0;  
	int count;  
	for(int j=0;j<3;j++)  
	{  
		double max=0;		  
	for(int i=0;i<3;i++)  
	{  
	    double a[3]={0.0};  
	//	scanf("lf",&a[i]);  
	    cin>>a[i];   
		if(a[i]>max)  
		{  
			max=a[i];  
			count=i;  
		}  
	}   
	cout<<c[count]<<" ";  
	sum*=max;  
    }  
    sum=(sum*0.65-1)*2;  
    printf("%.2f",sum);  
	return 0;  
}  

//标准答案  
>#include<cstdio>  
char S[3] = {'W','T','L'};  
 int main(){  
    double ans = 1.0, tmp, a;  
    int idx;                        //记录每行最大数字的下标  
    for(int i = 0; i < 3; i++){  
        tmp = 0.0;  
        for(int j = 0; j < 3; j++){ //寻找该行最大的数字存于 tmp  
            scanf("%lf", &a);  
            if(a > tmp){  
                tmp = a;  
                idx = j;  
            }   
        }  
        ans *= tmp;                 //按公式累乘  
        printf("%c ",S[idx]);       //输出对应的比赛结果   
    }   
    printf("%.2f", (ans * 0.65 - 1) * 2);   //输出最大收益  
    return 0;   
 }   
*/  

/*  
1025     
**PAT Ranking  读入区块成绩，分别输出几个排名**

***思路：node里面填充，第一个参数为小循环次数，小循环里面装入vector，更新local，根据成绩排序，  
          更新local_rank，放入大的vector，大的vector在小循环执行完后根据成绩更新final_rank  
          初始化小vector时一开始放在小循环外，然后clear，测试例子通不过，将小vector放入小循环开头初始化  
          例子可以通过，但是测试点部分通过   
	  通过重新审题，发现问题可能出在cmp函数里，即相同成绩的按序号排序上，更改后AC***   
 
>#include<iostream>  
#include<vector>  
#include<algorithm>  
using namespace std;  
struct node  
{  
	string id;  
	int score;  
	int final_rank;  
	int local;  
	int local_rank;  
};  
bool cmp(node a, node b)  //按成绩降序   
{  
	return (a.score!=b.score)? a.score>b.score : a.id<b.id;  
}  
int main()  
{     
    int count_kuai;  
	vector<node>vcount;     
	cin>>count_kuai;  
	int sum = 0;  
	for(int i = 0 ; i< count_kuai; i++){  
	    vector<node>v;  
		int m;  
		cin>>m;  
		sum += m;  
		for(int j = 0; j<m; j++){  
			node temp;  
			cin>>temp.id>>temp.score;  
			temp.local = i+1;  //更新local   
			v.push_back(temp);   
		}  
		//更新local_rank   
		sort(v.begin(),v.end(),cmp);  
		int k = 1;  
		v[0].local_rank = 1;  
		vcount.push_back(v[0]);   	
		for(int j = 1; j<m; j++){  
			if(v[j].score != v[j-1].score){  
				k++;  
				v[j].local_rank = k;  
			}  
			else if(v[j].score == v[j-1].score){  
				v[j].local_rank = v[j-1].local_rank;  
				k++;  
			}  
			vcount.push_back(v[j]);	  
//			v.clear();  
//		        for(int i = m-1; i>=0; i++){  
//			v.pop_back(v[i]);  
//		}  
		}  
	}   
	//更新final_rank   
	sort(vcount.begin(),vcount.end(),cmp);  
	int t = 1;  
	vcount[0].final_rank = 1;  
	for(int i = 1; i<vcount.size(); i++){  
		if(vcount[i].score != vcount[i-1].score){  
			t++;  
			vcount[i].final_rank = t;  
		}  
		else if(vcount[i].score == vcount[i-1].score){  
			vcount[i].final_rank = vcount[i-1].final_rank;  
			t++;  
		}  
	}   
	//输出  
	cout<<sum<<endl;  
	for(int i = 0; i<vcount.size(); i++){  
		cout<<vcount[i].id<<" "<<vcount[i].final_rank<<" "<<vcount[i].local<<" "<<vcount[i].local_rank<<endl;  
	}   
	return 0;  
}  
*/  

/*  
1036    
**Boys vs Girls 给出一系列学生的信息，第一排输出女生中最高成绩对应的名字和学号，  
              第二排输出男生中最低成绩对应的名字和学号，第三排输出女生与男生成绩的差值  
	      若有对应项没有信息，对应位置输出Absent，第三排输出NA**  
			  
***思路：用两个vector<node>分别存储信息，排序后判断再计算***   
 
>#include<iostream>  
#include<vector>  
#include<algorithm>  
#include<cstring>  
using namespace std;  
struct node  
{  
	string name;  
	char gender;  
	string id;  
	int grade;  
};  
bool cmp1(node a, node b)  //升序   
{  
	return a.grade<b.grade;  
}  
bool cmp2(node a, node b)  //降序   
{  
	return a.grade>b.grade;  
}  
int main()   
{  
	int n;  
	cin>>n;  
	int count_m = 0;  
	int count_f = 0;   
	vector <node> m,f;  
	//分别存入对应向量   
	for(int i = 0; i<n; i++){  //两种读入方式都可以   
//		string name;  
//	    char gender;  
//	    string id;  
//	    int grade;  
//		cin>>name>>gender>>id>>grade;  
//		m.push_back(node{name,gender,id,grade});  	 
        node temp;  
        cin>>temp.name>>temp.gender>>temp.id>>temp.grade;  
		if(temp.gender == 'M'){  
			m.push_back(temp);  
			count_m++;  
		}  
		else if(temp.gender == 'F'){  
			f.push_back(temp);  
			count_f++;  
		}  
	}  
	//排序  
	sort(m.begin(),m.end(),cmp1);  //男生升序   
	sort(f.begin(),f.end(),cmp2);//女生降序   
	//分类输出   
	if(count_m>0 && count_f>0){  
	//	printf("%s %s\n",f[0].name.c_str(),f[0].id.c_str());   
	//	printf("%s %s\n",m[0].name.c_str(),m[0].id.c_str());  
		cout<<f[0].name.c_str()<<" "<<f[0].id.c_str()<<endl;  
		cout<<m[0].name.c_str()<<" "<<m[0].id.c_str()<<endl;  
		cout<<f[0].grade-m[0].grade<<endl;  
	}  
	else if(count_m == 0 && count_f != 0){  
		printf("%s %s\n",f[0].name.c_str(),f[0].id.c_str());  
		cout<<"Absent"<<endl;  
		cout<<"NA"<<endl;  
	}  
	else if(count_f == 0 && count_m != 0){  
		cout<<"Absent"<<endl;  
		printf("%s %s\n",m[0].name.c_str(),m[0].id.c_str());  
		cout<<"NA"<<endl;  
	}  
	else if(count_f == 0 && count_m == 0){  
		cout<<"Absent"<<endl;  
		cout<<"Absent"<<endl;  
		cout<<"NA"<<endl;  
	}  
	return 0;  
}   
*/  

/*  
1037   
**Magic Coupon 给出两排数据，从中选出相同个数进行计算，输出最大乘积和** 
			  
***思路：用四个vector<int>分别两排的正负数，读取相应个数对应较小的为size为项数 累加求和***   
 
>#include<iostream>  
#include<vector>  
#include<algorithm>  
using namespace std;  
bool cmp1(int a, int b)  //升序（对负数用）    
{  
	return a<b;  
}  
bool cmp2(int a, int b)  //降序（对正数用）   
{  
	return a>b;  
}  
int main()  
{  
	vector<int>zheng1,zheng2,fu1,fu2;  
	int n,m;  
	cin>>n;  
	for(int i = 0 ; i<n; i++){  
		int temp;  
		cin>>temp;  
		if(temp>0) zheng1.push_back(temp);   
		else if(temp<0) fu1.push_back(temp);   
	}  
	cin>>m;  
	for(int j = 0; j<m; j++){  
		int temp;  
		cin>>temp;  
		if(temp>0) zheng2.push_back(temp);  
		else if(temp<0) fu2.push_back(temp);   
	}  
	sort(zheng1.begin(),zheng1.end(),cmp2);  
	sort(zheng2.begin(),zheng2.end(),cmp2);  
	sort(fu1.begin(),fu1.end(),cmp1);  
	sort(fu2.begin(),fu2.end(),cmp1);  
	int size1,size2;  
	size1 = zheng1.size()<zheng2.size()? zheng1.size() : zheng2.size();  
	size2 = fu1.size()<fu2.size()? fu1.size() : fu2.size();   
	int count = 0;  
	for(int i = 0; i<size1; i++){  
		count += zheng1[i]*zheng2[i];  
	}  
	for(int j = 0; j<size2; j++){  
		count += fu1[j]*fu2[j];  
	}   
	cout<<count<<endl;  
	return 0;  
}  
*/   

/*  
1038  
**Recover the Smallest Number  给一系列数字，组一个最小数字**

***思路：字符串数组读入，去判断相同位数上的数字大小，排序***    

>include<iostream>  
using namespace std;  
int main()  
{
	int n;  
	cin>>n;  
	string s[n];  
	for(int i = 0; i<n; i++){  
		cin>>s[i];  
	}  
	//冒泡排序去交换 如何写交换条件就看本事了  
	for(int i = 0; i<n-1; i++){  
		for(int j = i+1; j<n; j++){  
			int k;  
			for(k = 0;k<(s[i].size()<s[j].size()?s[i].size():s[j].size());k++)  
			{  
				string temp;  
				if(s[i][k]<s[j][k]){  
					break;  
				}  
				else if(s[i][k]>s[j][k]){  
					temp = s[i];  
				    s[i] = s[j];  
				    s[j] = temp;  
				    break;  
				}	  
			}  
			if(k<(s[i].size()<s[j].size()?s[i].size():s[j].size())) continue;  
			else if(s[i][k] != '\0'){  
				if(s[i][k]>s[j][0]){  
					string temp;  
					temp = s[i];  
				    s[i] = s[j];  
				    s[j] = temp;  
				   // break;  
				}  
			}  
			else if(s[j][k] != '\0'){  
				if(s[j][k]<s[i][0]){  
					string temp;   
					temp = s[i];    
				    s[i] = s[j];  
				    s[j] = temp;  
				 //   break;  
				}  
			}   
		}  
	}  
	//第一个数去掉左起的零  
	int t;    
	for(int j = 0; j<s[0].size(); j++){  
		if(s[0][j] != '0'){  
			t = j;  
			break;  
		}  
	}     
	for(int j = t; j<s[0].size(); j++){  
		cout<<s[0][j];  
	}  
	for(int i = 1; i<n; i++){  
		cout<<s[i];  
	}  
	return 0;  
} 
	
***//大神思路：比较每两个相邻的元素，如果交换可以使得整个序列变大，就交换之，直到最后没有任何两个值之间能进行交换***  
***注释掉的地方是只考虑第一个字符串左起有零的情况，但是有一个测试点通不过，改为先整合为大字符串再判断左起零，包括全零输出零的情况，AC***
>#include<iostream>  
#include<algorithm>  
using namespace std;  
bool cmp(string &a,string &b)  //实现大的在前，用地址操作 改变顺序   
{  
	return a+b < b+a;  
}   
int main()  
{  
	int n;  
	cin>>n;  
	string s[n];  
	for(int i = 0; i<n; i++){  
		cin>>s[i];  
	}  
	sort(s,s+n,cmp);   
/*  
	//第一个数去掉左起的零  
	int t;    
	for(int j = 0; j<s[0].size(); j++){  
		if(s[0][j] != '0'){  
			t = j;  
			break;  
		}   
	}   
	for(int j = t; j<s[0].size(); j++){  
		cout<<s[0][j];  
	}
	for(int i = 1; i<n; i++){  
		cout<<s[i];  
	}  
*/    
    string out;  
    for(int i = 0; i<n; i++){  
    	out += s[i];  
	}  
	int j;    
	for( j = 0; j<out.size()&&out[j]=='0'; j++);  
	if(j==out.size())cout<<"0";  
	else printf("%s",out.c_str()+j);  
	return 0;  
}   
*/    

/*  
1041   
**Be Unique  渣渣题**     

***思路：一个数组按顺序存数，另一个数组利用下标存储出现次数***   
>#include<iostream>  
using namespace std;  
int main()  
{  
	int a[100001] = {0};  
	int b[100001]= {0};   
	int n;  
	cin>>n;  
	for(int i = 0 ; i<n; i++){  
		int temp;  
		cin>>temp;  
		a[temp]++;  
		b[i] = temp;   
	}  
	for(int i = 0 ; i<n; i++){  
		if(a[b[i]] == 1){  
			cout<<b[i];  
			return 0;  
		}  
	}  
	cout<<"None"<<endl;  
	return 0;  
}  
*/   

/*  
1042   
**Shuffling Machine**  
 
***思路：字符串数组存储，数字数组存储交换顺序***   
>#include<iostream>  
using namespace std;  
int main()  
{  
	string a[55] = {"0","S1","S2","S3","S4","S5","S6","S7","S8","S9","S10","S11","S12","S13","H1","H2","H3","H4","H5","H6","H7","H8","H9","H10","H11","H12","H13","C1","C2","C3","C4","C5","C6","C7","C8","C9","C10","C11","C12","C13","D1","D2","D3","D4","D5","D6","D7","D8","D9","D10","D11","D12","D13","J1","J2"};  
    string b[55] = {"0"};  
    int c[55] = {0};  
	int k;  
    cin>>k;  
    	for(int j = 1; j<55; j++){  
    		int temp;  
    		cin>>temp;  
    		c[j] = temp;  
    		b[temp] = a[j];  
		}  
		for(int j = 1; j<55; j++){  
    		a[j] = b[j];  
		}  	
    for(int i = 1; i<k; i++){  
    	for(int j = 1;j<55 ;j++){  
    		b[c[j]] = a[j];  
		}  
    	for(int j = 1; j<55; j++){  
    		a[j] = b[j];  
	    }  
	}  
	cout<<a[1];  
	for(int j = 2; j<55; j++){  
    		cout<<" "<<a[j];  
		}  
	return 0;  
}   
*/  

/*  
1044  有两个运行超时 count+min依然超时，神奇   
**Shopping in Mars 给定n个数和一个应该支付的数，在数列中连续几个刚好够支付或者最小差的支付方式输出**  

***思路：死循环 至flag位，强行遍历输出刚好总和为这个数的方案，若没有，总和+1继续遍历***     

>#include<iostream>  
using namespace std;  
int main()  
{  
	int n,count;  
	scanf("%d %d",&n,&count);  
//	cin>>n>>count;  
	int a[n+1] = {0};  
	for(int i = 1; i<=n; i++){  
		scanf("%d",&a[i]);  
//		cin>>a[i];  
	}  
	int flag = 0;  
	int min = 999;   
	while(1){  
	for(int j = 1; j<=n; j++){  
		int sum = 0;  
		for(int k = 0;k<=n-j;k++){  
			sum += a[j+k];   
			if(sum == count){    
				printf("%d-%d\n",j,j+k);  
//				cout<<j<<"-"<<j+k<<endl;  
				flag = 1;  
				break;  
			}  
			if(sum > count){  
				int temp = sum-count;  
				if(temp<min)  
				min = temp;  
				break;  
			}   
		}  
	}	  
	if(flag) return 0;  
	else count += min;  
	}  
	return 0;  
}   
*/   

/*  
1149   
**Dangerous Goods Packaging**   

>#include<iostream>  
#include<vector>  
#include<set>  
using namespace std;  
bool judge(vector<set<int> >v,int *a,int k)  
{  
	for(int i = 0; i<k-1; i++){  
		for(int j = i+1; j<k; j++){  
			if(i!=j && v[a[i]].find(a[j]) != v[a[i]].end())  
			return false;  
		}  
	}  
	return true;  
}  
int main()  
{  
	int m,n;   
  cin>>m>>n;  
	vector<set<int> >v(100010);  
	for(int i = 0; i<m; i++){   
		int a,b;  
		cin>>a>>b;  
		v[a].insert(b);  
		v[b].insert(a);  
	}  
	for(int j = 0; j<n; j++){  
		int k;  
	    cin>>k;  
	    int a[k];  
	    for(int i = 0; i<k; i++){  
	    	cin>>a[i];  
		}  
	    printf("%s\n",judge(v,a,k)? "Yes" : "No");  
	}  
	return 0;  
}  
*/  
	
/*
**1015 Reversible Primes 给一个整数，给一个进制，判断这个数和进制转换后的相反数(同一进制)是否都为素数，若是则输出Yes 否则输出No**

思路：进制转换，判断素数的结合   
 
>#include<iostream>  
#include<cmath>  
using namespace std;  
bool IsLeap(int n)  
{  
	if(n<2) return false;  
	for(int i = 2; i<= sqrt(n); i++){  
		if(n%i == 0)return false;  
	}  
	return true;  
}  
int main()  
{   
    int a[12] = {0};  
    int b[12] = {0};  
	while(1){  
	int count,m;  
	cin>>count;  
	int hh = count;  
	if(count<0){  
		return 0;  
	}  
	else cin>>m;  
	int k = 0;  
	while(count>0){  
		a[k] = count % m;  
		count = count / m;  
		k++;  
	}  
	int t = 0;  
	for(int j = k-1; j >= 0; j--){  
		b[t] = a[j];  
		t++;  
	}  
	int sum = 0;   
	for(int i = 0; i < k; i++){   
		sum += b[i]*pow(m,i);  
	}   
	if(IsLeap(hh) && IsLeap(sum)) cout<<"Yes"<<endl;  
	else cout<<"No"<<endl;  
	}  
}   
*/ 
			      
			      /*
**1027 Colors in Mars 十进制转13进制0-9,ABC，不足两位左起放0，开始有个"#"**   
   
>#include<iostream>  
using namespace std;  
int main()  
{  
	int k = 0;  
	for(int i = 0 ; i < 3; i++){  
	    char c[14] = {"0123456789ABC"};  
		int temp;  
		cin>>temp;  
		if(k == 0){  
			cout<<"#";  
			k++;  
		}  
		int high,low;  
		high = temp / 13;  
		low = temp % 13;  
        cout<<c[high]<<c[low];  
	}  
	return 0;  
}  
*/  

/*  
**1031 Hello World for U  给定一个字符串，输出为u型**   
>#include<iostream>  
#include<cstring>   
using namespace std;  
int main()  
{  
	string s;  
	cin>>s;  
	int len = s.size();  
	len = len +2;   
	int lie,hang;  
	hang = len / 3;  //总行数   
	lie = len - 2*hang; //总列数   
	for(int i = 0; i < hang-1; i++){  
		cout<<s[i];  
		for(int j = 0; j < lie-2; j++)cout<<" ";  
		cout<<s[s.size()-1-i]<<endl;  
	}  
	for(int i = hang-1;i<hang+lie-1;i++)cout<<s[i];   
	return 0;  
}  
*/      

/*  
**1035 Password  敏感字符替换**   

>#include<iostream>  
#include<cstring>  
#include<vector>  
using namespace std;  
struct node  
{  
	string id;  
	string password;  
};  
int main()  
{  
	int n;  
	cin>>n;  
	string id;  
	string password;  
	int sum = 0;   
	vector<node> v;  
	for(int i = 0 ;i < n; i++){  
		int flag = 0;  
		cin>>id>>password;  
		for(int i = 0 ; i < password.size(); i++){  
			if(password[i] == '1' || password[i] == '0' || password[i] == 'l' || password[i] == 'O'){  
				if(password[i] == '1') password[i] = '@';  
				else if(password[i] == '0') password[i] = '%';    
				else if(password[i] == 'l') password[i] = 'L';  
				else if(password[i] == 'O') password[i] = 'o';  
				flag = 1;  
			}  
		}  
		if(flag == 1){  
			sum++;  
			v.push_back(node{id,password});  
		}  
	}  
	if(sum == 0 && n ==1)printf("There is 1 account and no account is modified\n");  
	else if(sum == 0 && n>1)printf("There are %d accounts and no account is modified\n",n);  
	else{  
		cout<<v.size()<<endl;  
		for(int i = 0;i<v.size();i++){  
				cout<<v[i].id<<" "<<v[i].password<<endl;  
		}  
	}  
	return 0;  
}   
*/  

/*  
1148 Werewolf - Simple Version  

>#include<iostream>  
#include<cmath>  
using namespace std;  
int main()  
{  
	int n;  
	cin>>n;  
	int a[n+1];  
	for(int i = 1; i <= n; i++){  
		cin>>a[i];  
	}	  
	for(int i = 1 ; i < n ; i++){  
		for(int j = i+1 ; j <= n ; j++){  
			int b[n+1] = {0};  
			int count_lang = 0;  
			int count_pm = 0;  
			b[i] = 1;  
			b[j] = 1;  
			for(int k = 1 ; k <= n ; k++){  
				if(a[k]<0 && (b[abs(a[k])]!=1)){  
					if(k == i || k == j) count_lang++;  
					else count_pm++;  
				}  
				else if(a[k]>0 && (b[abs(a[k])]!=0)){  
					if(k == i || k == j) count_lang++;  
					else count_pm++;  
				}  
			}   
			if(count_lang == 1 &&count_pm == 1){  
				cout<<i<<" "<<j<<endl;  
				return 0;  
			}  
		}  
	}  
	cout<<"No Solution";  
	return 0;  
}   
*/	  
	

/*  
1144 The Missing Number   
 
>#include<iostream>  
#include<algorithm>  
using namespace std;  
int main()  
{  
	int n;  
	cin>>n;  
	int a[100010] = {0};  
	for(int i = 0 ; i < n ; i++){  
		int k;  
		cin>>k;  
		if(k>0 && k<100010)  
		a[k]++;  
	}  
	for(int i = 1 ; i < 100010 ; i++){  
		if(a[i] == 0){  
			cout<<i<<endl;  
			break;  
		}  
	}  
	return 0;  
}     
*/	  
	
	
