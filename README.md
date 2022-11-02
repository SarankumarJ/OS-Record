2.A) CPU Scheduling Algorithms Implementation of First Come First Serve Scheduling.

PROGRAM:-
~~~py
#include<stdio.h>
int main()
{
int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp;
float avg_wt,avg_tat;
printf("Enter number of process:");
scanf("%d",&n);
printf("\nEnter burst time:\n");
for(i=0;i<n;i++) {
printf("p%d:",i+1);
scanf("%d",&bt[i]);
p[i]=i+1;
}
wt[0]=0;
for(i=1;i<n;i++) {
wt[i]=0;
wt[i]+=bt[j];
for(j=0;j<i;j++)
total+=wt[i];
}
avg_wt=(float)total;
total=0;
printf("\nProcess \t Burst time \t Waiting time \t Turnaround Time");
for(i=0;i<n;i++) {
tat[i]=bt[i]+wt[i];
total+= tat[i];
printf("\np%d \t\t\t %d \t\t\t\t %d \t\t\t\t\t %d",p[i],bt[i],wt[i],tat[i]);
}
avg_tat = (float)total;
printf("\n\nAverage waiting time =%f",avg_wt);
printf("\nAverage Turnaround time= %f \n",avg_tat);

}
~~~
2.B) CPU Scheduling Algorithms Implementation of Shortest Job First

PROGRAM:-
~~~py
#include <stdio.h>
int main()
{
    int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp;
    float avg_wt,avg_tat;
    printf("Enter number of process:");
    scanf("%d",&n);
    printf("\n Enter Burst Time:\n");
    for (i=0;i<n;i++)
    {
        printf("P%d:",i+1);
        scanf("%d",&bt[i]);
        p[i]=i+1;
    }
    for(i=0;i<n;i++)
    {
        pos=i;
        for(j=i+1;j<n;j++)
        {
            if(bt[j]<bt[pos])
            pos=j;
        }
        temp=bt[i];
        bt[i]=bt[pos];
        bt[pos]=temp;
        temp=p[i];
        p[i]=p[pos];
        p[pos]=temp;
    }
    wt[0]=0;
    for(i=1;i<n;i++)
    {
        wt[i]=20;
        for(j=0;j<i;j++)
        wt[i]+=bt[j];
        avg_wt=(float)total/n;
        total=0;
    }
        printf("\n Process\t Burst Time\t Waiting Time\t Turnaround Time");
   
    for(i=0;i<n;i++)
    {
        tat[i]=bt[i]+wt[i];
        total+=tat[i];
        printf("\n P%d \t\t %d \t\t\t %d \t\t\t\t %d",p[i],bt[i],wt[i],tat[i]);
        
    }
    avg_tat=(float)total;
    printf("\n\n Average Waiting Time =%f",avg_wt);
    printf("\n Average Turnaround Time = %f\n",avg_tat);
}
~~~
2.C) CPU Scheduling Algorithms Implementation of Priority Scheduling

PROGRAM:-
~~~py
#include <stdio.h>
int main()
{
    int bt[20],p[20],wt[20],tat[20],pri[20],i,j,k,r,n,total=0,pos,temp;
    float avg_wt,avg_tat;
    printf("Enter number of process:");
    scanf("%d",&n);
    printf("\n Enter Burst Time:\n");
    for (i=0;i<n;i++)
    {
        printf("P%d:",i+1);
        scanf("%d",&bt[i]);
        p[i]=i+1;
    }
        printf("Enter Priority of the Process");
    
    for(i=0;i<n;i++)
    {
        p[i]=i;
        printf("\nP%d:",i+1);
        scanf("%d",&pri[i]);
    }
        for(i=0;i<n;i++)
          for(k=i+1;k<n;k++)
          if(pri[i]>pri[k])
          {
        
        temp=pri[i];
        pri[i]=pri[k];
        pri[k]=temp;
    }
    wt[0]=0;
    for(i=1;i<n;i++)
    {
        wt[i]=0;
        for(j=0;i<i;j++)
        wt[i]+=bt[j];
        total+=wt[i];
    }
        avg_wt=(float)total;
        total=0;
        printf("\n Process\t Burst Time\t Priority Time\t Waiting Time\t Turnaround Time");
    
    for(i=0;i<n;i++)
    {
        tat[i]=bt[i]+wt[i];
        total+=tat[i];
        printf("\n P%d \t\t %d \t\t\t %d \t\t\t\t %d \t\t\t %d",p[i],bt[i],pri[i],wt[i],tat[i]);
        
    }
    avg_tat=(float)total;
    printf("\n\n Average Waiting Time =%f",avg_wt);
    printf("\n Average Turnaround Time = %f\n",avg_tat);

}

