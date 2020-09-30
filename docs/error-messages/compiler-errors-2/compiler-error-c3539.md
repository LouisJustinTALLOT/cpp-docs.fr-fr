---
title: Erreur du compilateur C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: e30ea0713229bfd8da395baef710571f8dfd49e9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508150"
---
# <a name="compiler-error-c3539"></a>Erreur du compilateur C3539

'type' : un argument de modèle ne peut pas être un type contenant’auto'

Le type d’argument de modèle indiqué ne peut pas contenir une utilisation du **`auto`** mot clé.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Ne spécifiez pas l’argument template avec le **`auto`** mot clé.

## <a name="example"></a>Exemple

L’exemple suivant génère C3539.

```cpp
// C3539.cpp
// Compile with /Zc:auto
template<class T> class C{};
int main()
{
   C<auto> c;   // C3539
   return 0;
}
```

## <a name="see-also"></a>Voir aussi

[Auto, mot clé](../../cpp/auto-cpp.md)
