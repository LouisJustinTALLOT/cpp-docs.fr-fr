---
title: Directives vers le préprocesseur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1ddecf1e205cc9a6d7f09a27fbf243417540e49
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033561"
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