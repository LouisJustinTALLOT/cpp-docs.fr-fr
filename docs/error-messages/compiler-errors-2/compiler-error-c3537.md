---
title: Erreur du compilateur C3537 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3537
dev_langs:
- C++
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f04500998adf132594b91fc38f82c8bec4b1c5c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107683"
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