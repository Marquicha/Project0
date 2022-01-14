#include <stdio.h>
#include <dirent.h>
#include <stdlib.h>


int main(int argc, char *argv[]) {
    struct dirent **namelist;
    int n;
    {

        n=scandir(argv[1],&namelist,NULL,alphasort);
        if (n == -1) {
            printf("tuls: cannot open directory");
            //perror("scandir");
            //exit(EXIT_FAILURE);
            return 1;
        }
    }

    //struct dirent *name[99];
    //printf("argc = %d\n",argc);

    n=scandir(argv[1],&namelist,NULL,alphasort);
    //printf("Number Files %d\n", n);

    if (n == -1) {
        printf("tuls: cannot open directory");
        //perror("scandir");
        //exit(EXIT_FAILURE);
        return 1;
    }
    printf("Number Files %d\n", n);
    while (n--)
    {
        printf("%s\n",namelist[n]->d_name);
        free(namelist[n]);
    }
    return 0;
}
