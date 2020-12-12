---
description: 'En savoir plus sur : erreur du compilateur C3360'
title: Erreur du compilateur C3360
ms.date: 11/04/2016
f1_keywords:
- C3360
helpviewer_keywords:
- C3360
ms.assetid: 6acf983a-dbb6-422b-b045-a34bb4ba6761
ms.openlocfilehash: d4ab0a4ffd12e5ffde46971134dfe858c491733c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150889"
---
# <a name="compiler-error-c3360"></a>Erreur du compilateur C3360

'string' : Impossible de créer le nom

La valeur passée à l’attribut [uuid](../../windows/attributes/uuid-cpp-attributes.md) n’était pas valide.

L’exemple suivant génère l’erreur C3360 :

```cpp
// C3360.cpp
[ uuid("1") ]
// try this line instead
// [ uuid("12341234-1234-1234-1234-123412341234") ]
struct A   // C3360
{
};

int main()
{
}
```
