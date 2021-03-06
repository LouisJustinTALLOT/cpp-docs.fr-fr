---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4221'
title: Avertissement des outils Éditeur de liens LNK4221
ms.date: 08/19/2019
f1_keywords:
- LNK4221
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
ms.openlocfilehash: d7aee041536afc1da0c4fd8a6e520ceb5e99e57a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222630"
---
# <a name="linker-tools-warning-lnk4221"></a>Avertissement des outils Éditeur de liens LNK4221

Ce fichier objet ne définit aucun symbole public précédemment non défini, donc il ne sera pas utilisé par une opération de liaison qui consomme cette bibliothèque

Considérez les deux extraits de code suivants.

```cpp
// a.cpp
#include <atlbase.h>
```

```cpp
// b.cpp
#include <atlbase.h>
int function()
{
   return 0;
}
```

Pour compiler les fichiers et créer deux fichiers objets, exécutez **cl/c a. cpp b. cpp** à l’invite de commandes. Si vous liez les fichiers objets en exécutant **link/lib/out : test. lib a. obj b. obj**, vous recevrez l’avertissement LNK4221. Si vous liez les objets en exécutant **link/lib/out : test. lib b. obj a. obj**, vous ne recevrez pas d’avertissement.

Aucun avertissement n’est émis dans le deuxième scénario, car l’éditeur de liens fonctionne selon une méthode LIFO (dernier entré, premier sorti). Dans le premier scénario, b. obj est traité avant un. objet un. obj n’a aucun nouveau symbole à ajouter. En demandant à l’éditeur de liens de traiter d’abord un. obj, vous pouvez éviter l’avertissement.

::: moniker range=">=msvc-160"

Cette erreur est souvent due au fait que deux fichiers sources spécifient l’option [/Yc (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md) avec le même nom de fichier d’en-tête spécifié dans le champ d' **en-tête précompilé** . L’une des causes courantes de ce problème concerne *pch. h* , car, par défaut, *pch. cpp* comprend *pch. h* et n’ajoute pas de nouveaux symboles. Si un autre fichier source comprend *pch. h* avec **/Yc** et que le fichier. obj associé est traité avant pch. obj, l’éditeur de liens lèvera LNK4221.

::: moniker-end

::: moniker range="<=msvc-150"

Cette erreur est souvent due au fait que deux fichiers sources spécifient l’option [/Yc (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md) avec le même nom de fichier d’en-tête spécifié dans le champ d' **en-tête précompilé** . L’une des causes courantes de ce problème concerne *stdafx. h* , car, par défaut, *stdafx. cpp* comprend *stdafx. h* et n’ajoute pas de nouveaux symboles. Si un autre fichier source comprend *stdafx. h* avec **/Yc** et que le fichier. obj associé est traité avant stdafx. obj, l’éditeur de liens lèvera LNK4221.

::: moniker-end

Une façon de résoudre ce problème consiste à s’assurer que pour chaque en-tête précompilé, il n’y a qu’un seul fichier source qui l’inclut avec **/Yc**. Tous les autres fichiers sources doivent utiliser des en-têtes précompilés. Pour plus d’informations sur la modification de ce paramètre, consultez [/Yu (utiliser un fichier d’en-tête précompilé)](../../build/reference/yu-use-precompiled-header-file.md).
