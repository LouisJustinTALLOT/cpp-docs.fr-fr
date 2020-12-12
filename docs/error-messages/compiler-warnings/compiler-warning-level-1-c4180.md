---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4180'
title: Avertissement du compilateur (niveau 1) C4180
ms.date: 11/04/2016
f1_keywords:
- C4180
helpviewer_keywords:
- C4180
ms.assetid: 40c91bd4-37f1-4d59-a4f3-d5ddab68239b
ms.openlocfilehash: d85097212086d98b70b71837b01ef1522f87580c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266713"
---
# <a name="compiler-warning-level-1-c4180"></a>Avertissement du compilateur (niveau 1) C4180

qualificateur appliqué au type fonction n'a pas de sens ; ignoré

Un qualificateur, tel que **`const`** , est appliqué à un type de fonction défini par **`typedef`** .

## <a name="example"></a>Exemple

```cpp
// C4180.cpp
// compile with: /W1 /c
typedef int FuncType(void);

// the const qualifier cannot be applied to the
// function type FuncType
const FuncType f;   // C4180
```
