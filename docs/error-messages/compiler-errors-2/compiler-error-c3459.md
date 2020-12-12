---
description: 'En savoir plus sur : erreur du compilateur C3459'
title: Erreur du compilateur C3459
ms.date: 11/04/2016
f1_keywords:
- C3459
helpviewer_keywords:
- C3459
ms.assetid: 3d290a20-d313-4c07-9bd8-c5c159cb169f
ms.openlocfilehash: 862dd9b2f84a44db2e2cd08b918938b14692e18d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113569"
---
# <a name="compiler-error-c3459"></a>Erreur du compilateur C3459

'attribute' : attribut autorisé uniquement sur un indexeur de classe (propriété indexée par défaut)

Un attribut conçu pour être appliqué à une propriété d’indexeur de classe a été utilisé incorrectement.

Pour plus d’informations, consultez [Comment : utiliser des propriétés en C++/CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3459 :

```cpp
// C3459.cpp
// compile with: /clr /c
public ref class MyString {
public:
   [System::Runtime::CompilerServices::IndexerName("Chars")]   // C3459
   property int Prop;
};

// OK
public ref class MyString2 {
   array<int>^ MyArr;
public:
   MyString2() {
      MyArr = gcnew array<int>(5);
   }

   [System::Runtime::CompilerServices::IndexerName("Chars")]   // OK
   property int default[int] {
      int get(int index) {
         return MyArr[index];
      }
      void set(int index, int value) {
         MyArr[index] = value;
      }
   }
};
```
