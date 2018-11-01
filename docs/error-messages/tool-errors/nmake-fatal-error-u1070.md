---
title: Erreur irrécupérable NMAKE U1070
ms.date: 11/04/2016
f1_keywords:
- U1070
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
ms.openlocfilehash: 35bea47f6626dfe283a537d3d96340921c37f3f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484212"
---
# <a name="nmake-fatal-error-u1070"></a>Erreur irrécupérable NMAKE U1070

cycle dans la définition de macro 'nom_macro'

La définition de macro donnée contenait une macro dont la définition contenue la macro donnée. Définitions de macros circulaires ne sont pas valides.

## <a name="example"></a>Exemple

Les définitions de macro suivantes

```
ONE=$(TWO)
TWO=$(ONE)
```

provoquer l’erreur suivante :

```
cycle in macro definition 'TWO'
```