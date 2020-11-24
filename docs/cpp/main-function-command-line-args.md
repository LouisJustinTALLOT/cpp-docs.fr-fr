---
title: '`main` fonction et arguments de ligne de commande (C++)'
description: La `main` fonction est le point d’entrée d’un programme C++.
ms.date: 11/19/2020
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
ms.openlocfilehash: 8a5ed43bdacf5d9d6dd2cbc5d1c56783c82b8e9a
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483215"
---
# <a name="no-locmain-function-and-command-line-arguments"></a>`main` arguments de ligne de commande et de fonction

Tous les programmes C++ doivent avoir une `main` fonction. Si vous essayez de compiler un programme C++ sans `main` fonction, le compilateur génère une erreur. (Les bibliothèques de liens dynamiques et les static bibliothèques n’ont pas de `main` fonction.) La `main` fonction est l’emplacement où votre code source commence à s’exécuter, mais avant qu’un programme n’entre dans la `main` fonction, tous les static membres de classe sans initialiseurs explicites sont définis à zéro. Dans Microsoft C++, static les objets globaux sont également initialisés avant l’entrée dans `main` . Plusieurs restrictions s’appliquent à la `main` fonction qui ne s’applique pas à d’autres fonctions C++. La `main` fonction :

- Ne peut pas être surchargé (consultez [surcharge de fonction](./function-overloading.md)).
- Ne peut pas être déclaré comme **`inline`** .
- Ne peut pas être déclaré comme **`static`** .
- L’adresse ne peut pas être prise.
- Ne peut pas être appelé à partir de votre programme.

## <a name="the-no-locmain-function-signature"></a>Signature de la `main` fonction

La `main` fonction n’a pas de déclaration, car elle est intégrée dans le langage. Si c’est le cas, la syntaxe de la déclaration pour se présente `main` comme suit :

```cpp
int main();
int main(int argc, char *argv[]);
```

Si aucune valeur de retour n’est spécifiée dans `main` , le compilateur fournit une valeur de retour de zéro.

## <a name="standard-command-line-arguments"></a>Arguments de ligne de commande standard

Les arguments pour `main` autorisent l’analyse pratique de la ligne de commande des arguments. Les types pour `argc` et `argv` sont définis par le langage. Les noms `argc` et `argv` sont traditionnels, mais vous pouvez les nommer comme vous le souhaitez.

Les définitions d’argument sont les suivantes :

*`argc`*\
Entier qui contient le nombre d’arguments qui suivent dans *argv* . Le *argc* paramètre est toujours supérieur ou égal à 1.

*`argv`*\
Tableau de chaînes terminées par le caractère NULL qui représentent les arguments de ligne de commande entrés par l’utilisateur du programme. Par Convention, `argv[0]` est la commande avec laquelle le programme est appelé. `argv[1]` est le premier argument de ligne de commande. Le dernier argument de la ligne de commande est `argv[argc - 1]` , et `argv[argc]` est toujours null.

