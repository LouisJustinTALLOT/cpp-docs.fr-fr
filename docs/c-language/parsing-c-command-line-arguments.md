---
title: Analyse des arguments de ligne de commande C
description: Découvrez comment le code de démarrage Microsoft C Runtime interprète les arguments de ligne de commande pour créer les paramètres argv et argc.
ms.date: 11/09/2020
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- double quote marks
- command line, parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: ffce8037-2811-45c4-8db4-1ed787859c80
ms.openlocfilehash: 92921e91ee6bb37b2bf7b702a1b31ed045187b59
ms.sourcegitcommit: b38485bb3a9d479e0c5d64ffc3d841fa2c2b366f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94441253"
---
# <a name="parsing-c-command-line-arguments"></a>Analyse des arguments de ligne de commande C

**Spécifique à Microsoft**

Le code de démarrage Microsoft C utilise les règles suivantes lors de l’interprétation des arguments spécifiés dans la ligne de commande du système d’exploitation :

- Les arguments sont délimités par un espace blanc, qui peut être un espace ou une tabulation.

- Le premier argument ( `argv[0]` ) est traité de façon spéciale. Elle représente le nom du programme. Comme il doit s’agir d’un nom de chemin d’accès valide, les pièces entourées par des guillemets doubles ( **`"`** ) sont autorisées. Les guillemets doubles ne sont pas inclus dans la `argv[0]` sortie. Les parties entourées par des guillemets doubles empêchent l’interprétation d’un espace ou d’un caractère de tabulation comme fin de l’argument. Les règles ultérieures de cette liste ne s’appliquent pas.

- Une chaîne entourée de guillemets doubles est interprétée comme un argument unique, qu’elle contienne ou non un espace blanc. Une chaîne entre guillemets peut être incorporée dans un argument. Le signe insertion ( **`^`** ) n’est pas reconnu comme caractère d’échappement ni comme délimiteur. Dans une chaîne entre guillemets, une paire de guillemets doubles est interprétée comme un guillemet double placé dans une séquence d’échappement. Si la ligne de commande se termine avant qu’un guillemet double fermant soit trouvé, tous les caractères lus jusqu’à présent sont générés comme étant le dernier argument.

- Un guillemet double précédé d’une barre oblique inverse ( **`\"`** ) est interprété comme un guillemet double littéral ( **`"`** ).

- Les barres obliques inverses sont interprétées littéralement, sauf si elles précèdent immédiatement un guillemet double.

- Si un nombre pair de barres obliques inverses est suivi d’un guillemet double, une barre oblique inverse ( **`\`** ) est placée dans le `argv` tableau pour chaque paire de barres obliques inverses ( **`\\`** ) et le guillemet double ( **`"`** ) est interprété comme un délimiteur de chaîne.

- Si un nombre impair de barres obliques inverses est suivi d’un guillemet double, une barre oblique inverse ( **`\`** ) est placée dans le `argv` tableau pour chaque paire de barres obliques inverses ( **`\\`** ). Le guillemet double est interprété comme une séquence d’échappement par la barre oblique inverse restante, ce qui entraîne la mise en place d’un guillemet double littéral ( **`"`** ) `argv` .

Cette liste illustre les règles énoncées ci-dessus en indiquant le résultat interprété passé à `argv` pour plusieurs exemples d'arguments de ligne de commande. La sortie indiquée dans les deuxième, troisième et quatrième colonnes provient du programme ARGS.C qui suit la liste.

|Entrée sur la ligne de commande|argv[1]|argv[2]|argv[3]|
|-------------------------|---------------|---------------|---------------|
|`"a b c" d e`|`a b c`|`d`|`e`|
|`"ab\"c" "\\" d`|`ab"c`|`\`|`d`|
|`a\\\b d"e f"g h`|`a\\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|
|`a"b"" c d`|`ab" c d`|||

## <a name="example"></a>Exemple

### <a name="code"></a>Code

```c
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

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Fonction main et exécution du programme](../c-language/main-function-and-program-execution.md)
