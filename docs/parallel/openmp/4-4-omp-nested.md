---
title: 4.4 OMP_NESTED | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1083269f31ebc710da24430635ff8381e3f2147a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419514"
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED

Le `OMP_NESTED` variable d’environnement Active ou désactive le parallélisme imbriquée à moins que le parallélisme imbriqué est activé ou désactivé en appelant le `o` **mp_set_nested** routine de bibliothèque. Si la valeur **TRUE**, parallélisme imbriquée est activée ; si elle est définie sur **FALSE**imbriquée parallélisme est désactivé. La valeur par défaut est **FALSE**.

Exemple :

```
setenv OMP_NESTED TRUE
```

## <a name="cross-reference"></a>Référence croisée :

- `omp_set_nested` fonction, consultez [Section 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) sur la page 40.