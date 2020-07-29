---
title: Description des arguments
ms.date: 11/04/2016
helpviewer_keywords:
- envp argument
- main function, syntax
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 91c2cbe3-9aca-4277-afa1-6137eb8fb704
ms.openlocfilehash: dd973c96c9056f6156976698dfc3695b00ebbbb7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200866"
---
# <a name="argument-description"></a>Description des arguments

Le paramètre `argc` dans les fonctions **main** et **wmain** est un entier spécifiant le nombre d’arguments passés au programme depuis la ligne de commande. Le nom du programme étant considéré comme un argument, la valeur `argc` est d'au moins un.

## <a name="remarks"></a>Notes

Le paramètre `argv` est un tableau de pointeurs vers des chaînes terminées par le caractère NULL qui représente les arguments de programme. Chaque élément du tableau pointe vers une représentation sous forme de chaîne d’un argument passé à **main** (ou **wmain**). (Pour plus d’informations sur les tableaux, consultez [déclarations de tableau](../c-language/array-declarations.md).) Le `argv` paramètre peut être déclaré comme un tableau de pointeurs vers le type **`char`** ( `char *argv[]` ) ou comme pointeur vers des pointeurs vers le type **`char`** ( `char **argv` ). Pour **wmain**, le `argv` paramètre peut être déclaré comme un tableau de pointeurs en type **`wchar_t`** ( `wchar_t *argv[]` ) ou comme pointeur vers des pointeurs vers le type **`wchar_t`** ( `wchar_t **argv` ).

Par convention, `argv`**[0]** est la commande avec laquelle le programme est appelé.  Toutefois, il est possible de générer un processus à l’aide de [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) et si vous utilisez à la fois le premier et le deuxième argument ( `lpApplicationName` et `lpCommandLine` ), `argv` **[0]** ne peut pas être le nom de l’exécutable ; utilisez [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) pour récupérer le nom de l’exécutable.

Le dernier pointeur (`argv[argc]`) est **NULL**. (Consultez [getenv](../c-runtime-library/reference/getenv-wgetenv.md) dans la *Référence de la bibliothèque runtime* pour une connaître autre méthode pour obtenir des informations de variable d'environnement.)

**Spécifique à Microsoft**

Le paramètre `envp` est un pointeur vers un tableau de chaînes terminées par le caractère NULL qui représentent les valeurs définies dans les variables d'environnement de l'utilisateur. Le `envp` paramètre peut être déclaré comme tableau de pointeurs vers **`char`** ( `char *envp[]` ) ou comme pointeur vers des pointeurs vers **`char`** ( `char **envp` ). Dans une fonction **wmain** , le `envp` paramètre peut être déclaré comme tableau de pointeurs vers **`wchar_t`** ( `wchar_t *envp[]` ) ou comme pointeur vers des pointeurs vers **`wchar_t`** ( `wchar_t **envp` ). La fin du tableau est affichée par un pointeur **NULL** \*. Notez que le bloc environnement passé à **main** ou **wmain** est une copie « figée » de l'environnement actuel. Si vous modifiez par la suite l’environnement via un appel à _**putenv** ou `_wputenv` , l’environnement actuel (tel que retourné par `getenv` / `_wgetenv` et les `_environ` `_wenviron` variables ou) sera modifié, mais le bloc pointé par `envp` ne changera pas. Le paramètre `envp` est compatible ANSI en C, mais pas en C++.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Fonction main et exécution du programme](../c-language/main-function-and-program-execution.md)
