---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4125'
title: Avertissement du compilateur (niveau 4) C4125
ms.date: 11/04/2016
f1_keywords:
- C4125
helpviewer_keywords:
- C4125
ms.assetid: a081d1f4-0789-4915-91df-7ff0b28ca245
ms.openlocfilehash: 82c94743e2ff52efacdf1b5f139bc4d9d40d0eed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261916"
---
# <a name="compiler-warning-level-4-c4125"></a>Avertissement du compilateur (niveau 4) C4125

un nombre décimal termine une séquence d’échappement octale

Le compilateur évalue le nombre octal sans le chiffre décimal et suppose que le chiffre décimal est un caractère.

## <a name="example"></a>Exemple

```cpp
// C4125a.cpp
// compile with: /W4
char array1[] = "\709"; // C4125
int main()
{
}
```

Si le chiffre 9 est censé être un caractère, corrigez l’exemple comme suit :

```cpp
// C4125b.cpp
// compile with: /W4
char array[] = "\0709";  // C4125 String containing "89"
int main()
{
}
```
