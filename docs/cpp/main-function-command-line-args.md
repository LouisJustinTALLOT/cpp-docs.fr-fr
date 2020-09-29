---
title: main fonction et arguments de ligne de commande (C++)
description: La main fonction est le point d’entrée d’un programme C++.
ms.date: 01/15/2019
ms.assetid: c6568ee6-40ab-4ae8-aa44-c99e232f64ac
no-loc:
- main
- wmain
- inline
- static
- _tmain
- void
- exit
- argc
- argv
- envp
- CreateProcess
- GetModuleFileName
- char
- wchar_t
- extern
ms.openlocfilehash: b27668c3c7ce77e4369af144bb8be4efb695e522
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499807"
---
# <a name="no-locmain-function-and-command-line-arguments"></a>main arguments de ligne de commande et de fonction

Tous les programmes C++ doivent avoir une `main` fonction. Si vous essayez de compiler un projet C++ *. exe* sans main fonction, le compilateur génère une erreur. (Les bibliothèques de liens dynamiques et les static bibliothèques n’ont pas de `main` fonction.) La `main` fonction est l’emplacement où votre code source commence à s’exécuter, mais avant qu’un programme n’entre dans la `main` fonction, tous les static membres de classe sans initialiseurs explicites sont définis à zéro. Dans Microsoft C++, static les objets globaux sont également initialisés avant l’entrée dans `main` . Plusieurs restrictions s’appliquent à la `main` fonction qui ne s’applique pas à d’autres fonctions C++. La `main` fonction :

- Ne peut pas être surchargé (consultez [surcharge de fonction](function-overloading.md)).
- Ne peut pas être déclaré comme **`inline`** .
- Ne peut pas être déclaré comme **`static`** .
- son adresse ne peut pas être prise.
- Ne peut pas être appelé.

La main fonction n’a pas de déclaration, car elle est intégrée dans le langage. Si c’est le cas, la syntaxe de la déclaration pour se présente `main` comme suit :

```cpp
int main();
int main(int argc, char *argv[], char *envp[]);
```

**Spécifique à Microsoft**

Si vos fichiers sources utilisent Unicode char acters, vous pouvez utiliser `wmain` , qui est la char version à acter étendue de `main` . La syntaxe de déclaration pour `wmain` est la suivante :

