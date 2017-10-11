---
title: "Définitions d’arguments | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: d50e32a54cdb10af4adbfb3cfda64b8f1b21b2eb
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="argument-definitions"></a>Définitions d’arguments
Les arguments dans le prototype  
  
```  
  
int main( int  
argc[ ,char*argv[] [,char*envp[] ] ] );intwmain(intargc[ ,wchar_t*argv[] [,wchar_t*envp[] ] ] );  
```  
  
 permettent d'analyser facilement les arguments sur la ligne de commande et, éventuellement, d'accéder aux variables d'environnement. Les définitions d’argument sont les suivantes :  
  
 `argc`  
 Entier qui contient le nombre d'arguments qui se suivent dans `argv`. Le paramètre `argc` est toujours supérieur ou égal à 1.  
  
 `argv`  
 Tableau de chaînes terminées par le caractère NULL qui représentent les arguments de ligne de commande entrés par l’utilisateur du programme. Par convention, `argv` **[0]** est la commande à laquelle le programme est appelé, `argv` **[1]** est le premier argument de ligne de commande et ainsi de suite, jusqu’au `argv` ** [**`argc`**]**, qui est toujours **NULL**. Consultez [personnalisation du traitement de ligne de commande](../cpp/customizing-cpp-command-line-processing.md) pour plus d’informations sur la suppression du traitement de ligne de commande.  
  
 Le premier argument de ligne de commande est toujours `argv` **[1]** et la dernière n’est pas `argv` **[** `argc` - 1**]**.  
  
> [!NOTE]
>  Par convention, `argv`**[0]** est la commande avec laquelle le programme est appelé.  Toutefois, il est possible de lancer un processus à l’aide de [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms683197) et si vous utilisez les premier et le second arguments (`lpApplicationName` et `lpCommandLine`), `argv` **[0]** ne peut pas être le nom du fichier exécutable ; Utilisez [GetModuleFileName](http://msdn.microsoft.com/library/windows/desktop/ms683197) pour récupérer le nom du fichier exécutable et son chemin d’accès qualifié complet.  
  
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 `envp`  
 Le tableau `envp`, qui est une extension courante dans de nombreux systèmes Unix, est utilisé dans Microsoft C++. Il s'agit d'un tableau de chaînes représentant les variables définies dans l'environnement de l'utilisateur. Ce tableau se termine par un **NULL** entrée. Il peut être déclaré comme un tableau de pointeurs vers les **char (char** \*envp []**)** ou sous la forme d’un pointeur vers des pointeurs en **char (char** \* \* envp**)**. Si votre programme utilise **wmain** au lieu de **principal**, utilisez le `wchar_t` de type de données à la place de `char`. Le bloc environnement passé à **principal** et **wmain** est une copie « figée » de l’environnement actuel. Si vous modifiez ultérieurement l’environnement via un appel à **putenv** ou `_wputenv`, l’environnement actuel (tel que retourné par `getenv` / `_wgetenv` et `_environ` /  `_wenviron` variable) est modifié, mais le bloc dirigé vers envp ne changera pas. Consultez [personnalisation du traitement de ligne de commande](../cpp/customizing-cpp-command-line-processing.md) pour plus d’informations sur la suppression du traitement de l’environnement. Cet argument est compatible ANSI en C, mais pas en C++.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `argc`, `argv`, et `envp` arguments **principal**:  
  
```  
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
