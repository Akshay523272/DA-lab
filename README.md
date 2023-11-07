# DAA-lab
#include<stdio.h>
#define INF 9999
#define n 4
void fldwarsh(int graph[][n])
{
    int matrix[4][4],i,j,k;
    for(i=0;i<n;i++)
        for(j=0;j<n;j++)
            matrix[i][j]=graph[i][j];
    
    for(k=0;k<n;k++){
        for(i=0;i<n;i++){
            for(j=0;j<n;j++)
            {
                if((matrix[i][k]+matrix[k][j])< matrix[i][j])
                    matrix[i][j]=matrix[i][k]+matrix[k][j];
            }
        }
    }
    printmatrix(matrix);
}
void printmatrix(int matrix[n][n])
{
    int i,j;
    for(i=0;i<n;i++)
    {
        for(j=0;j<n;j++)
        {
            if(matrix[i][j]==INF)
                printf("%s\t",INF);
            else
                printf("%d\t",matrix[i][j]);
        }
        printf(" \n");
    }
}

int main()
{
    int graph[n][n]={{0,3,INF,5},
 		{2,0,INF,4},
		{INF,1,0,INF},
		{INF,INF,2,0}};
    fldwarsh(graph);
}