```cpp
int wmain( );
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

Vous pouvez également utiliser `_tmain` , qui est défini dans t char . h. `_tmain` se résout à `main` , sauf si _UNICODE est défini. Dans ce cas, `_tmain` est résolu à `wmain`.

Si aucune valeur de retour n’est spécifiée, le compilateur fournit une valeur de retour de zéro. En guise d’alternative, les `main` `wmain` fonctions et peuvent être déclarées comme retournant **`void`** (aucune valeur de retour). Si vous déclarez `main` ou `wmain` comme retournant **`void`** , vous ne pouvez pas retourner exit de code au processus parent ou au système d’exploitation à l’aide d’une instruction [Return](./program-termination.md) . Pour retourner un exit code lorsque `main` ou `wmain` est déclaré comme **`void`** , vous devez utiliser la [exit](./program-termination.md) fonction.

**FIN spécifique à Microsoft**

## <a name="command-line-arguments"></a>Arguments de ligne de commande

Les arguments pour `main` ou `wmain` permettent l’analyse pratique de la ligne de commande des arguments et, éventuellement, l’accès aux variables d’environnement. Les types pour `argc` et `argv` sont définis par le langage. Les noms `argc` , `argv` et `envp` sont traditionnels, mais vous pouvez les nommer comme vous le souhaitez.

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

Les définitions d’argument sont les suivantes :

*argc*<br/>
Entier qui contient le nombre d’arguments qui suivent dans *argv* . Le *argc* paramètre est toujours supérieur ou égal à 1.

*argv*<br/>
Tableau de chaînes terminées par le caractère NULL qui représentent les arguments de ligne de commande entrés par l’utilisateur du programme. Par Convention, `argv[0]` est la commande avec laquelle le programme est appelé, `argv[1]` est le premier argument de ligne de commande, et ainsi de suite, jusqu’à `argv[argc]` , qui a toujours la valeur null. Pour plus d’informations sur la suppression du traitement de ligne de commande, consultez Personnalisation du traitement de la [ligne de commande]() .

Le premier argument de ligne de commande est toujours `argv[1]` et le dernier `argv[argc - 1]`.

> [!NOTE]
> Par Convention, `argv[0]` est la commande avec laquelle le programme est appelé. Toutefois, il est possible de générer un processus à l’aide [CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) de et si vous utilisez à la fois le premier et le deuxième arguments (*LpApplicationName* et *lpCommandLine*), `argv[0]` peut ne pas être le nom de l’exécutable ; utilisez [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) pour récupérer le nom de l’exécutable et son chemin d’accès complet.

**Spécifique à Microsoft**

*envp*<br/>
Le *envp* tableau, qui est une extension courante dans de nombreux systèmes UNIX, est utilisé dans Microsoft C++. Il s'agit d'un tableau de chaînes représentant les variables définies dans l'environnement de l'utilisateur. Ce tableau se termine par une entrée NULL. Il peut être déclaré comme un tableau de pointeurs vers **`char`** ( `char *envp[]` ) ou comme pointeur vers des pointeurs vers **`char`** ( `char **envp` ). Si votre programme utilise `wmain` au lieu de `main` , utilisez le **`wchar_t`** type de données au lieu de **`char`** . Le bloc d’environnement passé à `main` et `wmain` est une copie « figée » de l’environnement actuel. Si vous modifiez ultérieurement l’environnement via un appel à `putenv` ou `_wputenv` , l’environnement actuel (tel que retourné par `getenv` ou `_wgetenv` et `_environ` la  `_wenviron` variable ou) sera modifié, mais le bloc pointé par envp ne changera pas. Pour plus d’informations sur la suppression du traitement de l’environnement, consultez Personnalisation du traitement de la [ligne de commande]() . Cet argument est compatible ANSI en C, mais pas en C++.

**FIN spécifique à Microsoft**

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser les *argc* arguments, *argv* et *envp* pour `main` :

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

## <a name="parsing-c-command-line-arguments"></a>Analyse des arguments de ligne de commande C++

**Spécifique à Microsoft**

Le code de démarrage Microsoft C/C++ utilise les règles suivantes lors de l’interprétation des arguments fournis sur la ligne de commande du système d’exploitation :

- Les arguments sont délimités par un espace blanc, qui peut être un espace ou une tabulation.

- Le signe insertion char acter (^) n’est pas reconnu comme un char séparateur ou un acter d’échappement. Le char acter est entièrement géré par l’analyseur de ligne de commande dans le système d’exploitation avant d’être passé au `argv` tableau dans le programme.

- Une chaîne placée entre guillemets doubles ("*String*") est interprétée comme un argument unique, quel que soit l’espace blanc contenu dans. Une chaîne entre guillemets peut être incorporée dans un argument.

- Un guillemet double précédé d’une barre oblique inverse ( \\ ") est interprété comme un guillemet double littéral char acter (").

- Les barres obliques inverses sont interprétées littéralement, sauf si elles précèdent immédiatement un guillemet double.

- Si un nombre pair de barres obliques inverses est suivi d’un guillemet double, une barre oblique inverse est placée dans le `argv` tableau pour chaque paire de barres obliques inverses, et le guillemet double est interprété comme un délimiteur de chaîne.

- Si un nombre impair de barres obliques inverses est suivi d’un guillemet double, une barre oblique inverse est placée dans le `argv` tableau pour chaque paire de barres obliques inverses, et le guillemet double est « placé dans une séquence d’échappement » par la main barre oblique inverse, ce qui entraîne le placement d’un guillemet double littéral (") `argv` .

### <a name="example"></a>Exemple

Le programme suivant illustre le mode de transmission des arguments de ligne de commande :

```cpp
// command_line_arguments.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
int main( int argc,      // Number of strings in array argv
          char *argv[],   // Array of command-line argument strings
          char *envp[] )  // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    cout << "\nCommand-line arguments:\n";
    for( count = 0; count < argc; count++ )
         cout << "  argv[" << count << "]   "
                << argv[count] << "\n";
}
```

Le tableau suivant présente des exemples d’entrée et de sortie attendue, illustrant les règles de la liste précédente.

### <a name="results-of-parsing-command-lines"></a>Résultats de l’analyse des lignes de commande

|Entrée sur la ligne de commande|argv[1]|argv[2]|argv1,3|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**FIN spécifique à Microsoft**

## <a name="wildcard-expansion"></a>Développement des caractères génériques

**Spécifique à Microsoft**

Vous pouvez utiliser des caractères génériques (le point d'interrogation (?) et l'astérisque (*)) pour spécifier des arguments de nom de fichier et de chemin d'accès sur la ligne de commande.

Les arguments de ligne de commande sont gérés par une routine appelée `_setargv` (ou `_wsetargv` dans l' char environnement acter), qui, par défaut, ne développe pas les caractères génériques en chaînes séparées dans le `argv` tableau de chaînes. Pour plus d’informations sur l’activation de l’extension de caractères génériques, consultez [extension des arguments génériques](../c-language/expanding-wildcard-arguments.md).

**FIN spécifique à Microsoft**

## <a name="customizing-c-command-line-processing"></a>Personnalisation du traitement de ligne de commande C++

**Spécifique à Microsoft**

Si votre programme ne prend pas d’arguments de ligne de commande, vous pouvez économiser une petite quantité d’espace en supprimant l’utilisation de la routine de bibliothèque qui exécute le traitement de ligne de commande. Cette routine est appelée `_setargv` et est décrite dans [extension des caractères génériques](). Pour supprimer son utilisation, définissez une routine qui ne fait rien dans le fichier contenant la `main` fonction et nommez-la `_setargv` . L’appel à `_setargv` est ensuite satisfait par votre définition de `_setargv` et la version de la bibliothèque n’est pas chargée.

De même, si vous n’accédez jamais à la table d’environnement via l' `envp` argument, vous pouvez fournir votre propre routine vide à utiliser à la place de `_setenvp` , la routine de traitement de l’environnement. À l’instar de la `_setargv` fonction, `_setenvp` doit être déclaré comme ** extern « C »**.

Votre programme peut effectuer des appels à `spawn` la `exec` famille ou des routines dans la bibliothèque Runtime C. Si c’est le cas, vous ne devez pas supprimer la routine de traitement de l’environnement, car cette routine est utilisée pour passer un environnement du processus parent au processus enfant.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Concepts de base](../cpp/basic-concepts-cpp.md)
