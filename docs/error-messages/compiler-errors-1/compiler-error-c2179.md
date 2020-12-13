---
description: 'En savoir plus sur : erreur du compilateur C2179'
title: Erreur du compilateur C2179
ms.date: 11/04/2016
f1_keywords:
- C2179
helpviewer_keywords:
- C2179
ms.assetid: f929bfc6-3964-4e54-87d6-7529b9b6c0b9
ms.openlocfilehash: 17ddc839161f36efc668bb52504e2434ec82f995
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335225"
---
# <a name="compiler-error-c2179"></a>Erreur du compilateur C2179

'type' : un argument d’attribut ne peut pas utiliser de paramètres de type

Un paramètre de type générique est résolu au moment de l’exécution. Toutefois, un paramètre d’attribut doit être résolu au moment de la compilation. Par conséquent, vous ne pouvez pas utiliser un paramètre de type générique en tant qu’argument d’un attribut.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2179.

```cpp
// C2179.cpp
// compile with: /clr
using namespace System;

public ref struct Attr : Attribute {
   Attr(Type ^ a) {
      x = a;
   }

   Type ^ x;
};

ref struct G {};

generic<typename T>
public ref class Z {
public:
   Type ^ d;
   [Attr(T::typeid)]   // C2179
   // try the following line instead
   // [Attr(G::typeid)]
   T t;
};
```
