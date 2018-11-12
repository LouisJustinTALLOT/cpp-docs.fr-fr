---
title: _pipe
ms.date: 11/04/2016
apiname:
- _pipe
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- pipe
- _pipe
helpviewer_keywords:
- pipes, creating
- _pipe function
- pipes
- pipe function
ms.assetid: 8d3e9800-4041-44b5-9e93-2df0b0354a75
ms.openlocfilehash: c5db59fecd84ae291e5651b1cec1be31c815e53a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453979"
---
# <a name="pipe"></a>_pipe

Crée un canal pour la lecture et l’écriture.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _pipe(
   int *pfds,
   unsigned int psize,
   int textmode
);
```

### <a name="parameters"></a>Paramètres

*CF*<br/>
Pointeur vers un tableau de deux **int** à conserver et à écrire des descripteurs de fichier.

*psize*<br/>
Quantité de mémoire à réserver.

*TextMode*<br/>
Mode de Fichier.

## <a name="return-value"></a>Valeur de retour

Retourne 0 en cas de réussite. Retourne -1 pour indiquer une erreur. En cas d’erreur, **errno** est défini sur une des valeurs suivantes :

- **EMFILE**, ce qui indique que plus aucun descripteur de fichier n’est disponibles.

- **/ENFILE**, ce qui indique un dépassement de capacité de table de fichiers système.

- **EINVAL**, ce qui indique que soit le tableau *CF* est un pointeur null ou qu’une valeur non valide pour *textmode* a été passé.

Pour plus d’informations sur ces codes de retour et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_pipe** fonction crée un *canal*, qui est un canal d’e/s artificiel qu’un programme utilise pour passer des informations à d’autres programmes. Un canal s’apparente à un fichier en ce sens qu’il dispose d’un pointeur de fichier, d’un descripteur de fichier ou les deux, et peut être lu ou écrit à l’aide des fonctions d’entrée et de sortie de la bibliothèque standard. Cependant, un canal ne représente pas un fichier ou un appareil déterminé. En effet, il représente un stockage temporaire en mémoire qui est indépendant de la mémoire propre au programme et qui est contrôlé entièrement par le système d’exploitation.

**_pipe** ressemble à **_open** mais ouvre le canal pour lire et écrire et retourne deux descripteurs plutôt qu’un seul de fichier. Le programme peut utiliser les deux côtés du canal ou fermer celui dont il n’a pas besoin. Par exemple, le processeur de commandes dans Windows crée un canal lorsqu’il exécute une commande comme **PROGRAM1** | **PROGRAM2**.

Descripteur de sortie de la norme **PROGRAM1** est rattaché au descripteur d’écriture du canal. Le descripteur d’entrée standard de **PROGRAM2** est rattaché au descripteur de lecture du canal. De ce fait, il n’est plus nécessaire de créer des fichiers temporaires pour transmettre des informations à d’autres programmes.

Le **_pipe** fonction retourne deux descripteurs de fichier pour le canal dans le *CF* argument. L’élément *CF*[0] contient le descripteur de lecture et l’élément *CF*[1] contient le descripteur d’écriture. Les descripteurs de fichier de canal sont utilisés de la même façon que les autres descripteurs de fichier. (L’entrée de bas niveau et les fonctions de sortie **_read** et **_write** peut lire et écrire dans un canal.) Pour détecter la condition de fin de canal, recherchez un **_read** demande qui retourne 0 en tant que le nombre d’octets lus.

Le *psize* argument spécifie la quantité de mémoire, en octets, à réserver pour le canal. Le *textmode* argument spécifie le mode de traduction pour le canal. La constante de manifeste **_O_TEXT** spécifie une traduction de texte et la constante **_O_BINARY** spécifie une traduction binaire. (Pour obtenir une description des modes texte et binaire, consultez [fopen, _wfopen](fopen-wfopen.md).) Si le *textmode* argument est 0, **_pipe** utilise le mode de traduction par défaut qui est spécifié par la variable de mode par défaut [_fmode](../../c-runtime-library/fmode.md).

Dans les programmes multithread, aucun verrouillage n’est effectué. Les descripteurs de fichier retournés sont ouverts et ne doivent pas être référencés par aucun thread tant que le **_pipe** appel est terminé.

Pour utiliser le **_pipe** de fonction pour communiquer entre un processus parent et un processus enfant, chaque processus doit avoir qu’un seul descripteur ouvert sur le canal. Les descripteurs doivent être contraires : si le parent a un descripteur de lecture ouvert, l’enfant doit avoir un descripteur d’écriture ouvert. Le plus simple pour ce faire consiste au niveau du bit ou (**|**) le **_O_NOINHERIT** indicateur avec *textmode*. Ensuite, utilisez **_dup** ou **_dup2** pour créer une copie pouvant être héritée du descripteur de canal que vous souhaitez passer à l’enfant. Fermez le descripteur d’origine, puis générez le processus enfant. Une fois le retour de l’appel de génération obtenu, fermez le descripteur en double dans le processus parent. Pour plus d’informations, consultez l’exemple 2 plus loin dans ce même article.

Dans le système d’exploitation Windows, un canal est détruit dès lors que tous ses descripteurs sont fermés. (Si tous les descripteurs de lecture du canal ont été fermés, toute opération d’écriture dans le canal entraîne une erreur.) Toutes les opérations de lecture et d’écriture au niveau du canal restent en attente tant qu’il n’y a pas suffisamment de données ou d’espace de mémoire tampon pour faire aboutir la demande d’E/S.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_pipe**|\<io.h>|\<fcntl.h>,1 \<errno.h>2|

1 pour **_O_BINARY** et **_O_TEXT** définitions.

2 **errno** définitions.

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example-1"></a>Exemple 1

```C
// crt_pipe.c
/* This program uses the _pipe function to pass streams of
* text to spawned processes.
*/

