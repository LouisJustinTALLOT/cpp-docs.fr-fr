---
title: Avertissement des outils Éditeur de liens LNK4221
ms.date: 11/04/2016
f1_keywords:
- LNK4221
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
ms.openlocfilehash: b44ba8f0b88beda3e81d9baf59e5348ad4949b01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460968"
---
# <a name="linker-tools-warning-lnk4221"></a>Avertissement des outils Éditeur de liens LNK4221

Ce fichier objet ne définit pas de symboles publics jusqu’ici non définis, donc il ne sera pas utilisé par une opération de liaison qui utilise cette bibliothèque

Prendre en compte les extraits de deux code suivants.

```
// a.cpp
#include <atlbase.h>
```

```
// b.cpp
#include <atlbase.h>
int function()
{
   return 0;
}

```

Pour compiler les fichiers et créer deux fichiers objets, exécutez **cl /c a.cpp b.cpp** à une invite de commandes. Si vous liez les fichiers objets en exécutant **lier/lib /out:test.lib a.obj b.obj**, vous recevrez l’avertissement LNK4221. Si vous liez les objets en exécutant **lier/lib /out:test.lib b.obj a.obj**, vous ne recevrez pas d’un avertissement.

Aucun avertissement n’est émis dans le second scénario, car l’éditeur de liens fonctionne de façon dernier entré premier sorti (LIFO). Dans le premier scénario, b.obj est traité avant a.obj, et a.obj n’a aucun nouveau symbole à ajouter. En demandant à l’éditeur de liens à traiter d’abord a.obj, vous pouvez éviter l’avertissement.

Une cause courante de cette erreur est lorsque deux fichiers sources spécifient l’option [/Yc (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md) avec le même nom de fichier d’en-tête spécifié dans le **en-tête précompilé** champ. Une cause courante de ce problème est liée à stdafx.h dans la mesure où, par défaut, stdafx.cpp inclut stdafx.h et n’ajoute pas de nouveaux symboles. Si un autre fichier source inclut stdafx.h avec **/Yc** et le fichier .obj associé est traité avant stdafx.obj, l’éditeur de liens lèvera LNK4221.

Une façon de résoudre ce problème consiste à vous assurer que chaque en-tête précompilé, il n'existe qu’un seul fichier source inclut avec **/Yc**. Tous les autres fichiers sources doivent utiliser des en-têtes précompilés. Pour plus d’informations sur la façon de modifier ce paramètre, consultez [/Yu (utiliser un en-tête précompilé)](../../build/reference/yu-use-precompiled-header-file.md).