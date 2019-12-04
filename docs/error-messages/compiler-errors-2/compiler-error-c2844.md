---
title: Erreur du compilateur C2844
ms.date: 11/04/2016
f1_keywords:
- C2844
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
ms.openlocfilehash: fdfd2200503f80addb120117ce06f5f837d6b9f2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752013"
---
# <a name="compiler-error-c2844"></a>Erreur du compilateur C2844

'membre' : ne peut pas être membre de l’interface’interface'

Une [classe d’interface](../../extensions/interface-class-cpp-component-extensions.md) ne peut pas contenir de données membres à moins qu’il ne s’agit également d’une propriété.

Tout élément autre qu’une fonction de propriété ou de membre n’est pas autorisé dans une interface. En outre, les constructeurs, les destructeurs et les opérateurs ne sont pas autorisés.

L’exemple suivant génère l’C2844 :

```cpp
// C2844a.cpp
// compile with: /clr /c
public interface class IFace {
   int i;   // C2844
   // try the following line instead
   // property int Size;
};
```
