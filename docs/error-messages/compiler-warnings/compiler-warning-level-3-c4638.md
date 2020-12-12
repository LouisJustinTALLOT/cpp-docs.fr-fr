---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4638'
title: Avertissement du compilateur (niveau 3) C4638
ms.date: 08/27/2018
f1_keywords:
- C4638
helpviewer_keywords:
- C4638
ms.assetid: 2c07923a-e103-4e40-bd11-fdfed428a5ec
ms.openlocfilehash: fc771004ebbfeef436a456523e2e2fc87382a291
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338566"
---
# <a name="compiler-warning-level-3-c4638"></a>Avertissement du compilateur (niveau 3) C4638

> Cible de commentaire de document XML : référence à un symbole inconnu'*symbol*'

## <a name="remarks"></a>Notes

Le compilateur n’a pas pu résoudre un symbole (*symbole*). Le symbole doit être valide dans la compilation.

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4638 :

```cpp
// C4638.cpp
// compile with: /clr /doc /LD /W3
using namespace System;

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary> Text </summary>
   /// <see cref="aSymbolThatAppearsNowhereInMyProject"/>
   // Try the following line instead:
   // /// <see cref="System::Console::WriteLine"/>
   void MyMethod() {}
};   // C4638
```
