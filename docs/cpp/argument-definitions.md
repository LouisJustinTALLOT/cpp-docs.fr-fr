---
title: Définitions d’arguments | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- envp argument
- main function, arguments
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 6148cbf3-ebe8-44f2-b277-de4b723991c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e0c42478e5e6ce3c9efe66c45ed32292f2040a83
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49084150"
---
# <a name="argument-definitions"></a>Définitions d’arguments

Les arguments dans le prototype

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

permettent d'analyser facilement les arguments sur la ligne de commande et, éventuellement, d'accéder aux variables d'environnement. Les définitions d’argument sont les suivantes :

*argc*<br/>
Entier qui contient le nombre d’arguments qui suivent dans *argv*. Le *argc* paramètre est toujours supérieure ou égale à 1.

*argv*<br/>
Tableau de chaînes terminées par le caractère NULL qui représentent les arguments de ligne de commande entrés par l’utilisateur du programme. Par convention, `argv` **[0]** est la commande avec laquelle le programme est appelé, `argv` **[1]** est le premier argument de ligne de commande et ainsi de suite, jusqu'à ce que `argv`  **[**`argc`**]**, qui est toujours NULL. Consultez [personnalisation du traitement de ligne de commande](../cpp/customizing-cpp-command-line-processing.md) pour plus d’informations sur la suppression du traitement de ligne de commande.

Le premier argument de ligne de commande est toujours `argv` **[1]** et le dernier `argv` **[** `argc` - 1 **]**.

> [!NOTE]
>  Par convention, `argv`**[0]** est la commande avec laquelle le programme est appelé.  Toutefois, il est possible de générer un processus utilisant [CreateProcess](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulefilenamea) et si vous utilisez le premier et le deuxième argument (*IpApplicationName* et *lpCommandLine*), `argv` **[0]** peut ne pas être le fichier exécutable nom ; utiliser [GetModuleFileName](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulefilenamea) pour récupérer le nom de l’exécutable et son chemin d’accès qualifié complet.

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

*envp*<br/>
Le *envp* tableau, qui est une extension courante dans de nombreux systèmes UNIX, est utilisé dans Microsoft C++. Il s'agit d'un tableau de chaînes représentant les variables définies dans l'environnement de l'utilisateur. Ce tableau se termine par une entrée NULL. Il peut être déclaré en tant que tableau de pointeurs vers **char (char** \*envp []**)** ou en tant que pointeur vers des pointeurs en **char (char** \* \* envp **)**. Si votre programme utilise `wmain` au lieu de `main`, utilisez le `wchar_t` au lieu du type de données **char**. Le bloc environnement passé à `main` et `wmain` est une copie « figée » de l’environnement actuel. Si vous modifiez ultérieurement l’environnement via un appel à `putenv` ou `_wputenv`, l’environnement actuel (tel que retourné par `getenv` / `_wgetenv` et `_environ` /  `_wenviron` variable) sera modification, mais le bloc dirigé vers envp ne changera pas. Consultez [personnalisation du traitement de ligne de commande](../cpp/customizing-cpp-command-line-processing.md) pour plus d’informations sur la suppression du traitement de l’environnement. Cet argument est compatible ANSI en C, mais pas en C++.

**FIN de la section spécifique à Microsoft**

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le *argc*, *argv*, et *envp* arguments à `main`:

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