Pour plus d’informations sur la façon de supprimer le traitement de ligne de commande, consultez [personnaliser le traitement de ligne de commande C++](#customize).

> [!NOTE]
> Par Convention, `argv[0]` est le nom de fichier du programme. Toutefois, sur Windows, il est possible de générer un processus à l’aide de [`CreateProcess`](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) . Si vous utilisez à la fois le premier et le deuxième argument ( *`lpApplicationName`* et *`lpCommandLine`* ), `argv[0]` peut ne pas être le nom de l’exécutable. Vous pouvez utiliser [`GetModuleFileName`](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) pour récupérer le nom de l’exécutable et son chemin d’accès complet.

## <a name="microsoft-specific-extensions"></a>Extensions spécifiques à Microsoft

Les sections suivantes décrivent le comportement spécifique à Microsoft.

## <a name="the-no-locwmain-function-and-no-loc_tmain-macro"></a>La `wmain` fonction et la `_tmain` macro

Si vous concevez votre code source pour utiliser Unicode char acters, vous pouvez utiliser le `wmain` point d’entrée spécifique à Microsoft, qui est la char version à acter étendue de `main` . Voici la syntaxe de déclaration effective pour `wmain` :

```cpp
int wmain();
int wmain(int argc, wchar_t *argv[]);
```

Vous pouvez également utiliser le spécifique à Microsoft `_tmain` , qui est une macro de préprocesseur définie dans *`tchar.h`* . `_tmain` se résout à `main` , sauf si `_UNICODE` est défini. Dans ce cas, `_tmain` est résolu à `wmain`. La `_tmain` macro et les autres macros qui commencent par `_t` sont utiles pour le code qui doit générer des versions distinctes pour les jeux acter étroits et larges char . Pour plus d’informations, consultez [utilisation de mappages de texte générique](../c-runtime-library/using-generic-text-mappings.md).

## <a name="returning-no-locvoid-from-no-locmain"></a>Retourner `void` de main

En tant qu’extension Microsoft, `main` les `wmain` fonctions et peuvent être déclarées comme retournant **`void`** (aucune valeur de retour). Cette extension est également disponible dans d’autres compilateurs, mais son utilisation n’est pas recommandée. Elle est disponible pour la symétrie lorsque `main` ne retourne pas de valeur.

Si vous déclarez `main` ou `wmain` comme retournant **`void`** , vous ne pouvez pas retourner exit de code au processus parent ou au système d’exploitation à l’aide d’une [`return`](./program-termination.md) instruction. Pour retourner un exit code lorsque `main` ou `wmain` est déclaré comme **`void`** , vous devez utiliser la [`exit`](./program-termination.md) fonction.

## <a name="the-no-locenvp-command-line-argument"></a>L' `envp` argument de ligne de commande

Les `main` `wmain` signatures ou autorisent une extension facultative spécifique à Microsoft pour l’accès aux variables d’environnement. Cette extension est également courante dans d’autres compilateurs pour les systèmes Windows et UNIX. Le nom *`envp`* est traditionnel, mais vous pouvez nommer le paramètre d’environnement comme vous le souhaitez. Voici les déclarations effectives pour les listes d’arguments qui incluent le paramètre d’environnement :

```cpp
int main(int argc, char* argv[], char* envp[]);
int wmain(int argc, wchar_t* argv[], wchar_t* envp[]);
```

*`envp`*\
Le *`envp`* paramètre facultatif est un tableau de chaînes représentant les variables définies dans l’environnement de l’utilisateur. Ce tableau se termine par une entrée NULL. Il peut être déclaré comme un tableau de pointeurs vers **`char`** ( `char *envp[]` ) ou comme pointeur vers des pointeurs vers **`char`** ( `char **envp` ). Si votre programme utilise `wmain` au lieu de `main` , utilisez le **`wchar_t`** type de données au lieu de **`char`** .

Le bloc d’environnement passé à `main` et `wmain` est une copie « figée » de l’environnement actuel. Si vous modifiez ultérieurement l’environnement en effectuant un appel à `putenv` ou `_wputenv` , l’environnement actuel (tel que retourné par `getenv` ou `_wgetenv` et la `_environ`  `_wenviron` variable ou) sera modifié, mais le bloc pointé par *`envp`* ne changera pas. Pour plus d’informations sur la façon de supprimer le traitement de l’environnement, consultez [personnaliser le traitement de ligne de commande C++](#customize). L' *`envp`* argument est compatible avec la norme C89, mais pas avec les normes C++.

### <a name="example-arguments-to-no-locmain"></a>Exemples d’arguments pour `main`

L’exemple suivant montre comment utiliser les *`argc`* arguments, *`argv`* et *`envp`* pour `main` :

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

Les règles d’analyse de la ligne de commande utilisées par le code Microsoft C/C++ sont spécifiques à Microsoft. Le code de démarrage du runtime utilise ces règles lors de l’interprétation des arguments fournis sur la ligne de commande du système d’exploitation :

- Les arguments sont délimités par un espace blanc, qui peut être un espace ou une tabulation.

- Le premier argument ( `argv[0]` ) est traité de façon spéciale. Elle représente le nom du programme. Comme il doit s’agir d’un nom de chemin d’accès valide, les pièces entourées par des guillemets doubles ( **`"`** ) sont autorisées. Les guillemets doubles ne sont pas inclus dans la `argv[0]` sortie. Les parties entourées par des guillemets doubles empêchent l’interprétation d’un espace ou d’un onglet char acter comme la fin de l’argument. Les règles ultérieures de cette liste ne s’appliquent pas.

- Une chaîne entourée de guillemets doubles est interprétée comme un argument unique, qui peut contenir des espaces blancs char acters. Une chaîne entre guillemets peut être incorporée dans un argument. Le signe insertion ( **`^`** ) n’est pas reconnu comme un char acter ou un délimiteur d’échappement. Dans une chaîne entre guillemets, une paire de guillemets doubles est interprétée comme un guillemet double placé dans une séquence d’échappement. Si la ligne de commande se termine avant qu’un guillemet double fermant soit trouvé, tous les char acters lus jusqu’à présent sont générés comme étant le dernier argument.

- Un guillemet double précédé d’une barre oblique inverse ( **`\"`** ) est interprété comme un guillemet double littéral ( **`"`** ).

- Les barres obliques inverses sont interprétées littéralement, sauf si elles précèdent immédiatement un guillemet double.

- Si un nombre pair de barres obliques inverses est suivi d’un guillemet double, une barre oblique inverse ( **`\`** ) est placée dans le `argv` tableau pour chaque paire de barres obliques inverses ( **`\\`** ) et le guillemet double ( **`"`** ) est interprété comme un délimiteur de chaîne.

- Si un nombre impair de barres obliques inverses est suivi d’un guillemet double, une barre oblique inverse ( **`\`** ) est placée dans le `argv` tableau pour chaque paire de barres obliques inverses ( **`\\`** ). Le guillemet double est interprété comme une séquence d’échappement par la main barre oblique inverse, ce qui entraîne la mise en place d’un guillemet double littéral ( **`"`** ) `argv` .

### <a name="example-of-command-line-argument-parsing"></a>Exemple d’analyse d’argument de ligne de commande

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

### <a name="results-of-parsing-command-lines"></a>Résultats de l’analyse des lignes de commande

Le tableau suivant présente des exemples d’entrée et de sortie attendue, illustrant les règles de la liste précédente.

| Entrée de ligne de commande | argv[1] | argv[2] | argv1,3 |
|--|--|--|--|
| `"abc" d e` | `abc` | `d` | `e` |
| `a\\b d"e f"g h` | `a\\b` | `de fg` | `h` |
| `a\\\"b c d` | `a\"b` | `c` | `d` |
| `a\\\\"b c" d e` | `a\\b c` | `d` | `e` |
| `a"b"" c d` | `ab" c d` |  |  |

## <a name="wildcard-expansion"></a>Développement des caractères génériques

Le compilateur Microsoft vous permet éventuellement d’utiliser des acters *génériques* char , le point d’interrogation ( **`?`** ) et l’astérisque ( **`*`** ), pour spécifier des arguments de nom de fichier et de chemin d’accès sur la ligne de commande.

Les arguments de ligne de commande sont gérés par une routine interne dans le code de démarrage du runtime, qui, par défaut, ne développe pas les caractères génériques en chaînes séparées dans le `argv` tableau de chaînes. Vous pouvez activer l’extension de caractères génériques en incluant le *`setargv.obj`* fichier ( *`wsetargv.obj`* fichier pour `wmain` ) dans les **`/link`** Options du compilateur ou la **`LINK`** ligne de commande.

Pour plus d’informations sur les options de l’éditeur de liens de démarrage du runtime, consultez [options de liaison](../c-runtime-library/link-options.md).

## <a name="customize-c-command-line-processing"></a><a name="customize"/> Personnaliser le traitement de ligne de commande C++

Si votre programme ne prend pas d’arguments de ligne de commande, vous pouvez supprimer la routine de traitement de ligne de commande pour économiser une petite quantité d’espace. Pour supprimer son utilisation, incluez le *`noarg.obj`* fichier (pour `main` et `wmain` ) dans les **`/link`** Options du compilateur ou la **`LINK`** ligne de commande.

De même, si vous n’accédez jamais à la table d’environnement via l' *`envp`* argument, vous pouvez supprimer la routine de traitement de l’environnement interne. Pour supprimer son utilisation, incluez le *`noenv.obj`* fichier (pour `main` et `wmain` ) dans les **`/link`** Options du compilateur ou la **`LINK`** ligne de commande.

Votre programme peut effectuer des appels à `spawn` la `exec` famille ou des routines dans la bibliothèque Runtime C. Si c’est le cas, vous ne devez pas supprimer la routine de traitement de l’environnement, car elle est utilisée pour passer un environnement du processus parent au processus enfant.

## <a name="see-also"></a>Voir aussi

[Concepts de base](../cpp/basic-concepts-cpp.md)
