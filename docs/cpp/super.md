---
description: 'En savoir plus sur : `__super`'
title: __super
ms.date: 11/04/2016
f1_keywords:
- __super_cpp
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
ms.openlocfilehash: 30f2733abbd4599deabfa989d72b099c929cb050
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178132"
---
# `__super`

**Spécifique à Microsoft**

Permet de déclarer explicitement que vous appelez une implémentation de classe de base pour une fonction que vous substituez.

## <a name="syntax"></a>Syntaxe

```
__super::member_function();
```

## <a name="remarks"></a>Notes

Toutes les méthodes de classe de base accessibles sont considérées pendant la phase de résolution de surcharge, et la fonction qui fournit la meilleure correspondance est celle qui est appelée.

**`__super`** peut apparaître uniquement dans le corps d’une fonction membre.

**`__super`** ne peut pas être utilisé avec une déclaration using. Pour plus d’informations, consultez Utilisation d’une [déclaration](../cpp/using-declaration.md) .

Avec l’introduction des [attributs](../windows/attributes/attributes-alphabetical-reference.md) qui injectent du code, votre code peut contenir une ou plusieurs classes de base dont vous pouvez ne pas connaître les noms, mais qui contiennent des méthodes que vous souhaitez appeler.

## <a name="example"></a>Exemple

```cpp
// deriv_super.cpp
// compile with: /c
struct B1 {
   void mf(int) {}
};

struct B2 {
   void mf(short) {}

   void mf(char) {}
};

struct D : B1, B2 {
   void mf(short) {
      __super::mf(1);   // Calls B1::mf(int)
      __super::mf('s');   // Calls B2::mf(char)
   }
};
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)
