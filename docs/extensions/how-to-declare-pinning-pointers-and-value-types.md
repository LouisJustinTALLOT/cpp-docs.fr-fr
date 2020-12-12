---
description: 'En savoir plus sur : Comment : déclarer des pointeurs épingles et des types valeur'
title: "Comment : déclarer l'épinglage de pointeurs et de types de valeur"
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
ms.openlocfilehash: abbb085a9d85870d43ad00687b30e0f395186ba2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119289"
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>Comment : déclarer l'épinglage de pointeurs et de types de valeur

Un type valeur peut être implicitement converti (boxed). Vous pouvez ensuite déclarer un pointeur épingle vers l’objet de type valeur lui-même et utiliser un **pin_ptr** pour le type valeur boxed.

## <a name="example"></a>Exemple

### <a name="code"></a>Code

```cpp
// pin_ptr_value.cpp
// compile with: /clr
value struct V {
   int i;
};

int main() {
   V ^ v = gcnew V;   // imnplicit boxing
   v->i=8;
   System::Console::WriteLine(v->i);
   pin_ptr<V> mv = &*v;
   mv->i = 7;
   System::Console::WriteLine(v->i);
   System::Console::WriteLine(mv->i);
}
```

```Output
8
7
7
```

## <a name="see-also"></a>Voir aussi

[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)
