---
title: Erreur du compilateur C3195 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3195
dev_langs:
- C++
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c299704b595ca6e6f6b81fb56ffad5534f81e6b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040594"
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