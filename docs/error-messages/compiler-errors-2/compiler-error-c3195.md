---
title: Erreur du compilateur C3195
ms.date: 11/04/2016
f1_keywords:
- C3195
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
ms.openlocfilehash: c8274e121e953c3e51a0f2ff8c68c315759ce3e1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760424"
---
# <a name="compiler-error-c3195"></a>Erreur du compilateur C3195

'operator' : est réservé et ne peut pas être utilisé comme membre d'une classe ref ou d'un type valeur. Les opérateurs CLR ou WinRT doivent être définis à l'aide du mot clé 'operator'

Le compilateur a détecté une définition d'opérateur utilisant la syntaxe des extensions managées pour C++. Vous devez utiliser la C++ syntaxe pour les opérateurs.

L'exemple suivant génère l'erreur C3195 et montre comment la corriger :

```cpp
// C3195.cpp
// compile with: /clr /LD
#using <mscorlib.dll>
value struct V {
   static V op_Addition(V v, int i);   // C3195
   static V operator +(V v, char c);   // OK for new C++ syntax
};
```
