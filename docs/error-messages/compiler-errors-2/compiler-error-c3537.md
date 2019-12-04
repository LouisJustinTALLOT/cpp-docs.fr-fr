---
title: Erreur du compilateur C3537
ms.date: 11/04/2016
f1_keywords:
- C3537
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
ms.openlocfilehash: ef3e954987b84ea128342b38307769903df4b346
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740479"
---
# <a name="compiler-error-c3537"></a>Erreur du compilateur C3537

'type' : vous ne pouvez pas effectuer un cast vers un type qui contient’auto'

Vous ne pouvez pas effectuer un cast d’une variable vers le type indiqué, car le type contient le mot clé `auto` et l’option de compilateur [/Zc : auto](../../build/reference/zc-auto-deduce-variable-type.md) par défaut est appliquée.

## <a name="example"></a>Exemple

Le code suivant génère C3537, car les variables sont converties en un type qui contient le mot clé `auto`.

```cpp
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
