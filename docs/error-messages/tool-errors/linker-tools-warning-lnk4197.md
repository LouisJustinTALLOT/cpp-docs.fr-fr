---
title: Avertissement des outils Éditeur de liens LNK4197
ms.date: 09/05/2018
f1_keywords:
- LNK4197
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
ms.openlocfilehash: 92702864a00455e4b70f00dfc9988bfb754e2e64
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183278"
---
# <a name="linker-tools-warning-lnk4197"></a>Avertissement des outils Éditeur de liens LNK4197

> l’exportation'*exportname*'a été spécifiée plusieurs fois ; utilisation de la première spécification

Une exportation est spécifiée de plusieurs façons différentes. L’éditeur de liens utilise la première spécification et ignore le reste.

Si vous reconstruisez la bibliothèque Runtime C, vous pouvez ignorer ce message.

Si une exportation est spécifiée exactement de la même façon plusieurs fois, l’éditeur de liens n’émet pas d’avertissement.

Par exemple, le contenu suivant d’un fichier. def provoquerait cet avertissement :

```
EXPORTS
   functioname      NONAME
   functioname      @10
```

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. La même exportation est spécifiée à la fois sur la ligne de commande (par exportation :) et dans le fichier. def.

2. La même exportation est indiquée deux fois dans le fichier. def avec des attributs différents.
