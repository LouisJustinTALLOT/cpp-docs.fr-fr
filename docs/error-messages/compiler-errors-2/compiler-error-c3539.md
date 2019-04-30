---
title: Erreur du compilateur C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: be1051859ebbcbdc22a9b71f8c5adba2e75c4e92
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344662"
---
# <a name="compiler-error-c3539"></a>Erreur du compilateur C3539

'type' : un argument template ne peut pas être un type contenant 'auto'

Le type d’argument template indiqué ne peut pas contenir une utilisation de la `auto` mot clé.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Ne spécifiez pas l’argument de modèle avec le `auto` mot clé.

## <a name="example"></a>Exemple

L’exemple suivant donne C3539.

```
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

[auto, mot clé](../../cpp/auto-keyword.md)