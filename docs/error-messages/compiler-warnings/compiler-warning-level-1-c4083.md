---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4083'
title: Avertissement du compilateur (niveau 1) C4083
ms.date: 11/04/2016
f1_keywords:
- C4083
helpviewer_keywords:
- C4083
ms.assetid: e7d3344e-5645-4d56-8460-d1acc9145ada
ms.openlocfilehash: 2913e4a55b7c777ae4c910631b8fb10120dd3463
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272329"
---
# <a name="compiler-warning-level-1-c4083"></a>Avertissement du compilateur (niveau 1) C4083

'Token’attendu ; identificateur’identifier’trouvé

Un identificateur se trouve à l’emplacement incorrect dans une instruction **#pragma** .

## <a name="example"></a>Exemple

```cpp
// C4083.cpp
// compile with: /W1 /LD
#pragma warning disable:4083    // C4083
#pragma warning(disable:4083)   //correct
```

Vérifiez la syntaxe des directives de [#pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) .
