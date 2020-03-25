---
title: Erreur irrécupérable NMAKE U1070
ms.date: 11/04/2016
f1_keywords:
- U1070
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
ms.openlocfilehash: 008d49df3460cb7cf760e4b278db20da444555fe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182771"
---
# <a name="nmake-fatal-error-u1070"></a>Erreur irrécupérable NMAKE U1070

cycle dans la définition de macro’nommacro'

La définition de macro donnée contenait une macro dont la définition contenait la macro donnée. Les définitions de macros circulaires ne sont pas valides.

## <a name="example"></a>Exemple

Les définitions de macro suivantes

```
ONE=$(TWO)
TWO=$(ONE)
```

cause de l’erreur suivante :

```
cycle in macro definition 'TWO'
```
