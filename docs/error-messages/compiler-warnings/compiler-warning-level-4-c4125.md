---
title: Compilateur avertissement (niveau 4) C4125 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4125
dev_langs:
- C++
helpviewer_keywords:
- C4125
ms.assetid: a081d1f4-0789-4915-91df-7ff0b28ca245
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7042dd8689bf5a9bafc35d6bdaa6028f0c52df2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087238"
---
# <a name="compiler-warning-level-4-c4125"></a>Avertissement du compilateur (niveau 4) C4125

un nombre décimal termine une séquence d’échappement octale

Le compilateur évalue le nombre octal sans le chiffre décimal et suppose que le chiffre décimal est un caractère.

## <a name="example"></a>Exemple

```
// C4125a.cpp
// compile with: /W4
char array1[] = "\709"; // C4125
int main()
{
}
```

Si le chiffre 9 est censé être un caractère, corrigez l’exemple comme suit :

```
// C4125b.cpp
// compile with: /W4
char array[] = "\0709";  // C4125 String containing "89"
int main()
{
}
```