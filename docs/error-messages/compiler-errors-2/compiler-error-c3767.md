---
title: Erreur du compilateur C3767 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3767
dev_langs:
- C++
helpviewer_keywords:
- C3767
ms.assetid: 5247cdcd-639c-4527-bd37-37e74c4e8fab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4e5f73016060ccc17dfe0218d8b518b2f5dbdbd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081440"
---
# <a name="compiler-error-c3767"></a>Erreur du compilateur C3767

'fonction' candidates non accessible

Une fonction friend définie dans une classe n’est pas censé être traitée comme si elle était définie et déclaré dans la portée espace de noms global. Il peut, toutefois, être trouvée par une recherche dépendante d’un argument.

C3767 peut également être dû à une modification avec rupture : les types natifs sont désormais privés par défaut dans un **/CLR** compilation ; consultez [tapez visibilité](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3767 :

```
// C3767a.cpp
// compile with: /clr
using namespace System;
public delegate void TestDel();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;
};

public ref class MyClass2 : public MyClass {
public:
   void Test() {
      MyClass^ patient = gcnew MyClass;
      patient->MyClass_Event();
    }
};

int main() {
   MyClass^ x = gcnew MyClass;
   x->MyClass_Event();   // C3767

   // OK
   MyClass2^ y = gcnew MyClass2();
   y->Test();
};
```

L’exemple suivant génère l’erreur C3767 :

```
// C3767c.cpp
// compile with: /clr /c

ref class Base  {
protected:
   void Method() {
      System::Console::WriteLine("protected");
   }
};

ref class Der : public Base {
   void Method() {
      ((Base^)this)->Method();   // C3767
      // try the following line instead
      // Base::Method();
   }
};
```

