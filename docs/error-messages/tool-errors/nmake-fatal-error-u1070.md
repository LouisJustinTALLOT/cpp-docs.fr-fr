---
description: 'En savoir plus sur : erreur irrécupérable NMAKE NMAKE U1070'
title: Erreur irrécupérable NMAKE U1070
ms.date: 11/04/2016
f1_keywords:
- U1070
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
ms.openlocfilehash: a3d0ee448062fec8a024501b0c08d5f0466d974b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283522"
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
