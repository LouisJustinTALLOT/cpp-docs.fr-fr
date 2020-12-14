---
description: En savoir plus sur:/LINKERMEMBER
title: /LINKERMEMBER
ms.date: 11/04/2016
f1_keywords:
- /linkermember
helpviewer_keywords:
- /LINKERMEMBER dumpbin option
- LINKERMEMBER dumpbin option
- -LINKERMEMBER dumpbin option
ms.assetid: c96868c1-d70e-4651-ae36-c55b58b16406
ms.openlocfilehash: 76c842bcc2299b4245847e7d4e9a64656e88d2d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199387"
---
# <a name="linkermember"></a>/LINKERMEMBER

```
/LINKERMEMBER[:{1|2}]
```

## <a name="remarks"></a>Notes

Cette option affiche les symboles publics définis dans une bibliothèque. Spécifiez l’argument 1 pour afficher les symboles dans l’ordre des objets, ainsi que leurs décalages. Spécifiez l’argument 2 pour afficher les décalages et les numéros d’index des objets, puis répertoriez les symboles par ordre alphabétique, ainsi que l’index d’objet pour chacun d’entre eux. Pour récupérer les deux sorties, spécifiez/LINKERMEMBER sans l’argument number.

Seule l’option [/HEADERS](headers.md) DUMPBIN peut être utilisée sur les fichiers générés avec l’option du compilateur [/GL](gl-whole-program-optimization.md).

## <a name="see-also"></a>Voir aussi

[Options DUMPBIN](dumpbin-options.md)
