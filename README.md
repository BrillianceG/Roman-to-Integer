# Roman-to-Integer
Roman to Integer
int map[26];

memset(map, 0, 26);

map['I'-65]=1;
map['V'-65]=5;
map['X'-65]=10;
map['L'-65]=50;
map['C'-65]=100;
map['D'-65]=500;
map['M'-65]=1000;

int len=strlen(s), i, sum=0, prev, cur=map[s[0]-65];

for(i=1; i<len; i++)
{
    prev=map[s[i-1]-65];
    cur=map[s[i]-65];

    if(prev>=cur)
    {
        sum+=prev;
    }
    else
    {
        sum+=cur-prev;
        if(i==(len-1))
            cur=0;/*to avoid adding up last Roman Number in case of for e.g XIV. We would have already added 10+4. We needn't add 5 again in return sum+cur. Thus making cur=0*/
        else
            cur=map[s[i+1]-65];/*In case we have XCV, and cur='C'. We have already added 90. we would want cur to be 'V' after for loop ends. else cur will retain 'C'. Then we would return 90+100 instead of 90+5*/
        i++;
    }

}
if(sum==0)
return cur;
else
return sum+cur;/*to add the last Roman Number*/
