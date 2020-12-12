---
description: En savoir plus sur les directives du préprocesseur
title: Directives vers le préprocesseur
ms.date: 11/04/2016
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
ms.openlocfilehash: 50691647436f492b329b6af43a626e933453d3a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213954"
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
