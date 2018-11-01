---
title: /LINKERMEMBER
ms.date: 11/04/2016
f1_keywords:
- /linkermember
helpviewer_keywords:
- /LINKERMEMBER dumpbin option
- LINKERMEMBER dumpbin option
- -LINKERMEMBER dumpbin option
ms.assetid: c96868c1-d70e-4651-ae36-c55b58b16406
ms.openlocfilehash: e55f613566b5c3bd7709fe7f30cd0ae985cd369f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494437"
---
# <a name="linkermember"></a>/LINKERMEMBER

```
/LINKERMEMBER[:{1|2}]
```

## <a name="remarks"></a>Notes

Cette option affiche des symboles publics définis dans une bibliothèque. Spécifier le 1 argument pour afficher les symboles dans l’ordre des objets, ainsi que leurs offsets. Spécifier l’argument 2 pour afficher les offsets et les numéros d’index des objets et puis répertoriez les symboles dans l’ordre alphabétique, ainsi que l’index de l’objet pour chacun. Pour obtenir les deux sorties, spécifiez /LINKERMEMBER dans l’argument number.

Uniquement les [/HEADERS](../../build/reference/headers.md) (option DUMPBIN) est disponible pour les fichiers générés avec le [/GL](../../build/reference/gl-whole-program-optimization.md) option du compilateur.

## <a name="see-also"></a>Voir aussi

[DUMPBIN, options](../../build/reference/dumpbin-options.md)