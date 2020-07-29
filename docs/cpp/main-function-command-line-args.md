---
title: :::no-loc(main):::fonction et arguments de ligne de commande (C++)
description: 'La :::no-loc(main)::: fonction est le point d’entrée d’un programme C++.'
ms.date: 01/15/2019
ms.assetid: c6568ee6-40ab-4ae8-aa44-c99e232f64ac
no-loc:
- ':::no-loc(main):::'
- ':::no-loc(wmain):::'
- ':::no-loc(inline):::'
- ':::no-loc(static):::'
- ':::no-loc(_tmain):::'
- ':::no-loc(void):::'
- ':::no-loc(exit):::'
- ':::no-loc(argc):::'
- ':::no-loc(argv):::'
- ':::no-loc(envp):::'
- ':::no-loc(CreateProcess):::'
- ':::no-loc(GetModuleFileName):::'
- ':::no-loc(char):::'
- ':::no-loc(wchar_t):::'
- ':::no-loc(extern):::'
ms.openlocfilehash: 9fe7c7a0808584a70bffa541903866b3de364e5f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213318"
---
# <a name="no-locmain-function-and-command-line-arguments"></a>:::no-loc(main):::arguments de ligne de commande et de fonction

Tous les programmes C++ doivent avoir une `:::no-loc(main):::` fonction. Si vous essayez de compiler un projet C++ *. exe* sans :::no-loc(main)::: fonction, le compilateur génère une erreur. (Les bibliothèques de liens dynamiques et les :::no-loc(static)::: bibliothèques n’ont pas de `:::no-loc(main):::` fonction.) La `:::no-loc(main):::` fonction est l’emplacement où votre code source commence à s’exécuter, mais avant qu’un programme n’entre dans la `:::no-loc(main):::` fonction, tous les :::no-loc(static)::: membres de classe sans initialiseurs explicites sont définis à zéro. Dans Microsoft C++, :::no-loc(static)::: les objets globaux sont également initialisés avant l’entrée dans `:::no-loc(main):::` . Plusieurs restrictions s’appliquent à la `:::no-loc(main):::` fonction qui ne s’applique pas à d’autres fonctions C++. La `:::no-loc(main):::` fonction :

- Ne peut pas être surchargé (consultez [surcharge de fonction](function-overloading.md)).
- Ne peut pas être déclaré comme **`:::no-loc(inline):::`** .
- Ne peut pas être déclaré comme **`:::no-loc(static):::`** .
- son adresse ne peut pas être prise.
- Ne peut pas être appelé.

La :::no-loc(main)::: fonction n’a pas de déclaration, car elle est intégrée dans le langage. Si c’est le cas, la syntaxe de la déclaration pour se présente `:::no-loc(main):::` comme suit :

```cpp
int :::no-loc(main):::();
int :::no-loc(main):::(int :::no-loc(argc):::, :::no-loc(char)::: *:::no-loc(argv):::[], :::no-loc(char)::: *:::no-loc(envp):::[]);
```

**Spécifique à Microsoft**

Si vos fichiers sources utilisent Unicode :::no-loc(char)::: acters, vous pouvez utiliser `:::no-loc(wmain):::` , qui est la :::no-loc(char)::: version à acter étendue de `:::no-loc(main):::` . La syntaxe de déclaration pour `:::no-loc(wmain):::` est la suivante :

```cpp
int :::no-loc(wmain):::( );
int :::no-loc(wmain):::(int :::no-loc(argc):::, :::no-loc(wchar_t)::: *:::no-loc(argv):::[], :::no-loc(wchar_t)::: *:::no-loc(envp):::[]);
```

Vous pouvez également utiliser `:::no-loc(_tmain):::` , qui est défini dans t :::no-loc(char)::: . h. `:::no-loc(_tmain):::`se résout à `:::no-loc(main):::` , sauf si _UNICODE est défini. Dans ce cas, `:::no-loc(_tmain):::` est résolu à `:::no-loc(wmain):::`.

