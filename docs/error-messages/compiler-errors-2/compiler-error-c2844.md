---
title: Erreur du compilateur C2844
ms.date: 11/04/2016
f1_keywords:
- C2844
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
ms.openlocfilehash: 8af9f42be279f728f72fc6968aeba98ee5d2474a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462710"
---
# <a name="compiler-error-c2844"></a>Erreur du compilateur C2844

'membre' : ne peut pas être un membre d’interface 'interface'

Un [classe d’interface](../../windows/interface-class-cpp-component-extensions.md) ne peut pas contenir un membre de données, sauf si elle est également une propriété.

Autre chose qu’une propriété ou une fonction membre n’est pas autorisée dans une interface. En outre, les constructeurs, destructeurs et les opérateurs ne sont pas autorisés.

L’exemple suivant génère l’erreur C2844 :

```
// C2844a.cpp
// compile with: /clr /c
public interface class IFace {
   int i;   // C2844
   // try the following line instead
   // property int Size;
};
```
