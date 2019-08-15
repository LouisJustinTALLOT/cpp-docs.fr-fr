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
ms.openlocfilehash: 14e5ea3a051d81828c5f88ac16df60b6ebb5b559
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498815"
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
Tableau de chaînes terminées par le caractère NULL qui représentent les arguments de ligne de commande entrés par l’utilisateur du programme. Par Convention, `argv[0]` est la commande avec laquelle le programme est appelé, `argv[1]` est le premier argument de ligne de commande, et ainsi de suite, `argv[argc]`jusqu’à, qui a toujours la valeur null. Pour plus d’informations sur la suppression du traitement de ligne de commande, consultez Personnalisation du traitement de la [ligne de commande](../cpp/customizing-cpp-command-line-processing.md) .

Le premier argument de ligne de commande est toujours `argv[1]` et le dernier `argv[argc - 1]`.

> [!NOTE]
> Par Convention, `argv[0]` est la commande avec laquelle le programme est appelé.  Toutefois, il est possible de générer un processus à l’aide de [CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) et si vous utilisez à la fois le premier et le deuxième argument `argv[0]` (*lpApplicationName* et *lpCommandLine*), peut ne pas être le nom de l’exécutable; utiliser [GetModuleFileName ](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew)pour récupérer le nom de l’exécutable et son chemin d’accès complet.

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

*envp*<br/>
Le tableau *envp* , qui est une extension courante dans de nombreux systèmes UNIX, est utilisé dans C++Microsoft. Il s'agit d'un tableau de chaînes représentant les variables définies dans l'environnement de l'utilisateur. Ce tableau se termine par une entrée NULL. Il peut être déclaré comme tableau de pointeurs vers **char** `char *envp[]`() ou comme pointeur vers des pointeurs vers **char** (`char **envp`). Si votre programme utilise `wmain` au lieu `main`de, utilisez le type de données **wchar_t** au lieu de **char**. Le bloc d’environnement passé `main` à `wmain` et est une copie «figée» de l’environnement actuel. Si vous modifiez ultérieurement l’environnement via un appel à `putenv` ou `_wputenv`, l’environnement actuel (tel que retourné `getenv` par `_wgetenv` ou et `_environ` la `_wenviron` variable ou) sera modifié, mais le bloc désigné par envp ne change pas. Pour plus d’informations sur la suppression du traitement de l’environnement, consultez Personnalisation du traitement de la [ligne de commande](../cpp/customizing-cpp-command-line-processing.md) . Cet argument est compatible ANSI en C, mais pas en C++.

**FIN de la section spécifique à Microsoft**

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