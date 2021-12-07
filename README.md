# Clone-FlipKart
package com.company;
import java.util.*;
import java.io.*;
public class Main {

    public static void main(String[] args) {
        // write your code here
        Scanner sc = new Scanner(System.in);
        //int t=sc.nextInt();
        //int c=1;
        /*while(t-->0){
            int n=sc.nextInt();
            int p=sc.nextInt();
            int arr[]=new int[n];
            for(int i=0;i<n;i++)
                arr[i]=sc.nextInt();
            Arrays.sort(arr);
            int prefix[]=new int[n+1];
            for(int i=0;i<n;i++)
                prefix[i+1]=prefix[i]+arr[i];
            long result=Long.MAX_VALUE;
            for(int i=p-1;i<n;i++){
                long sum=prefix[i]-prefix[i-(p-1)];
                long fl=arr[i]*(p-1)-sum;
                result=Math.min(fl,result);
            }
            System.out.println("Case #"+c+": "+result);
            c++;
        }*/

        /*for(int i=0;i<n;i++)
            if(max<arr[i])
                max=arr[i];
        //findthewindow(arr,arr.length-1,max);
        int sum=0,temp=0;
        for(int i=1;i<12;i++){
            sum+=i;
            if(sum>=12) {
                temp = i;
                break;
            }

        }
        System.out.print(temp);
        //selectionsort(arr,arr.length);
        //insertionsort(arr,arr.length);

        //quicksort(arr,0,arr.length-1);

        //countsort(arr,arr.length,max);
        //System.out.println(max);
        //for(int i=0;i< arr.length;i++)
          //  System.out.println(arr[i]);*/
        //int n=sc.nextInt();
        /*int arnab[]=new int[n];
        int dj[]=new int[n];
        for(int i=0;i<n;i++)
            arnab[i]=sc.nextInt();
        for(int i=0;i<n;i++)
            dj[i]=sc.nextInt();
        Arrays.sort(arnab);
        Arrays.sort(dj);
        int win=0;
        int c1=0,c2=0;
        for(int i=0;i<n;i++){
            if(arnab[c1]>dj[c2]){
                c1++;
                c2++;
                win++;
            }
            else
                c1++;

        }
        System.out.println(win);*/
        /*for(int i=1;i<n+1;i++){
            if(arr[i]!=i)
                sum+=Math.abs(arr[i]-i);
        }*/
        //System.out.println(sortfun(arr,0,n));
        /*int start=0;
        int end=n;
        if(sorted(arr,0,end)==true)
            System.out.println(n-start);
        else
            System.out.println(uniqsort(arr,start,end-1));*/
        /*int t=sc.nextInt();
        while(t-->0){
            int n=sc.nextInt();
            String name1[]=new String[n];
            String name0[]=new String[n];
            int no1[]=new int[n];
            int no2[]=new int[n];
            for(int i=0;i<n;i++){
                String nn=sc.next();
                int p=sc.nextInt();
                int c=sc.nextInt();
                if(c==1){
                    name1[i]=nn;
                    no1[i]=p+c;
                }
                else{
                    name0[i]=nn;
                    no2[i]=p+c;
                }
            }
            sorted(name1,no1,n);
            sorted(name0,no2,n);
            for(int i=0;i<n;i++){
                if(name1[i]!=null)
                    System.out.println(name1[i]);
            }
            for(int i=0;i<n;i++){
                if(name0[i]!=null)
                    System.out.println(name0[i]);
            }
        } */
        int arr[]={20,40,30,50,70};
        Arrays.sort(arr);
        triplet(arr,arr.length);

    }
    static void triplet(int[] arr,int n){
        Hashtable<Integer,Integer> t1=new Hashtable<>();
        for(int i=0;i<n;i++){
            t1.put(arr[i],1);
        }
        int flag=0;
        for(int i=n-1;i>=0;i--){
            for(int j=0;j<n;j++){
                if(t1.get(arr[i]-arr[j])!=null && arr[i]-arr[j]>=0 && arr[i]-arr[j]!=arr[j]) {
                    System.out.print(arr[i]+" "+ arr[j]+" "+(arr[i]-arr[j]));
                    flag=1;
                    break;
                }
            }
            if(flag==1)
                break;
        }
        if(flag==0)
            System.out.print(-1);
    }
    static void sorted(String name1[],int arr[],int n ) {
        for (int i = 0; i < n; i++) {
            for (int j = i; j < n; j++) {
                if (arr[i] < arr[j]) {
                    int temp = arr[i];
                    arr[i] = arr[j];
                    arr[j] = temp;
                    String ntemp = name1[i];
                    name1[i] = name1[j];
                    name1[j] = ntemp;
                }
            }
        }
    }

