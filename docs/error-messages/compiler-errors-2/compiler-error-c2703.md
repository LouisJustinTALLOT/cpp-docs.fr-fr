---
title: Erreur du compilateur C2703
description: Décrit l’erreur C2703 du compilateur Microsoft C/C++.
ms.date: 08/24/2020
f1_keywords:
- C2703
helpviewer_keywords:
- C2703
ms.assetid: 384295c3-643d-47ae-a9a6-865b3036aa84
ms.openlocfilehash: 4d5b5ccad1cd15c1a107c81423e2372e14165776
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898600"
---
# <a name="compiler-error-c2703"></a>Erreur du compilateur C2703

> instruction non conforme `__leave`

## <a name="remarks"></a>Notes

Une **`__leave`** instruction doit être à l’intérieur d’un **`__try`** bloc.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2703 :

```cpp
// C2703.cpp
int main() {
   __leave;   // C2703
   __try {
      // try the following line instead
      __leave;
   }
   __finally {}
}
```

## <a name="see-also"></a>Voir aussi

[`__leave`Mot clé](../../cpp/try-except-statement.md#__leave)\
[`try-except` gestion](../../cpp/try-except-statement.md)\
[`try-finally` gestion](../../cpp/try-finally-statement.md)