~~~
2.D) CPU Scheduling Algorithms Implementations of Round Robin Scheduling

PROGRAM:-
~~~py
    #include<stdio.h>  
    #include<conio.h>  
      
    void main()  
    {  
   
        int i, NOP, sum=0,count=0, y, quant, wt=0, tat=0, at[10], bt[10], temp[10];  
        float avg_wt, avg_tat;  
        printf(" Enter number of process: ");  
        scanf("%d", &NOP);  
        y = NOP; 
   
    for(i=0; i<NOP; i++)  
    {  
    printf("\n P[%d]\n", i+1);  
    printf(" Arrival time: \t"); 
    scanf("%d", &at[i]);  
    printf(" \nBurst time: \t"); 
    scanf("%d", &bt[i]);  
    temp[i] = bt[i];  
    }  

    printf("Enter the Time Quantum: \t");  
    scanf("%d", &quant);  
 
    printf("\n Process No \t\t Burst Time \t\t\t TAT \t\t\t Waiting Time ");  
    for(sum=0, i = 0; y!=0; )  
    {  
    if(temp[i] <= quant && temp[i] > 0) 
    {  
        sum = sum + temp[i];  
        temp[i] = 0;  
        count=1;  
        }     
        else if(temp[i] > 0)  
        {  
            temp[i] = temp[i] - quant;  
            sum = sum + quant;    
        }  
        if(temp[i]==0 && count==1)  
        {  
            y--; 
            printf("\nProcess No[%d] \t\t %d\t\t\t\t %d\t\t\t %d", i+1, bt[i], sum-at[i], sum-at[i]-bt[i]);  
            wt = wt+sum-at[i]-bt[i];  
            tat = tat+sum-at[i];  
            count =0;     
        }  
        if(i==NOP-1)  
        {  
            i=0;  
        }  
        else if(at[i+1]<=sum)  
        {  
            i++;  
        }  
        else  
        {  
            i=0;  

        }  
    }  
  
    avg_wt = wt * 1.0/NOP;  
    avg_tat = tat * 1.0/NOP;  
    printf("\nAverage Turn Around Time: %f", avg_wt);  
    printf("\nAverage Waiting Time: %f", avg_tat);  
    getch();  
    }  
~~~
4 A)PAGING TECHNIQUE OF MEMORY MANAGEMENT

PROGRAM:-
~~~py
#include<stdio.h>
int main()
{
int ms, ps, nop, np, rempages, i, j, x, y, pa, offset;
int s[10], fno[10][20];
printf("\nEnter the memory size -- ");
scanf("%d",&ms);
printf("\nEnter the page size -- ");
scanf("%d",&ps);nop = ms/ps;
printf("\nThe no. of pages available in memory are -- %d ",nop);
printf("\nEnter number of processes -- ");
scanf("%d",&np);
rempages = nop;
for(i=1;i<=np;i++)
{
printf("\nEnter no. of pages required for p[%d]-- ",i);
scanf("%d",&s[i]);
if(s[i] >rempages)
{
printf("\nMemory is Full");
break;
}
rempages = rempages - s[i];
printf("\nEnter pagetable for p[%d] --- ",i);
for(j=0;j<s[i];j++)
scanf("%d",&fno[i][j]);
}
printf("\nEnter Logical Address to find Physical Address ");
printf("\nEnter process no. and page number and offset -- ");
scanf("%d %d %d",&x,&y, &offset);
if(x>np || y>=s[i] || offset>=ps)
printf("\nInvalid Process or Page Number or offset");
else
{ pa=fno[x][y]*ps+offset;
printf("\nThe Physical Address is -- %d",pa);
}

}
~~~