        static int uniqsort(int[] arr,int start,int end){
        int mid=start+(end-start)/2;
        if(sorted(arr,start,mid+1)==true)
            return mid-start+1;
        if(sorted(arr,mid+1,end+1)==true)
            return end-mid;
        int c1=uniqsort(arr,start,mid);
        int c2=uniqsort(arr,mid+1,end);
        if(c1>=c2)
            return c1;
        return c2;
    }
    static boolean sorted(int[] arr,int start,int high){
        boolean flag=true;
        for(int i=start+1;i<high;i++){
            if(arr[i]<arr[i-1]){
                flag=false;
                break;
            }
        }
        return flag;
    }
    static int sortfun(int[] arr,int low,int high){
        if(low+1==high)
            return 1;
        int mid=(low+high)/2;
        int h1=sortfun(arr,low,mid);
        int h2=sortfun(arr,mid,high);
        if(h1==h2 && h1==(high-low)/2 && arr[mid-1]<=arr[mid])
            return high-low;
        if(h1>h2)
            return h1;
        else
            return h2;
    }
    static void roboprep(int[] arr,int n){
        int t=0;
        while (n>0){
            int rem=n%10;
            arr[t++]=rem;
            n/=10;
        }
        Arrays.sort(arr,0,t);
        int flag=0;
        for(int i=0;i<t-1;i++){
            if((arr[i]+1)!=arr[i+1]){
                flag=1;
                break;
            }
        }
        if(flag==0)
            System.out.print("YES");
        else
            System.out.print("NO");
    }
    static void findthewindow(int[] arr,int n){
        int low=0,high=0;
        for(low=0;low<n-1;low++){
            if(arr[low]>arr[low+1])
                break;
        }
        for(high=n-1;high>0;high--)
            if(arr[high]<arr[high-1])
                break;
        int min=Integer.MAX_VALUE,max=Integer.MIN_VALUE;
        for(int i=0;i<n;i++){
            if(arr[i]>max)
                max=arr[i];
            if(arr[i]<min)
                min=arr[i];
        }
        for(int i=0;i<low;i++){
            if(arr[i]>min)
                low=i;
        }
        for(int i=high;i>n;i--){
            if(arr[i]<max)
                high=i;
        }
        System.out.print(low+" "+high);
    }
    static int noofhours(int[]arr,int p,int n){
        int prefix[]=new int[n];
        prefix[0]=arr[0];
        for(int i=1;i<n;i++)
            prefix[i]=prefix[i-1]+arr[i];
        if(p==n)
            p=p-1;
        int h=Integer.MAX_VALUE;
        int v=0;
        for(int i=0;i<n;i++){
            int sum=0;
            if((i-p+1)>0){
                sum+=arr[i]*p- prefix[i-1]-v;
                System.out.print(sum+" ");
                v=arr[i-p+1];
                h=Math.min(sum,h);
            }
        }
        return h;
    }
    static void countsort(int[]arr,int n,int max){
        int count[]=new int[max+1];
        int r1[]=new int[n];
        for(int i=0;i<n;i++)
            count[arr[i]]++;
        for(int i=1;i< count.length;i++)
            count[i]+=count[i-1];
        for(int i=n-1;i>=0;i--){
            int temp=count[arr[i]]-1;
            r1[temp]=arr[i];
            count[arr[i]]-=1;
        }
        for(int i=0;i<n;i++)
            System.out.print(r1[i]+"  ");

    }
    static void quicksort(int arr[],int low,int high){
        if(low>=high)
            return;
        int pivot=quick(arr,low,high);
        quicksort(arr,low,pivot-1);
        quicksort(arr,pivot+1,high);
    }
    static int quick(int[] arr,int low,int high){
        int pivot=arr[high];
        int i=low-1,temp;
        for(int j=low;j<=high-1;j++){
            if(arr[j]<=pivot){
                i++;
                temp=arr[i];
                arr[i]=arr[j];
                arr[j]=temp;
            }
        }
        temp=arr[i+1];
        arr[i+1]=arr[high];
        arr[high]=temp;
        return i+1;
    }
    static void mergesort(int[]arr,int low,int high){
        if(low>=high)
            return;
        int mid=low+(high-low)/2;
        mergesort(arr,low,mid);
        mergesort(arr,mid+1,high);
        merge(arr,low,mid,high);
    }
    static void merge(int[] arr,int low,int mid,int high){
        int n1=mid-low+1,n2=high-mid;
        int[] l1=new int[n1];
        int r1[]=new int[n2];
        for(int i=0;i<n1;i++)
            l1[i]=arr[low+i];
        for(int i=0;i<n2;i++)
            r1[i]=arr[mid+i+1];
        int i=0,j=0,k=low;
        while(i<n1 && j<n2) {
            if (l1[i] < r1[j])
                arr[k++] = l1[i++];
            else
                arr[k++] = r1[j++];
        }
            while(i<n1)
                arr[k++]=l1[i++];
            while(j<n2)
                arr[k++]=r1[j++];

    }
    static void insertionsort(int[]arr,int n){

        for(int i=1;i<n;++i){
            int var=arr[i];
            int j=i-1;
            while(j>=0 && arr[j]>var)  {
                arr[j+1] = arr[j];
                j=j-1;
            }
            arr[j+1]=var;
        }
    }
    static void selectionsort(int[] arr,int n){
        for(int i=0;i<n;i++){
            int min=i;
            for(int j=i;j<n;j++){
                if(arr[j]<arr[min]){
                    int temp=arr[min];
                    arr[min]=arr[j];
                    arr[j]=temp;
                }
            }
        }
    }
}
