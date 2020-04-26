#include <iostream>
#include <string>
using namespace std;
string S[5]= {"keyword","identifier","integer","boundary","operator"};
string T[6]= {"main","if","else","for","while","int"};
void panduan(string s)
{
    if(s[0]>='0'&&s[0]<='9')
    {
        cout<<"("<<S[2]<<","<<s<<")"<<endl;
    }
    else
    {
        int f=1;
        for(int i=0; i<6; i++)
        {
            if(s==T[i])
            {
                f=0;
                cout<<"("<<S[0]<<","<<s<<")"<<endl;
                break;
            }
        }
        if(f==1)
        {
            cout<<"("<<S[1]<<","<<s<<")"<<endl;
        }
    }

}
int main()
{

    string s;
    while(cin>>s)
    {
        int len=s.length();
        string temp="";
        for(int i=0; i<len; i++)
        {
            if(s[i] == '=' || s[i] == '+' || s[i] == '-'||s[i] == '*'|| s[i] == '/' || s[i] == '<' || s[i] == '>' || s[i] == '!')
            {
                if(temp.length())
                {
                    panduan(temp);
                }
                temp="";
                if(i+1<len&&s[i+1]=='=')
                {
                    cout<<"("<<S[4]<<","<<s[i]<<s[i+1]<<")"<<endl;
                    i++;
                }
                else
                {
                    cout<<"("<<S[4]<<","<<s[i]<<")"<<endl;
                }
            }
            else if(s[i] == '(' || s[i] == ')' || s[i] == '{'||s[i] == '}'|| s[i] == ',' || s[i] ==';')
            {
                if(temp.length())
                {
                    panduan(temp);
                }
                temp="";
                cout<<"("<<S[3]<<","<<s[i]<<")"<<endl;
            }
            else
            {
                temp=temp+s[i];

            }
        }
        if(temp.length())
        {
            panduan(temp);
        }

    }
    return 0;}
