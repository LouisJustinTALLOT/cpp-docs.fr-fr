---
description: 'En savoir plus sur : erreur du compilateur C2140'
title: Erreur du compilateur C2140
ms.date: 11/04/2016
f1_keywords:
- C2140
helpviewer_keywords:
- C2140
ms.assetid: d44a0500-002c-4632-9e5e-c71c3a473ec4
ms.openlocfilehash: b9292019ce9a17c8f1dabca87f61f27b21494a82
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124148"
---
# <a name="compiler-error-c2140"></a>Erreur du compilateur C2140

'type' : un type dépendant d’un paramètre de type générique n’est pas autorisé en tant qu’argument pour le trait de type intrinsèque du compilateur’trait'

Un spécificateur de type non valide a été passé à un trait de type.

Pour plus d’informations, consultez [Prise en charge du compilateur pour les caractéristiques de type](../../extensions/compiler-support-for-type-traits-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2140.

```cpp
// C2140.cpp
// compile with: /clr /c
template <class T>

struct is_polymorphic {
   static const bool value = __is_polymorphic(T);
};

class x {};

generic <class T>
ref class C {
   void f() {
      System::Console::WriteLine(__is_polymorphic(T));   // C2140
      System::Console::WriteLine(is_polymorphic<T>::value);   // C2140

      System::Console::WriteLine(__is_polymorphic(x));   // OK
      System::Console::WriteLine(is_polymorphic<x>::value);   // OK
   }
};
```