4 B)PAGE REPLACEMENT ALGORITHM (FIFO)

PROGRAM:-
~~~py
#include<stdio.h>
int main()
{
int i,j,n,a[50],frame[10],no,k,avail,count=0;
printf("\n ENTER THE NUMBER OF PAGES:\n");
scanf("%d",&n);
printf("\n ENTER THE PAGE NUMBER :\n");
for(i=1;i<=n;i++)
scanf("%d",&a[i]);
printf("\n ENTER THE NUMBER OF FRAMES :");
scanf("%d",&no);
for(i=0;i<no;i++)
frame[i]= -1;
j=0;
printf("\tRef string\t Page Frames\n");
for(i=1;i<=n;i++)
{
printf("%d\t\t\t",a[i]);
avail=0;
for(k=0;k<no;k++)
if(frame[k]==a[i])
avail=1;
if (avail==0)
{
frame[j]=a[i];
j=(j+1)%no;
count++;
for(k=0;k<no;k++)
printf("%d\t",frame[k]);
}
printf("\n");
}
printf("\nPage Fault Is %d",count);
return 0;
}
~~~

4 C)PAGE REPLACEMENT ALGORITHM (LRU)

PROGRAM:-
~~~py
#include<stdio.h>
main()
{
int q[20],p[50],c=0,c1,d,f,i,j,k=0,n,r,t,b[20],c2[20];
printf("Enter no of pages: \n");
scanf("%d",&n);
printf("Enter the reference string: \n");
for(i=0;i<n;i++)
scanf("%d",&p[i]);
printf("Enter no of frames: \n");
scanf("%d",&f);
q[k]=p[k];
printf("\t\n\t %d\n",q[k]);
c++;
k++;
for(i=1;i<n;i++)
{
c1=0;
for(j=0;j<f;j++)
{
if(p[i]!=q[j])
c1++;
}
if(c1==f){
c++;
if(k<f)
{
q[k]=p[i];
k++;
for(j=0;j<k;j++)
printf("\t%d",q[j]);
printf("\n");
}
else
{
for(r=0;r<f;r++)
{
c2[r]=0;
for(j=i-1;j<n;j--)
{
if(q[r]!=p[j])
c2[r]++;
else
break;
}
}
for(r=0;r<f;r++)
b[r]=c2[r];
for(r=0;r<f;r++)
{
for(j=r;j<f;j++)
{
if(b[r]<b[j])
{
t=b[r];
b[r]=b[j];
b[j]=t;
}
}
}
for(r=0;r<f;r++)
{
if(c2[r]==b[0])
q[r]=p[i];
printf("\t%d",q[r]);
}
printf("\n");
}
}
}
printf("\nThe no of page faults is %d",c);
}
~~~

4 D)PAGE REPLACEMENT ALGORITHM (OPR)

PROGRAM:-
~~~py
#include<stdio.h>
int main()
{
int i,j,n,a[50],frame[10],no,k,avail,count=0;
printf("\n ENTER THE NUMBER OF PAGES:\n");
scanf("%d",&n);
printf("\n ENTER THE PAGE NUMBER :\n");
for(i=1;i<=n;i++)
scanf("%d",&a[i]);
printf("\n ENTER THE NUMBER OF FRAMES :");
scanf("%d",&no);
for(i=0;i<no;i++)
frame[i]= -1;
j=0;
printf("\tref string\t page frames\n");
for(i=1;i<=n;i++)
{
printf("%d\t\t",a[i]);
avail=0;
for(k=0;k<no;k++)
if(frame[k]==a[i])
avail=1;
if (avail==0)
{
frame[j]=a[i];
j=(j+1)%no;
count++;
for(k=0;k<no;k++)
printf("%d\t",frame[k]);
}
printf("\n");
}
printf("Page Fault Is %d",count);
return 0;
}
~~~
