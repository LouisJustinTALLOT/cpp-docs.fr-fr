---
title: Erreur du compilateur C2714
ms.date: 07/22/2020
f1_keywords:
- C2714
helpviewer_keywords:
- C2714
ms.assetid: 401a5a42-660c-4bad-9d63-1a2d092bc489
ms.openlocfilehash: d3f733f065af5b3217dc19d46b46e504d39151f4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225408"
---
# <a name="compiler-error-c2714"></a>Erreur du compilateur C2714

> `alignof(void)`n’est pas autorisé

Une valeur non valide a été passée à un opérateur.

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [ `alignof` Operator](../../cpp/alignof-operator.md) .

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2714.

```cpp
// C2714.cpp
int main() {
   return alignof(void);   // C2714
   return alignof(char);   // OK
}
```