Si aucune valeur de retour n’est spécifiée, le compilateur fournit une valeur de retour de zéro. En guise d’alternative, les `:::no-loc(main):::` `:::no-loc(wmain):::` fonctions et peuvent être déclarées comme retournant **`:::no-loc(void):::`** (aucune valeur de retour). Si vous déclarez `:::no-loc(main):::` ou `:::no-loc(wmain):::` comme retournant **`:::no-loc(void):::`** , vous ne pouvez pas retourner :::no-loc(exit)::: de code au processus parent ou au système d’exploitation à l’aide d’une instruction [Return](../cpp/return-statement-in-program-termination-cpp.md) . Pour retourner un :::no-loc(exit)::: code lorsque `:::no-loc(main):::` ou `:::no-loc(wmain):::` est déclaré comme **`:::no-loc(void):::`** , vous devez utiliser la [:::no-loc(exit):::](../cpp/:::no-loc(exit):::-function.md) fonction.

**FIN spécifique à Microsoft**

## <a name="command-line-arguments"></a>Arguments de ligne de commande

Les arguments pour `:::no-loc(main):::` ou `:::no-loc(wmain):::` permettent l’analyse pratique de la ligne de commande des arguments et, éventuellement, l’accès aux variables d’environnement. Les types pour `:::no-loc(argc):::` et `:::no-loc(argv):::` sont définis par le langage. Les noms `:::no-loc(argc):::` , `:::no-loc(argv):::` et `:::no-loc(envp):::` sont traditionnels, mais vous pouvez les nommer comme vous le souhaitez.

```cpp
int :::no-loc(main):::( int :::no-loc(argc):::, :::no-loc(char):::* :::no-loc(argv):::[], :::no-loc(char):::* :::no-loc(envp):::[]);
int :::no-loc(wmain):::( int :::no-loc(argc):::, :::no-loc(wchar_t):::* :::no-loc(argv):::[], :::no-loc(wchar_t):::* :::no-loc(envp):::[]);
```

Les définitions d’argument sont les suivantes :

*:::no-loc(argc):::*<br/>
Entier qui contient le nombre d’arguments qui suivent dans *:::no-loc(argv):::* . Le *:::no-loc(argc):::* paramètre est toujours supérieur ou égal à 1.

*:::no-loc(argv):::*<br/>
Tableau de chaînes terminées par le caractère NULL qui représentent les arguments de ligne de commande entrés par l’utilisateur du programme. Par Convention, `:::no-loc(argv):::[0]` est la commande avec laquelle le programme est appelé, `:::no-loc(argv):::[1]` est le premier argument de ligne de commande, et ainsi de suite, jusqu’à `:::no-loc(argv):::[:::no-loc(argc):::]` , qui a toujours la valeur null. Pour plus d’informations sur la suppression du traitement de ligne de commande, consultez Personnalisation du traitement de la [ligne de commande](../cpp/customizing-cpp-command-line-processing.md) .

Le premier argument de ligne de commande est toujours `:::no-loc(argv):::[1]` et le dernier `:::no-loc(argv):::[:::no-loc(argc)::: - 1]`.

> [!NOTE]
> Par Convention, `:::no-loc(argv):::[0]` est la commande avec laquelle le programme est appelé. Toutefois, il est possible de générer un processus à l’aide [:::no-loc(CreateProcess):::](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) de et si vous utilisez à la fois le premier et le deuxième arguments (*LpApplicationName* et *lpCommandLine*), `:::no-loc(argv):::[0]` peut ne pas être le nom de l’exécutable ; utilisez [:::no-loc(GetModuleFileName):::](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) pour récupérer le nom de l’exécutable et son chemin d’accès complet.

**Spécifique à Microsoft**

