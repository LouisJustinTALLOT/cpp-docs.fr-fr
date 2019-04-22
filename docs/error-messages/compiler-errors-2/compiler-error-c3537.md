---
title: Erreur du compilateur C3537
ms.date: 11/04/2016
f1_keywords:
- C3537
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
ms.openlocfilehash: 50a06180dabfa192292fae7ba1962b6b7455bb89
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024022"
---
# <a name="compiler-error-c3537"></a>Erreur du compilateur C3537

'type' : vous ne pouvez pas effectuer un cast en un type contenant 'auto'

Vous ne pouvez pas effectuer un cast d’une variable dans le type indiqué parce que le type contient le `auto` mot clé et la valeur par défaut [/Zc : auto](../../build/reference/zc-auto-deduce-variable-type.md) option du compilateur est en vigueur.

## <a name="example"></a>Exemple

Le code suivant donne C3537 parce que les variables sont converties en un type qui contient le `auto` mot clé.

```
// C3537.cpp
// Compile with /Zc:auto
int main()
{
   int value = 123;
   auto(value);                        // C3537
   (auto)value;                        // C3537
   auto x1 = auto(value);              // C3537
   auto x2 = (auto)value;              // C3537
   auto x3 = static_cast<auto>(value); // C3537
   return 0;
}
```

## <a name="see-also"></a>Voir aussi

[auto, mot clé](../../cpp/auto-keyword.md)