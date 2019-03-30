# qqques4.lpu
 Design a scheduling program to implements a Queue with two levels: Level 1 : Fixed priority preemptive Scheduling Level 2 : Round Robin Scheduling For a Fixed priority preemptive Scheduling (Queue 1), the Priority 0 is highest priority. If one process P1 is scheduled and running, another process P2 with higher priority comes. The New process (high priority) process P2 preempts currently running process P1 and process P1 will go to second level queue. Time for which process will strictly execute must be considered in the multiples of 2. All the processes in second level queue will complete their execution according to round robin scheduling. Consider: 1. Queue 2 will be processed after Queue 1 becomes empty. 2. Priority of Queue 2 has lower priority than in Queue 1.


#include<unistd.h>
#include<stdio.h>
void main()
{
int n,bur[100],arr[100],pro[100],timequant,flag=0,i,k,temp[100],total=0;
printf("enter the no. of processes:");
scanf("%d",&n);
for(i=0;i<n;i++)
{
printf("enter burst time of process%d:",i+1);
scanf("%d",&bur[i]);               
pro[i]=0;               

}
printf("enter the time quantum:");
scanf("%d",&timequant);
i=0;k=0;
while(1)
{
if(i==n)                
i=0;
if(flag==n)             
break;


if(bur[i]<=timequant && bur[i]>0)
{
//w[i]+=total-p[i];
flag++;                      

total+=bur[i];    
bur[i]=0;
temp[k]=i;
k++;

}
if(bur[i]>timequant)
{
//w[i]+=total-p[i];
bur[i]=bur[i]-timequant;
total+=timequant;
temp[k]=i;
k++;
}
pro[i]=total;
i++;
}
printf("order of execution:\n");
for(i=0;i<k;i++)
{
printf("P%d ",temp[i]);
}

}


