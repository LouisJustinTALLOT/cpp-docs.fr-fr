---
title: _exec, _wexec, fonctions
ms.date: 11/04/2016
apilocation:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _texecve
- texecl
- _texeclpe
- texecve
- texecv
- texeclp
- texecle
- exec
- texeclpe
- _texecvp
- _texecl
- _texecle
- wexec
- _exec
- _texeclp
- _texecvpe
- texecvpe
- _texecv
- _wexec
helpviewer_keywords:
- _texecle function
- _texecv function
- texeclpe function
- texecle function
- _texecl function
- texecv function
- _texeclp function
- _texecve function
- texecl function
- texecve function
- exec function
- texeclp function
- texecvp function
- texecvpe function
- processes, executing new
- _texecvp function
- _texeclpe function
- _wexec functions
- wexec functions
- _exec function
- _texecvpe function
ms.assetid: a261df93-206a-4fdc-b8ac-66aa7db83bc6
ms.openlocfilehash: d31192a25cce86dad6f8e1e8b0258a457d0a5436
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500134"
---
# <a name="_exec-_wexec-functions"></a>_exec, _wexec, fonctions

Chaque fonction dans cette famille charge et exécute un nouveau processus :

|||
|-|-|
|[_execl, _wexecl](../c-runtime-library/reference/execl-wexecl.md)|[_execv, _wexecv](../c-runtime-library/reference/execv-wexecv.md)|
|[_execle, _wexecle](../c-runtime-library/reference/execle-wexecle.md)|[_execve, _wexecve](../c-runtime-library/reference/execve-wexecve.md)|
|[_execlp, _wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|[_execvp, _wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|
|[_execlpe, _wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|[_execvpe, _wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|

La lettre à la fin du nom de fonction détermine la variance.

|Suffixe de fonction _exec|Description|
|----------------------------|-----------------|
|`e`|`envp`, un tableau de pointeurs vers les paramètres d'environnement, est passé au nouveau processus.|
|`l`|Les arguments de ligne de commande sont passés individuellement à la fonction `_exec`. Utilisée généralement quand le nombre de paramètres du nouveau processus est connu à l'avance.|
|`p`|La variable d'environnement `PATH` est utilisée pour rechercher le fichier à exécuter.|
|`v`|`argv`, un tableau de pointeurs vers des arguments de ligne de commande, est passé à `_exec`. Utilisée généralement quand le nombre de paramètres du nouveau processus est variable.|

## <a name="remarks"></a>Remarques

Chaque fonction `_exec` charge et exécute un nouveau processus. Toutes les fonctions `_exec` utilisent la même fonction de système d’exploitation ([CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw)). Les fonctions `_exec` gèrent automatiquement des arguments de chaîne de caractères multioctets de façon appropriée, en identifiant des séquences de caractères multioctets selon la page de codes multioctets actuellement utilisée. Les fonctions `_wexec` sont des versions à caractères larges des fonctions `_exec`. Les fonctions `_wexec` se comportent de la même façon que leurs équivalents de famille `_exec`, sauf qu'elles ne gèrent pas les chaînes de caractères multioctets.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_texecl`|`_execl`|`_execl`|`_wexecl`|
|`_texecle`|`_execle`|`_execle`|`_wexecle`|
|`_texeclp`|`_execlp`|`_execlp`|`_wexeclp`|
|`_texeclpe`|`_execlpe`|`_execlpe`|`_wexeclpe`|
|`_texecv`|`_execv`|`_execv`|`_wexecv`|
|`_texecve`|`_execve`|`_execve`|`_wexecve`|
|`_texecvp`|`_execvp`|`_execvp`|`_wexecvp`|
|`_texecvpe`|`_execvpe`|`_execvpe`|`_wexecvpe`|

Le paramètre `cmdname` spécifie le fichier à exécuter comme nouveau processus. Il peut spécifier un chemin d'accès complet (depuis la racine), un chemin d'accès partiel (depuis le répertoire de travail actif) ou un nom de fichier. Si `cmdname` n'a pas une extension de nom de fichier ou ne se termine pas par un point (.), la fonction `_exec` recherche le fichier nommé. Si la recherche n'aboutit pas, elle tente le même nom de base avec l'extension de nom de fichier .com, puis avec les extensions de nom de fichier .exe, .bat et .cmd. Si `cmdname` a une extension de nom de fichier, seule cette extension est employée dans la recherche. Si `cmdname` se termine par un point, la fonction `_exec` recherche `cmdname` sans extension de nom de fichier. `_execlp`, `_execlpe`, `_execvp` et `_execvpe` recherchent `cmdname` (en utilisant les mêmes procédures) dans les répertoires spécifiés par la variable d'environnement `PATH`. Si `cmdname` contient un spécificateur de lecteur ou des barres obliques (autrement dit, s'il s'agit d'un chemin d'accès relatif), l'appel de fonction `_exec` recherche uniquement le fichier spécifié ; aucune recherche n'est effectuée sur le chemin d'accès.

Les paramètres sont passés au nouveau processus en fournissant un ou plusieurs pointeurs vers des chaînes de caractères comme paramètres dans l'appel de fonction `_exec`. Ces chaînes de caractères forment la liste de paramètres du nouveau processus. La longueur combinée des paramètres d'environnement hérités et des chaînes qui forment la liste de paramètres du nouveau processus ne doit pas dépasser 32 kilo-octets. Le caractère Null de fin ('\0') pour chaque chaîne n'est pas inclus dans le décompte, mais les espaces (insérés automatiquement pour séparer les paramètres) sont dénombrés.

> [!NOTE]
>  Les espaces incorporés dans les chaînes peuvent provoquer un comportement inattendu ; par exemple, le passage à `_exec` de la chaîne `"hi there"` a comme conséquence que le nouveau processus obtient deux arguments, `"hi"` et `"there"`. Si l'objectif était que le nouveau processus ouvre un fichier nommé « hi there », le processus échoue. Vous pouvez éviter cela en plaçant la chaîne `"\"hi there\""` entre guillemets.

> [!IMPORTANT]
>  Ne passez pas d'entrée utilisateur à `_exec` sans vérifier explicitement son contenu. `_exec` entraîne un appel à [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw), alors gardez à l’esprit que les noms de chemin incomplets peut créer des failles de sécurité potentielles.

Les fonctions `_exec` valident leurs paramètres. Si les paramètres attendus sont des pointeurs Null ou des chaînes vides, ou sont omis, les fonctions `_exec` appellent le gestionnaire de paramètre non valide comme décrit dans [Validation de paramètre](../c-runtime-library/parameter-validation.md). Si l'exécution est autorisée à se poursuivre, ces fonctions définissent `errno` avec la valeur `EINVAL` et retournent -1. Aucun nouveau processus n'est exécuté.

Les pointeurs d'argument peuvent être passés comme paramètres distincts (dans `_execl`, `_execle`, `_execlp` et `_execlpe`) ou comme tableau de pointeurs (dans `_execv`, `_execve`, `_execvp` et `_execvpe`). Au moins un paramètre, `arg0`, doit être passé au nouveau processus ; ce paramètre est `argv`[0] du nouveau processus. Généralement, ce paramètre est une copie de `cmdname`. (Une valeur différente ne produit pas d'erreur.)

Les appels de fonctions `_execl`, `_execle`, `_execlp` et `_execlpe` sont généralement utilisés quand le nombre de paramètres est connu à l'avance. Le paramètre `arg0` est généralement un pointeur vers `cmdname`. Les paramètres `arg1` à `argn` pointent vers les chaînes de caractères qui forment la nouvelle liste de paramètres. Un pointeur Null doit suivre `argn` pour marquer la fin de la liste de paramètres.

Les appels de fonctions `_execv`, `_execve`, `_execvp` et `_execvpe` sont utiles quand le nombre de paramètres du nouveau processus est variable. Les pointeurs vers les paramètres sont passés comme tableau, `argv`. Le paramètre `argv`[0] est généralement un pointeur vers `cmdname`. Les paramètres `argv`[1] à `argv`[`n`] pointent vers les chaînes de caractères qui forment la nouvelle liste de paramètres. Le paramètre `argv`[`n`+1] doit être un pointeur **NULL** pour marquer la fin de la liste de paramètres.

Les fichiers qui sont ouverts quand un appel de fonction `_exec` est effectué restent ouverts dans le nouveau processus. Dans les appels de fonctions `_execl`, `_execlp`, `_execv` et `_execvp`, le nouveau processus hérite de l'environnement du processus appelant. Les appels de fonctions `_execle`, `_execlpe`, `_execve` et `_execvpe` modifient l'environnement du nouveau processus en passant une liste de paramètres d'environnement via le paramètre `envp`. `envp` est un tableau de pointeurs de caractères, dont chaque élément (excepté le dernier) pointe vers une chaîne terminée par le caractère Null définissant une variable d'environnement. Une telle chaîne a généralement la forme `NAME`=`value` où `NAME` est le nom d’une variable d’environnement et `value` est la valeur de chaîne selon laquelle cette variable est définie. (Notez que `value` n'est pas placé entre guillemets doubles.) Le dernier élément du tableau `envp` doit être **NULL**. Quand `envp` a la valeur **NULL**, le nouveau processus hérite des paramètres d’environnement du processus appelant.

Un programme exécuté avec l'une des fonctions `_exec` est toujours chargé en mémoire comme si le champ d'allocation maximale dans l'en-tête du fichier .exe du programme avait pris la valeur par défaut 0xFFFFH.

Les appels de fonction `_exec` ne conservent pas les modes de traduction des fichiers ouverts. Si le nouveau processus doit utiliser des fichiers hérités du processus appelant, utilisez la routine [_setmode](../c-runtime-library/reference/setmode.md) pour définir le mode de traduction souhaité pour ces fichiers. Vous devez explicitement vider (à l'aide de `fflush` ou de `_flushall`) ou fermer tout flux avant l'appel de fonction `_exec`. Les paramètres de signal ne sont pas conservés dans les nouveaux processus qui sont créés par des appels aux routines de fonction `_exec`. Les paramètres de signal sont réinitialisés à la valeur par défaut dans le nouveau processus.

## <a name="example"></a>Exemples

```
// crt_args.c
// Illustrates the following variables used for accessing
// command-line arguments and environment variables:
// argc  argv  envp
// This program will be executed by crt_exec which follows.

#include <stdio.h>

int main( int argc,  // Number of strings in array argv
char *argv[],       // Array of command-line argument strings
char **envp )       // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    printf( "\nCommand-line arguments:\n" );
    for( count = 0; count < argc; count++ )
        printf( "  argv[%d]   %s\n", count, argv[count] );

    // Display each environment variable.
    printf( "\nEnvironment variables:\n" );
    while( *envp != NULL )
        printf( "  %s\n", *(envp++) );

    return;
}
```

Lancez le programme suivant pour exécuter Crt_args.exe :

```
// crt_exec.c
// Illustrates the different versions of exec, including
//      _execl          _execle          _execlp          _execlpe
//      _execv          _execve          _execvp          _execvpe
//
// Although CRT_EXEC.C can exec any program, you can verify how
// different versions handle arguments and environment by
// compiling and specifying the sample program CRT_ARGS.C. See
// "_spawn, _wspawn Functions" for examples of the similar spawn
// functions.

#include <stdio.h>
#include <conio.h>
#include <process.h>

char *my_env[] =     // Environment for exec?e
{
   "THIS=environment will be",
   "PASSED=to new process by",
   "the EXEC=functions",
   NULL
};

int main( int ac, char* av[] )
{
   char *args[4];
   int ch;
   if( ac != 3 ){
      fprintf( stderr, "Usage: %s <program> <number (1-8)>\n", av[0] );
      return;
   }

   // Arguments for _execv?
   args[0] = av[1];
   args[1] = "exec??";
   args[2] = "two";
   args[3] = NULL;

   switch( atoi( av[2] ) )
   {
   case 1:
      _execl( av[1], av[1], "_execl", "two", NULL );
      break;
   case 2:
      _execle( av[1], av[1], "_execle", "two", NULL, my_env );
      break;
   case 3:
      _execlp( av[1], av[1], "_execlp", "two", NULL );
      break;
   case 4:
      _execlpe( av[1], av[1], "_execlpe", "two", NULL, my_env );
      break;
   case 5:
      _execv( av[1], args );
      break;
   case 6:
      _execve( av[1], args, my_env );
      break;
   case 7:
      _execvp( av[1], args );
      break;
   case 8:
      _execvpe( av[1], args, my_env );
      break;
   default:
      break;
   }

   // This point is reached only if exec fails.
   printf( "\nProcess was not execed." );
   exit( 0 );
}
```

## <a name="requirements"></a>Configuration requise

**En-tête :** process.h

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../c-runtime-library/process-and-environment-control.md)<br/>
[abort](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_spawn, _wspawn, fonctions](../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)
