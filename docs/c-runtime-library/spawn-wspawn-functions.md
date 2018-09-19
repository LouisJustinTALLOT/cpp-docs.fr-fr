---
title: _spawn, _wspawn, fonctions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- _spawn
- _tspawnlp
- _tspawnlpe
- _tspawnve
- _tspawnvp
- _tspawnvpe
- _tspawnl
- spawn
- _tspawnv
- _tspawnle
- wspawn
dev_langs:
- C++
helpviewer_keywords:
- _tspawnve function
- _spawn functions
- _tspawnlpe function
- tspawnvpe function
- processes, creating
- tspawnve function
- _tspawnvp function
- spawn functions
- tspawnl function
- tspawnlp function
- _tspawnvpe function
- _tspawnl function
- tspawnvp function
- tspawnv function
- processes, executing new
- _tspawnv function
- tspawnle function
- process creation
- _tspawnlp function
- tspawnlpe function
- _tspawnle function
ms.assetid: bb47c703-5216-4e09-8023-8cf25bbf2cf9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cafa9e91ce16c2b18d80699363b615d55932bdb4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068557"
---
# <a name="spawn-wspawn-functions"></a>_spawn, _wspawn, fonctions

Chacune des fonctions `_spawn` crée et exécute un nouveau processus :

|||
|-|-|
|[_spawnl, _wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[_spawnv, _wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|
|[_spawnle, _wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[_spawnve, _wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|
|[_spawnlp, _wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[_spawnvp, _wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|
|[_spawnlpe, _wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[_spawnvpe, _wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|

Les lettres à la fin du nom de la fonction déterminent la variation.

|Lettre|Variante|
|-|-|
| `e`  | `envp`, un tableau de pointeurs vers les paramètres d'environnement, est passé au nouveau processus.  |
| `l`  | Les arguments de ligne de commande sont passés individuellement à la fonction `_spawn`. Ce suffixe est généralement utilisé lorsque plusieurs paramètres d'un nouveau processus sont connus à l'avance.  |
| `p`  | La variable d'environnement `PATH` est utilisée pour rechercher le fichier à exécuter.  |
| `v`  | `argv`, un tableau de pointeurs vers les arguments de ligne de commande, est passé à la fonction `_spawn`. Ce suffixe est généralement utilisé lorsque plusieurs paramètres d'un nouveau processus sont variables.  |

## <a name="remarks"></a>Notes

Les fonctions `_spawn` créent et exécutent chacune un nouveau processus. Elles gèrent automatiquement les arguments de chaîne de caractères multioctets si nécessaire, en identifiant les séquences de caractères multioctets en fonction de la page de codes multioctets en cours d'utilisation. Les fonctions `_wspawn` sont des versions à caractères larges des fonctions `_spawn` ; elles ne gèrent pas les chaînes de caractères multioctets. Sinon, les fonctions `_wspawn` se comportent de la même manière que leurs fonctions équivalentes `_spawn`.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_tspawnl`|`_spawnl`|`_spawnl`|`_wspawnl`|
|`_tspawnle`|`_spawnle`|`_spawnle`|`_wspawnle`|
|`_tspawnlp`|`_spawnlp`|`_spawnlp`|`_wspawnlp`|
|`_tspawnlpe`|`_spawnlpe`|`_spawnlpe`|`_wspawnlpe`|
|`_tspawnv`|`_spawnv`|`_spawnv`|`_wspawnv`|
|`_tspawnve`|`_spawnve`|`_spawnve`|`_wspawnve`|
|`_tspawnvp`|`_spawnvp`|`_spawnvp`|`_wspawnvp`|
|`_tspawnvpe`|`_spawnvpe`|`_spawnvpe`|`_wspawnvpe`|

Une quantité de mémoire suffisante doit être disponible pour charger et exécuter le nouveau processus. L'argument `mode` détermine l'action effectuée par le processus appelant avant et pendant `_spawn`. Les valeurs suivantes pour `mode` sont définies dans Process.h :

|||
|-|-|
| `_P_OVERLAY`  | Superpose un processus appelant avec un nouveau processus, en détruisant le processus appelant (même effet que les appels `_exec`).  |
| `_P_WAIT`  | Interrompt un thread appelant jusqu'à ce que l'exécution du nouveau processus soit terminée (`_spawn` synchrone).  |
| `_P_NOWAIT` ou `_P_NOWAITO`  | Continue d'exécuter un processus appelant en même temps que le nouveau processus (`_spawn` asynchrone).  |
| `_P_DETACH`  | Continue d'exécuter le processus appelant ; le nouveau processus est exécuté en arrière-plan sans accès à la console ou au clavier. Les appels à `_cwait` dans le nouveau processus échouent (`_spawn` asynchrone).  |

L'argument `cmdname` spécifie le fichier exécuté en tant que nouveau processus et peut spécifier un chemin d'accès complet (à partir de la racine), un chemin d'accès partiel (à partir du répertoire de travail actuel) ou simplement un nom de fichier. Si `cmdname` ne porte pas une extension de nom de fichier ou ne se termine pas par un point (.), la fonction `_spawn` tente d'abord l'extension de nom de fichier .com, puis l'extension de nom de fichier .exe, l'extension de nom de fichier .bat et enfin l'extension de nom de fichier .cmd.

Si `cmdname` a une extension de nom de fichier, seule cette extension est utilisée. Si `cmdname` se termine par un point, l'appel `_spawn` recherche `cmdname` sans extension de nom de fichier. Les fonctions `_spawnlp`, `_spawnlpe`, `_spawnvp` et `_spawnvpe` recherchent `cmdname` (à l’aide des mêmes procédures) dans les répertoires spécifiés par la variable d’environnement `PATH`.

Si `cmdname` contient un spécificateur de lecteur ou des barres obliques (autrement dit, s'il s'agit d'un chemin d'accès relatif), l'appel `_spawn` recherche uniquement le fichier spécifié ; le chemin d'accès n'est pas recherché.

Dans le passé, certaines de ces fonctions affectaient à `errno` la valeur zéro en cas de réussite ; le comportement actuel est de laisser `errno` intact en cas de réussite, comme spécifié dans la norme C. Si vous devez émuler l'ancien comportement, affectez à `errno` la valeur zéro juste avant d'appeler ces fonctions.

> [!NOTE]
>  Pour garantir l'initialisation et l'arrêt de la superposition, n'utilisez pas la fonction `setjmp` ou la fonction `longjmp` pour entrer ou quitter une routine de superposition.

## <a name="arguments-for-the-spawned-process"></a>Arguments du processus engendré

Pour passer des arguments au nouveau processus, fournissez un ou plusieurs pointeurs aux chaînes de caractères en tant qu'arguments dans l'appel `_spawn`. Ces chaînes de caractères forment la liste d'arguments du processus engendré. La longueur combinée des chaînes qui forment la liste d'arguments du nouveau processus ne doit pas dépasser 1024 octets. Le caractère null de fin ('\0') pour chaque chaîne n'est pas inclus dans le décompte, mais les espaces (insérés automatiquement pour séparer les arguments) sont inclus.

> [!NOTE]
>  Les espaces incorporés dans les chaînes peuvent provoquer un comportement inattendu ; par exemple, le passage à `_spawn` de la chaîne `"hi there"` a comme conséquence que le nouveau processus obtient deux arguments, `"hi"` et `"there"`. Si l'objectif était que le nouveau processus ouvre un fichier nommé « hi there », le processus échoue. Vous pouvez éviter cela en plaçant la chaîne `"\"hi there\""` entre guillemets.

> [!IMPORTANT]
>  Ne passez pas d'entrée utilisateur à `_spawn` sans vérifier explicitement son contenu. `_spawn` entraîne un appel à [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa), alors gardez à l’esprit que les noms de chemin incomplets peut créer des failles de sécurité potentielles.

Vous pouvez passer des pointeurs d'arguments en tant qu'arguments distincts (dans `_spawnl`, `_spawnle`, `_spawnlp` et `_spawnlpe`) ou en tant que tableau de pointeurs (dans `_spawnv`, `_spawnve`, `_spawnvp` et `_spawnvpe`). Vous devez passer au moins un argument, `arg0` ou `argv`[0], au processus engendré. Par convention, cet argument correspond au nom du programme tel que vous le taperiez sur la ligne de commande. Une valeur différente ne produit pas d'erreur.

Les appels `_spawnl`, `_spawnle`, `_spawnlp` et `_spawnlpe` sont généralement utilisés dans les cas où le nombre d'arguments est connu à l'avance. L’argument `arg0` est généralement un pointeur vers `cmdname`. Les arguments `arg1` à `argn` sont des pointeurs vers les chaînes de caractères formant la nouvelle liste d’arguments. Après `argn`, il doit exister un pointeur **NULL** pour marquer la fin de la liste des arguments.

Les appels `_spawnv`, `_spawnve`, `_spawnvp` et `_spawnvpe` sont utiles lorsque le nouveau processus contient un nombre variable d'arguments. Les pointeurs vers les arguments sont passés en tant que tableau, `argv`*.* L’argument `argv`[0] est généralement un pointeur qui désigne un chemin en mode réel ou le nom de programme en mode protégé, tandis que `argv`[1] à `argv`[`n`] sont des pointeurs qui pointent vers les chaînes de caractères formant la nouvelle liste d’arguments. L’argument `argv`[`n` +1] doit être un pointeur **NULL** pour marquer la fin de la liste d’arguments.

## <a name="environment-of-the-spawned-process"></a>Environnement du processus engendré

Les fichiers ouverts pendant un appel `_spawn` restent ouverts dans le nouveau processus. Dans les appels `_spawnl`, `_spawnlp`, `_spawnv` et `_spawnvp`, le nouveau processus hérite de l'environnement du processus appelant. Vous pouvez utiliser les appels `_spawnle`, `_spawnlpe`, `_spawnve` et `_spawnvpe` pour modifier l'environnement du nouveau processus en passant une liste de paramètres d'environnement via l'argument `envp`. L'argument `envp` est un tableau de pointeurs de caractère, dont chaque élément (excepté le dernier) pointe vers une chaîne terminée par le caractère null qui définit une variable d'environnement. Une telle chaîne a généralement la forme `NAME`=`value` où `NAME` est le nom d’une variable d’environnement et `value` est la valeur de chaîne selon laquelle cette variable est définie. (Notez que `value` n'est pas placé entre guillemets doubles.) Le dernier élément du tableau `envp` doit être **NULL**. Quand `envp` lui-même a la valeur **NULL**, le processus engendré hérite des paramètres d’environnement du processus parent.

Les fonctions `_spawn` peuvent passer toutes les informations sur les fichiers ouverts, y compris le mode de traduction, au nouveau processus. Ces informations sont passées en mode réel via l'entrée `C_FILE_INFO` de l'environnement. Le code de démarrage traite normalement cette entrée et la supprime ensuite de l'environnement. Toutefois, si une fonction `_spawn` génère un processus autre que C, cette entrée reste dans l'environnement. L'impression de l'environnement montre les caractères graphiques de la chaîne de définition pour cette entrée, car les informations d'environnement sont passées au format binaire en mode réel. Il ne devrait y avoir aucun autre effet sur les opérations normales. En mode protégé, les informations d'environnement sont passées au format texte et donc ne contiennent pas de caractères graphiques.

Vous devez explicitement vider (à l'aide de `fflush` ou `_flushall`) ou fermer un flux avant d'appeler une fonction `_spawn`.

Les nouveaux processus créés par des appels aux routines `_spawn` ne conservent pas les précédents paramètres de signal. En revanche, le processus engendré réinitialise les valeurs par défaut des paramètres de signal.

## <a name="redirecting-output"></a>Redirection de la sortie

Si vous appelez `_spawn` à partir d'une DLL ou d'une application GUI et souhaitez rediriger la sortie vers un canal, deux options sont possibles :

- Utilisez l’API Win32 pour créer un canal, appelez [AllocConsole](https://msdn.microsoft.com/library/windows/desktop/ms681944), définissez les valeurs de handle dans la structure de démarrage, puis appelez [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa).

- Appelez [_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md), ce qui crée un canal et appelle l’application à l’aide de **cmd.exe /c** (ou **command.exe /c**).

## <a name="example"></a>Exemple

```
// crt_spawn.c
// This program accepts a number in the range
// 1-8 from the command line. Based on the number it receives,
// it executes one of the eight different procedures that
// spawn the process named child. For some of these procedures,
// the CHILD.EXE file must be in the same directory; for
// others, it only has to be in the same path.
//

#include <stdio.h>
#include <process.h>

char *my_env[] =
{
   "THIS=environment will be",
   "PASSED=to child.exe by the",
   "_SPAWNLE=and",
   "_SPAWNLPE=and",
   "_SPAWNVE=and",
   "_SPAWNVPE=functions",
   NULL
};

int main( int argc, char *argv[] )
{
   char *args[4];

   // Set up parameters to be sent:
   args[0] = "child";
   args[1] = "spawn??";
   args[2] = "two";
   args[3] = NULL;

   if (argc <= 2)
   {
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );
      exit( 1 );
   }

   switch (argv[1][0])   // Based on first letter of argument
   {
   case '1':
      _spawnl( _P_WAIT, argv[2], argv[2], "_spawnl", "two", NULL );
      break;
   case '2':
      _spawnle( _P_WAIT, argv[2], argv[2], "_spawnle", "two",
               NULL, my_env );
      break;
   case '3':
      _spawnlp( _P_WAIT, argv[2], argv[2], "_spawnlp", "two", NULL );
      break;
   case '4':
      _spawnlpe( _P_WAIT, argv[2], argv[2], "_spawnlpe", "two",
                NULL, my_env );
      break;
   case '5':
      _spawnv( _P_OVERLAY, argv[2], args );
      break;
   case '6':
      _spawnve( _P_OVERLAY, argv[2], args, my_env );
      break;
   case '7':
      _spawnvp( _P_OVERLAY, argv[2], args );
      break;
   case '8':
      _spawnvpe( _P_OVERLAY, argv[2], args, my_env );
      break;
   default:
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );
      exit( 1 );
   }
   printf( "from SPAWN!\n" );
}
```

```Output
child process output
from SPAWN!
```

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../c-runtime-library/process-and-environment-control.md)<br/>
[abort](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[_exec, _wexec, fonctions](../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_flushall](../c-runtime-library/reference/flushall.md)<br/>
[_getmbcp](../c-runtime-library/reference/getmbcp.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_setmbcp](../c-runtime-library/reference/setmbcp.md)<br/>
[system, _wsystem](../c-runtime-library/reference/system-wsystem.md)