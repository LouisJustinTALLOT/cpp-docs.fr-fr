---
title: Erreur du compilateur C3227
ms.date: 11/04/2016
f1_keywords:
- C3227
helpviewer_keywords:
- C3227
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
ms.openlocfilehash: 460000531dba77e42379199f276c9e2e02f43a9b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743417"
---
# <a name="compiler-error-c3227"></a>Erreur du compilateur C3227

'paramètre' : impossible d’utiliser’keyword’pour allouer un type générique

Pour instancier un type, un constructeur approprié est requis. Toutefois, le compilateur n’est pas en mesure de s’assurer qu’un constructeur approprié est disponible.

Vous pouvez utiliser des modèles au lieu de génériques pour résoudre cette erreur, ou vous pouvez utiliser l’une des méthodes suivantes pour créer une instance du type.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3227.

```cpp
// C3227.cpp
// compile with: /clr /c
generic<class T> interface class ICreate {
   static T Create();
};

generic <class T>
where T : ICreate<T>
ref class C {
   void f() {
      T t = new T;   // C3227

      // OK
      T t2 = ICreate<T>::Create();
      T t3 = safe_cast<T>( System::Activator::CreateInstance(T::typeid) );
   }
};
```
