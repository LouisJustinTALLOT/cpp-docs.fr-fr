---
title: Erreur du compilateur C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: 813da5a2fd79c191df731937e58100d749f8690c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223406"
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

[Auto, mot clé](../../cpp/auto-keyword.md)