*:::no-loc(envp):::*<br/>
Le *:::no-loc(envp):::* tableau, qui est une extension courante dans de nombreux systèmes UNIX, est utilisé dans Microsoft C++. Il s'agit d'un tableau de chaînes représentant les variables définies dans l'environnement de l'utilisateur. Ce tableau se termine par une entrée NULL. Il peut être déclaré comme un tableau de pointeurs vers **`:::no-loc(char):::`** ( `:::no-loc(char)::: *:::no-loc(envp):::[]` ) ou comme pointeur vers des pointeurs vers **`:::no-loc(char):::`** ( `:::no-loc(char)::: **:::no-loc(envp):::` ). Si votre programme utilise `:::no-loc(wmain):::` au lieu de `:::no-loc(main):::` , utilisez le **`:::no-loc(wchar_t):::`** type de données au lieu de **`:::no-loc(char):::`** . Le bloc d’environnement passé à `:::no-loc(main):::` et `:::no-loc(wmain):::` est une copie « figée » de l’environnement actuel. Si vous modifiez ultérieurement l’environnement via un appel à `putenv` ou `_wputenv` , l’environnement actuel (tel que retourné par `getenv` ou `_wgetenv` et `_environ` la `_wenviron` variable ou) sera modifié, mais le bloc pointé par :::no-loc(envp)::: ne changera pas. Pour plus d’informations sur la suppression du traitement de l’environnement, consultez Personnalisation du traitement de la [ligne de commande](../cpp/customizing-cpp-command-line-processing.md) . Cet argument est compatible ANSI en C, mais pas en C++.

**FIN spécifique à Microsoft**

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser les *:::no-loc(argc):::* arguments, *:::no-loc(argv):::* et *:::no-loc(envp):::* pour `:::no-loc(main):::` :

```cpp
// argument_definitions.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;
int :::no-loc(main):::( int :::no-loc(argc):::, :::no-loc(char)::: *:::no-loc(argv):::[], :::no-loc(char)::: *:::no-loc(envp):::[] ) {
    int iNumberLines = 0;    // Default is no line numbers.

    // If /n is passed to the .exe, display numbered listing
    // of environment variables.

    if ( (:::no-loc(argc)::: == 2) && _stricmp( :::no-loc(argv):::[1], "/n" ) == 0 )
         iNumberLines = 1;

    // Walk through list of strings until a NULL is encountered.
    for( int i = 0; :::no-loc(envp):::[i] != NULL; ++i ) {
        if( iNumberLines )
            cout << i << ": " << :::no-loc(envp):::[i] << "\n";
    }
}
```

## <a name="parsing-c-command-line-arguments"></a>Analyse des arguments de ligne de commande C++

**Spécifique à Microsoft**

Le code de démarrage Microsoft C/C++ utilise les règles suivantes lors de l’interprétation des arguments fournis sur la ligne de commande du système d’exploitation :

- Les arguments sont délimités par un espace blanc, qui peut être un espace ou une tabulation.

- Le signe insertion :::no-loc(char)::: acter (^) n’est pas reconnu comme un :::no-loc(char)::: séparateur ou un acter d’échappement. Le :::no-loc(char)::: acter est entièrement géré par l’analyseur de ligne de commande dans le système d’exploitation avant d’être passé au `:::no-loc(argv):::` tableau dans le programme.

- Une chaîne placée entre guillemets doubles ("*String*") est interprétée comme un argument unique, quel que soit l’espace blanc contenu dans. Une chaîne entre guillemets peut être incorporée dans un argument.

- Un guillemet double précédé d’une barre oblique inverse ( \\ ") est interprété comme un guillemet double littéral :::no-loc(char)::: acter (").

- Les barres obliques inverses sont interprétées littéralement, sauf si elles précèdent immédiatement un guillemet double.

- Si un nombre pair de barres obliques inverses est suivi d’un guillemet double, une barre oblique inverse est placée dans le `:::no-loc(argv):::` tableau pour chaque paire de barres obliques inverses, et le guillemet double est interprété comme un délimiteur de chaîne.

