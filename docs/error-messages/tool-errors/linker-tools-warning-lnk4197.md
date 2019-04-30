---
title: Avertissement des outils Éditeur de liens LNK4197
ms.date: 09/05/2018
f1_keywords:
- LNK4197
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
ms.openlocfilehash: 0abad1b98ff4782f077312752603ec17fd611c12
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390358"
---
# <a name="linker-tools-warning-lnk4197"></a>Avertissement des outils Éditeur de liens LNK4197

> Exporter «*exportname*' spécifiée à plusieurs reprises ; première spécification utilisée

Une exportation est spécifiée dans plusieurs et différentes façons. L’éditeur de liens utilise la première spécification et ignore le reste.

Si vous régénérez la bibliothèque Runtime C, vous pouvez ignorer ce message.

Si une exportation est spécifiée de la même manière que plusieurs fois, l’éditeur de liens pas émet un avertissement.

Par exemple, le contenu suivant d’un fichier .def peut causer cet avertissement :

```
EXPORTS
   functioname      NONAME
   functioname      @10
```

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. La même exportation est spécifiée à la fois sur la ligne de commande (via l’exportation :) et dans le fichier .def.

2. La même exportation est répertoriée deux fois dans le fichier .def avec des attributs différents.