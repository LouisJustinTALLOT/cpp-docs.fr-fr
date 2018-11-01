---
title: Erreur du compilateur C2395
ms.date: 11/04/2016
f1_keywords:
- C2395
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
ms.openlocfilehash: dd3bd922e2bfa61da2da87d368bb4b28237161f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599835"
---
# <a name="compiler-error-c2395"></a>Erreur du compilateur C2395

'your_type::operator'op'' : opérateur CLR ou WinRT non valide. Au moins l'un des paramètres doit avoir les types suivants : 'T', 'T%', 'T&', 'T^', 'T^%', 'T^&', où T = 'your_type'

Un opérateur dans un type managé ou Windows Runtime ne disposait pas d'au moins un paramètre dont le type est le même que le type de la valeur de retour de l'opérateur.

L'exemple suivant génère l'erreur C2395 et montre comment la corriger :

```
// C2395.cpp
// compile with: /clr /c
value struct V {
   static V operator *(int i, char c);   // C2395

   // OK
   static V operator *(V v, char c);
   // or
   static V operator *(int i, V& rv);
};
```