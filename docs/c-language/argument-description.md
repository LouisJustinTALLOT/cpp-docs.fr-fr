---
title: Description des arguments | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- envp argument
- main function, syntax
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 91c2cbe3-9aca-4277-afa1-6137eb8fb704
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b8508b5a14e67092339a456f5b85f78d17906a5
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082538"
---
# <a name="argument-description"></a>Description des arguments

Le paramètre `argc` dans les fonctions **main** et **wmain** est un entier spécifiant le nombre d’arguments passés au programme depuis la ligne de commande. Le nom du programme étant considéré comme un argument, la valeur `argc` est d'au moins un.

## <a name="remarks"></a>Notes

Le paramètre `argv` est un tableau de pointeurs vers des chaînes terminées par le caractère NULL qui représente les arguments de programme. Chaque élément du tableau pointe vers une représentation sous forme de chaîne d’un argument passé à **main** (ou **wmain**). (Pour plus d'informations sur les tableaux, consultez [Déclarations de tableau](../c-language/array-declarations.md).) Le paramètre `argv` peut être déclaré soit comme tableau de pointeurs en type `char` (`char *argv[]`) soit comme pointeur vers des pointeurs en type `char` (`char **argv`). Pour **wmain**, le paramètre `argv` peut être déclaré soit comme tableau de pointeurs en type `wchar_t` (`wchar_t *argv[]`) soit comme pointeur vers des pointeurs en type `wchar_t` (`wchar_t **argv`).

Par convention, `argv`**[0]** est la commande avec laquelle le programme est appelé.  Toutefois, il est possible de générer un processus utilisant [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) et si vous utilisez à la fois le premier et le deuxième argument (`lpApplicationName` et `lpCommandLine`), `argv`**[0]** peut ne pas être le nom exécutable. Utilisez [GetModuleFileName](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulefilenamea) pour récupérer le nom exécutable.

Le dernier pointeur (`argv[argc]`) est **NULL**. (Consultez [getenv](../c-runtime-library/reference/getenv-wgetenv.md) dans la *Référence de la bibliothèque runtime* pour une connaître autre méthode pour obtenir des informations de variable d'environnement.)

**Section spécifique à Microsoft**

Le paramètre `envp` est un pointeur vers un tableau de chaînes terminées par le caractère NULL qui représentent les valeurs définies dans les variables d'environnement de l'utilisateur. Le paramètre `envp` peut être déclaré comme tableau de pointeurs en type `char` (`char *envp[]`) ou comme pointeur vers des pointeurs en type `char` (`char **envp`). Dans une fonction **wmain**, le paramètre `envp` peut être déclaré comme tableau de pointeurs vers `wchar_t` (`wchar_t *envp[]`) ou comme pointeur vers des pointeurs en `wchar_t` (`wchar_t **envp`). La fin du tableau est affichée par un pointeur **NULL** \*. Notez que le bloc environnement passé à **main** ou **wmain** est une copie « figée » de l'environnement actuel. Si vous modifiez ultérieurement l'environnement via un appel à _**putenv** ou `_wputenv`, l'environnement actuel (tel que retourné par `getenv`/`_wgetenv` et les variables `_environ` ou `_wenviron`) est modifié, mais pas le bloc dirigé vers `envp`. Le paramètre `envp` est compatible ANSI en C, mais pas en C++.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Fonction main et exécution du programme](../c-language/main-function-and-program-execution.md)