#include <stdlib.h>
#include <stdio.h>
#include <io.h>
#include <fcntl.h>
#include <process.h>
#include <math.h>

enum PIPES { READ, WRITE }; /* Constants 0 and 1 for READ and WRITE */
#define NUMPROBLEM 8

int main( int argc, char *argv[] )
{

   int fdpipe[2];
   char hstr[20];
   int pid, problem, c;
   int termstat;

   /* If no arguments, this is the spawning process */
   if( argc == 1 )
   {

      setvbuf( stdout, NULL, _IONBF, 0 );

      /* Open a set of pipes */
      if( _pipe( fdpipe, 256, O_BINARY ) == -1 )
          exit( 1 );

      /* Convert pipe read descriptor to string and pass as argument
       * to spawned program. Program spawns itself (argv[0]).
       */
      _itoa_s( fdpipe[READ], hstr, sizeof(hstr), 10 );
      if( ( pid = _spawnl( P_NOWAIT, argv[0], argv[0],
            hstr, NULL ) ) == -1 )
          printf( "Spawn failed" );

      /* Put problem in write pipe. Since spawned program is
       * running simultaneously, first solutions may be done
       * before last problem is given.
       */
      for( problem = 1000; problem <= NUMPROBLEM * 1000; problem += 1000)
      {

         printf( "Son, what is the square root of %d?\n", problem );
         _write( fdpipe[WRITE], (char *)&problem, sizeof( int ) );

      }

      /* Wait until spawned program is done processing. */
      _cwait( &termstat, pid, WAIT_CHILD );
      if( termstat & 0x0 )
         printf( "Child failed\n" );

      _close( fdpipe[READ] );
      _close( fdpipe[WRITE] );

   }

   /* If there is an argument, this must be the spawned process. */
   else
   {

      /* Convert passed string descriptor to integer descriptor. */
      fdpipe[READ] = atoi( argv[1] );

      /* Read problem from pipe and calculate solution. */
      for( c = 0; c < NUMPROBLEM; c++ )
      {

        _read( fdpipe[READ], (char *)&problem, sizeof( int ) );
        printf( "Dad, the square root of %d is %3.2f.\n",
                 problem, sqrt( ( double )problem ) );

      }
   }
}
```

```Output
Son, what is the square root of 1000?
Son, what is the square root of 2000?
Son, what iDad, the square root of 1000 is 31.62.
Dad, the square root of 2000 is 44.72.
s the square root of 3000?
Dad, the square root of 3000 is 54.77.
Son, what is the square root of 4000?
Dad, the square root of 4000 is 63.25.
Son, what is the square root of 5000?
Dad, the square root of 5000 is 70.71.
Son, what is the square root of 6000?
SonDad, the square root of 6000 is 77.46.
, what is the square root of 7000?
Dad, the square root of 7000 is 83.67.
Son, what is the square root of 8000?
Dad, the square root of 8000 is 89.44.
```

## <a name="example-2"></a>Exemple 2

Cet exemple porte sur une application de filtre rudimentaire. Il génère l’application crt_pipe_beeper après avoir créé un canal qui dirige la sortie stdout de l’application générée vers le filtre. Le filtre supprime les caractères ASCII 7 (beep).

```C
// crt_pipe_beeper.c

