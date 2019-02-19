---
title: Directives vers le préprocesseur
ms.date: 11/04/2016
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
ms.openlocfilehash: 520d181c3a58ee2c626678a3afd9126f1ef183cc
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149035"
---
# <a name="directives-to-the-preprocessor"></a>Directives vers le préprocesseur

Une « directive » demande au préprocesseur C d'exécuter une action spécifique sur le texte du programme avant la compilation. Les [directives de préprocesseur](../preprocessor/preprocessor-directives.md) sont décrites en détail dans la section *Référence du préprocesseur*. L'exemple suivant utilise la directive de préprocesseur `#define` :

```
#define MAX 100
```

Cette instruction indique au compilateur de remplacer chaque occurrence de `MAX` par `100` avant la compilation. Les directives de préprocesseur du compilateur C sont les suivantes :

|#define|#endif|#ifdef|#line|
|--------------|-------------|-------------|------------|
|`#elif`|`#error`|**#ifndef**|**#pragma**|
|`#else`|`#if`|`#include`|`#undef`|

## <a name="see-also"></a>Voir aussi

[Fichiers sources et programmes sources](../c-language/source-files-and-source-programs.md)
