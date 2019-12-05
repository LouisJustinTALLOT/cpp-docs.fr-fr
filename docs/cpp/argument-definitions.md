---
title: Définitions d’arguments
ms.date: 11/04/2016
helpviewer_keywords:
- envp argument
- main function, arguments
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 6148cbf3-ebe8-44f2-b277-de4b723991c7
ms.openlocfilehash: aebd4800ad8d653d532708784ef0a5333211d46b
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857656"
---
# <a name="argument-definitions"></a>Définitions d’arguments

Les arguments dans le prototype

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

permettent d’analyser facilement les arguments sur la ligne de commande et, éventuellement, d’accéder aux variables d’environnement. Les définitions d’argument sont les suivantes :

*argc*<br/>
Entier qui contient le nombre d’arguments qui suivent dans *argv*. Le paramètre *argc* est toujours supérieur ou égal à 1.

*argv*<br/>
Tableau de chaînes terminées par le caractère NULL qui représentent les arguments de ligne de commande entrés par l’utilisateur du programme. Par Convention, `argv[0]` est la commande avec laquelle le programme est appelé, `argv[1]` est le premier argument de ligne de commande, et ainsi de suite, jusqu’à `argv[argc]`, qui est toujours NULL. Pour plus d’informations sur la suppression du traitement de ligne de commande, consultez Personnalisation du traitement de la [ligne de commande](../cpp/customizing-cpp-command-line-processing.md) .

Le premier argument de ligne de commande est toujours `argv[1]` et le dernier `argv[argc - 1]`.

> [!NOTE]
> Par Convention, `argv[0]` est la commande avec laquelle le programme est appelé.  Toutefois, il est possible de générer un processus à l’aide de [CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) et, si vous utilisez le premier et le deuxième arguments (*lpApplicationName* et *lpCommandLine*), `argv[0]` peut ne pas être le nom de l’exécutable ; Utilisez [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) pour récupérer le nom de l’exécutable et son chemin d’accès complet.

**Section spécifique de Microsoft**

*envp*<br/>
Le tableau *envp* , qui est une extension courante dans de nombreux systèmes UNIX, est utilisé dans C++Microsoft. Il s'agit d'un tableau de chaînes représentant les variables définies dans l'environnement de l'utilisateur. Ce tableau se termine par une entrée NULL. Il peut être déclaré comme un tableau de pointeurs vers **char** (`char *envp[]`) ou comme pointeur vers des pointeurs vers **char** (`char **envp`). Si votre programme utilise `wmain` au lieu de `main`, utilisez le type de données **wchar_t** au lieu de **char**. Le bloc d’environnement passé à `main` et `wmain` est une copie « figée » de l’environnement actuel. Si vous modifiez ultérieurement l’environnement via un appel à `putenv` ou `_wputenv`, l’environnement actuel (tel que retourné par `getenv` ou `_wgetenv` et la variable `_environ` ou `_wenviron`) est modifié, mais le bloc pointé par envp ne change pas. Pour plus d’informations sur la suppression du traitement de l’environnement, consultez Personnalisation du traitement de la [ligne de commande](../cpp/customizing-cpp-command-line-processing.md) . Cet argument est compatible ANSI en C, mais pas en C++.

**Fin de la section spécifique de Microsoft**

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser les arguments *argc*, *argv*et *envp* pour `main`:

```cpp
// argument_definitions.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;
int main( int argc, char *argv[], char *envp[] ) {
    int iNumberLines = 0;    // Default is no line numbers.

    // If /n is passed to the .exe, display numbered listing
    // of environment variables.

    if ( (argc == 2) && _stricmp( argv[1], "/n" ) == 0 )
         iNumberLines = 1;

    // Walk through list of strings until a NULL is encountered.
    for( int i = 0; envp[i] != NULL; ++i ) {
        if( iNumberLines )
            cout << i << ": " << envp[i] << "\n";
    }
}
```

## <a name="see-also"></a>Voir aussi

[main : démarrage du programme](../cpp/main-program-startup.md)