---
title: 4.4 OMP_NESTED | Documents Microsoft
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
ms.openlocfilehash: 1779b75774a2177a0d6a4f0661406e28b479a7ee
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690268"
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED
Le `OMP_NESTED` variable d’environnement Active ou désactive le parallélisme imbriqué, sauf si le parallélisme imbriquée est activée ou désactivée en appelant le `o` **mp_set_nested** routine de bibliothèque. Si la valeur **TRUE**, parallélisme imbriquée est activée ; si elle est définie sur **FALSE**imbriquée parallélisme est désactivé. La valeur par défaut est **FALSE**.  
  
 Exemple :  
  
```  
setenv OMP_NESTED TRUE  
```  
  
## <a name="cross-reference"></a>Référence croisée :  
  
-   `omp_set_nested` fonction, consultez [Section 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) page 40.