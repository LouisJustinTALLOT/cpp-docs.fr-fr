---
title: Erreur du compilateur C3195
ms.date: 11/04/2016
f1_keywords:
- C3195
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
ms.openlocfilehash: 4a54a9c629a1abaa4f1c5d15d06448e82cf25561
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538851"
---
# <a name="compiler-error-c3195"></a>Erreur du compilateur C3195

'operator' : est réservé et ne peut pas être utilisé comme membre d'une classe ref ou d'un type valeur. Les opérateurs CLR ou WinRT doivent être définis à l'aide du mot clé 'operator'

Le compilateur a détecté une définition d’opérateur utilisant la syntaxe des extensions managées pour C++. Vous devez utiliser la syntaxe C++ pour les opérateurs.

L'exemple suivant génère l'erreur C3195 et montre comment la corriger :

```
// C3195.cpp
// compile with: /clr /LD
#using <mscorlib.dll>
value struct V {
   static V op_Addition(V v, int i);   // C3195
   static V operator +(V v, char c);   // OK for new C++ syntax
};
```