- Si un nombre impair de barres obliques inverses est suivi d’un guillemet double, une barre oblique inverse est placée dans le `:::no-loc(argv):::` tableau pour chaque paire de barres obliques inverses, et le guillemet double est « placé dans une séquence d’échappement » par la :::no-loc(main)::: barre oblique inverse, ce qui entraîne le placement d’un guillemet double littéral (") `:::no-loc(argv):::` .

### <a name="example"></a>Exemple

Le programme suivant illustre le mode de transmission des arguments de ligne de commande :

```cpp
// command_line_arguments.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
int :::no-loc(main):::( int :::no-loc(argc):::,      // Number of strings in array :::no-loc(argv):::
          :::no-loc(char)::: *:::no-loc(argv):::[],   // Array of command-line argument strings
          :::no-loc(char)::: *:::no-loc(envp):::[] )  // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    cout << "\nCommand-line arguments:\n";
    for( count = 0; count < :::no-loc(argc):::; count++ )
         cout << "  :::no-loc(argv):::[" << count << "]   "
                << :::no-loc(argv):::[count] << "\n";
}
```

Le tableau suivant présente des exemples d’entrée et de sortie attendue, illustrant les règles de la liste précédente.

### <a name="results-of-parsing-command-lines"></a>Résultats de l’analyse des lignes de commande

|Entrée sur la ligne de commande|:::no-loc(argv):::[1]|:::no-loc(argv):::[2]|:::no-loc(argv):::1,3|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**FIN spécifique à Microsoft**

## <a name="wildcard-expansion"></a>Développement des caractères génériques

**Spécifique à Microsoft**

Vous pouvez utiliser des caractères génériques (le point d'interrogation (?) et l'astérisque (*)) pour spécifier des arguments de nom de fichier et de chemin d'accès sur la ligne de commande.

Les arguments de ligne de commande sont gérés par une routine appelée `_set:::no-loc(argv):::` (ou `_wset:::no-loc(argv):::` dans l' :::no-loc(char)::: environnement acter), qui, par défaut, ne développe pas les caractères génériques en chaînes séparées dans le `:::no-loc(argv):::` tableau de chaînes. Pour plus d’informations sur l’activation de l’extension de caractères génériques, consultez [extension des arguments génériques](../c-language/expanding-wildcard-arguments.md).

**FIN spécifique à Microsoft**

## <a name="customizing-c-command-line-processing"></a>Personnalisation du traitement de ligne de commande C++

**Spécifique à Microsoft**

Si votre programme ne prend pas d’arguments de ligne de commande, vous pouvez économiser une petite quantité d’espace en supprimant l’utilisation de la routine de bibliothèque qui exécute le traitement de ligne de commande. Cette routine est appelée `_set:::no-loc(argv):::` et est décrite dans [extension des caractères génériques](../cpp/wildcard-expansion.md). Pour supprimer son utilisation, définissez une routine qui ne fait rien dans le fichier contenant la `:::no-loc(main):::` fonction et nommez-la `_set:::no-loc(argv):::` . L’appel à `_set:::no-loc(argv):::` est ensuite satisfait par votre définition de `_set:::no-loc(argv):::` et la version de la bibliothèque n’est pas chargée.

De même, si vous n’accédez jamais à la table d’environnement via l' `:::no-loc(envp):::` argument, vous pouvez fournir votre propre routine vide à utiliser à la place de `_set:::no-loc(envp):::` , la routine de traitement de l’environnement. À l’instar de la `_set:::no-loc(argv):::` fonction, `_set:::no-loc(envp):::` doit être déclaré comme ** :::no-loc(extern)::: « C »**.

Votre programme peut effectuer des appels à `spawn` la `exec` famille ou des routines dans la bibliothèque Runtime C. Si c’est le cas, vous ne devez pas supprimer la routine de traitement de l’environnement, car cette routine est utilisée pour passer un environnement du processus parent au processus enfant.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Concepts de base](../cpp/basic-concepts-cpp.md)
