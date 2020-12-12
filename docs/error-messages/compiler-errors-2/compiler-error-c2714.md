---
description: 'En savoir plus sur : erreur du compilateur C2714'
title: Erreur du compilateur C2714
ms.date: 07/22/2020
f1_keywords:
- C2714
helpviewer_keywords:
- C2714
ms.assetid: 401a5a42-660c-4bad-9d63-1a2d092bc489
ms.openlocfilehash: 7bea0fc27de49f5767b8b250254f255964423cdc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320829"
---
# <a name="compiler-error-c2714"></a>Erreur du compilateur C2714

> `alignof(void)` n’est pas autorisé

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
