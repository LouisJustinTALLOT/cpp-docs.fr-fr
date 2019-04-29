---
title: Erreur irrécupérable NMAKE U1070
ms.date: 11/04/2016
f1_keywords:
- U1070
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
ms.openlocfilehash: 35bea47f6626dfe283a537d3d96340921c37f3f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367237"
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