#include <stdio.h>
#include <string.h>

int main()
{
   int   i;
   for(i=0;i<10;++i)
      {
         printf("This is speaker beep number %d...\n\7", i+1);
      }
   return 0;
}
```

Voici l’application de filtre effective :

```C
// crt_pipe_BeepFilter.C
// arguments: crt_pipe_beeper.exe

#include <windows.h>
#include <process.h>
#include <memory.h>
#include <string.h>
#include <stdio.h>
#include <fcntl.h>
#include <io.h>

#define   OUT_BUFF_SIZE 512
#define   READ_FD 0
#define   WRITE_FD 1
#define   BEEP_CHAR 7

char szBuffer[OUT_BUFF_SIZE];

int Filter(char* szBuff, ULONG nSize, int nChar)
{
   char* szPos = szBuff + nSize -1;
   char* szEnd = szPos;
   int nRet = nSize;

   while (szPos > szBuff)
   {
      if (*szPos == nChar)
         {
            memmove(szPos, szPos+1, szEnd - szPos);
            --nRet;
         }
      --szPos;
   }
   return nRet;
}

int main(int argc, char** argv)
{
   int nExitCode = STILL_ACTIVE;
   if (argc >= 2)
   {
      HANDLE hProcess;
      int fdStdOut;
      int fdStdOutPipe[2];

      // Create the pipe
      if(_pipe(fdStdOutPipe, 512, O_NOINHERIT) == -1)
         return   1;

      // Duplicate stdout file descriptor (next line will close original)
      fdStdOut = _dup(_fileno(stdout));

      // Duplicate write end of pipe to stdout file descriptor
      if(_dup2(fdStdOutPipe[WRITE_FD], _fileno(stdout)) != 0)
         return   2;

      // Close original write end of pipe
      _close(fdStdOutPipe[WRITE_FD]);

      // Spawn process
      hProcess = (HANDLE)_spawnvp(P_NOWAIT, argv[1],
       (const char* const*)&argv[1]);

      // Duplicate copy of original stdout back into stdout
      if(_dup2(fdStdOut, _fileno(stdout)) != 0)
         return   3;

      // Close duplicate copy of original stdout
      _close(fdStdOut);

      if(hProcess)
      {
         int nOutRead;
         while   (nExitCode == STILL_ACTIVE)
         {
            nOutRead = _read(fdStdOutPipe[READ_FD],
             szBuffer, OUT_BUFF_SIZE);
            if(nOutRead)
            {
               nOutRead = Filter(szBuffer, nOutRead, BEEP_CHAR);
               fwrite(szBuffer, 1, nOutRead, stdout);
            }

            if(!GetExitCodeProcess(hProcess,(unsigned long*)&nExitCode))
               return 4;
         }
      }
   }
   return nExitCode;
}
```

```Output
This is speaker beep number 1...
This is speaker beep number 2...
This is speaker beep number 3...
This is speaker beep number 4...
This is speaker beep number 5...
This is speaker beep number 6...
This is speaker beep number 7...
This is speaker beep number 8...
This is speaker beep number 9...
This is speaker beep number 10...
```

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
