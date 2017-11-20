---
title: Analyse des arguments de ligne de commande C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- command line, parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: ffce8037-2811-45c4-8db4-1ed787859c80
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 95369f7554a557677636ea9c70665424e7e80c83
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="parsing-c-command-line-arguments"></a>Analyse des arguments de ligne de commande C
**Section spécifique à Microsoft**  
  
 Le code de démarrage Microsoft C utilise les règles suivantes lors de l’interprétation des arguments spécifiés dans la ligne de commande du système d’exploitation :  
  
-   Les arguments sont délimités par un espace blanc, qui peut être un espace ou une tabulation.  
  
-   Une chaîne placée entre guillemets doubles est interprétée comme un argument unique, quels que soient les espaces blancs inclus. Une chaîne entre guillemets peut être incorporée dans un argument. Notez que le signe insertion (**^**) n'est pas reconnu comme caractère d'échappement ni comme délimiteur.  
  
-   Un guillemet double précédé d'une barre oblique inverse **\\\"** est interprété comme un caractère guillemet double littéral (**"**).  
  
-   Les barres obliques inverses sont interprétées littéralement, sauf si elles précèdent immédiatement un guillemet double.  
  
-   Si un nombre pair de barres obliques inverses est suivi d'un guillemet double, une barre oblique inverse (**\\**) est placée dans le tableau `argv` pour chaque paire de barres obliques inverses (**\\\\**) et le guillemet double (**"**) est interprété comme un délimiteur de chaîne.  
  
-   Si un nombre impair de barres obliques inverses est suivi d'un guillemet double, une barre oblique inverse (**\\**) est placée dans le tableau `argv` pour chaque paire de barres obliques inverses (**\\\\**) et le guillemet double est interprétée comme une séquence d'échappement par la barre oblique inverse restante, provoquant l'insertion d'un guillemet double littéral (**"**) dans `argv`.  
  
 Cette liste illustre les règles énoncées ci-dessus en indiquant le résultat interprété passé à `argv` pour plusieurs exemples d'arguments de ligne de commande. La sortie indiquée dans les deuxième, troisième et quatrième colonnes provient du programme ARGS.C qui suit la liste.  
  
|Entrée sur la ligne de commande|argv[1]|argv[2]|argv[3]|  
|-------------------------|---------------|---------------|---------------|  
|`"a b c" d e`|`a b c`|`d`|`e`|  
|`"ab\"c" "\\" d`|`ab"c`|`\`|`d`|  
|`a\\\b d"e f"g h`|`a\\\b`|`de fg`|`h`|  
|`a\\\"b c d`|`a\"b`|`c`|`d`|  
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|  
  
## <a name="example"></a>Exemple  
  
### <a name="code"></a>Code  
  
```  
// Parsing_C_Commandline_args.c  
// ARGS.C illustrates the following variables used for accessing  
// command-line arguments and environment variables:  
// argc  argv  envp  
//  
  
#include <stdio.h>  
  
int main( int argc, // Number of strings in array argv  
 char *argv[],      // Array of command-line argument strings  
 char **envp )      // Array of environment variable strings  
{  
    int count;  
  
    // Display each command-line argument.  
    printf_s( "\nCommand-line arguments:\n" );  
    for( count = 0; count < argc; count++ )  
        printf_s( "  argv[%d]   %s\n", count, argv[count] );  
  
    // Display each environment variable.  
    printf_s( "\nEnvironment variables:\n" );  
    while( *envp != NULL )  
        printf_s( "  %s\n", *(envp++) );  
  
    return;  
}  
```  
  
## <a name="comments"></a>Commentaires  
 Voici un exemple de sortie de ce programme :  
  
```  
Command-line arguments:  
  argv[0]   C:\MSC\TEST.EXE  
  
Environment variables:  
  COMSPEC=C:\NT\SYSTEM32\CMD.EXE  
  
  PATH=c:\nt;c:\binb;c:\binr;c:\nt\system32;c:\word;c:\help;c:\msc;c:\;  
  PROMPT=[$p]   
  TEMP=c:\tmp  
  TMP=c:\tmp  
  EDITORS=c:\binr  
  WINDIR=c:\nt        
```  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction main et exécution du programme](../c-language/main-function-and-program-execution.md)