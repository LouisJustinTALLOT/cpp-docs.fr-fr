---
title: Compilateur avertissement (niveau 1) C4180 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4180
dev_langs:
- C++
helpviewer_keywords:
- C4180
ms.assetid: 40c91bd4-37f1-4d59-a4f3-d5ddab68239b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 231c979c0c728e3a69ec27905e7fbd42342bbd6d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080049"
---
# <a name="compiler-warning-level-1-c4180"></a>Avertissement du compilateur (niveau 1) C4180

qualificateur appliqué au type fonction n'a pas de sens ; ignoré

Un qualificateur, tel que **const**, est appliqué à un type de fonction défini par `typedef`.

## <a name="example"></a>Exemple

```
// C4180.cpp
// compile with: /W1 /c
typedef int FuncType(void);

// the const qualifier cannot be applied to the
// function type FuncType
const FuncType f;   // C4180
```