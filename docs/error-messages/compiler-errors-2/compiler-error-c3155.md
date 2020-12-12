---
description: 'En savoir plus sur : erreur du compilateur C3155'
title: Erreur du compilateur C3155
ms.date: 11/04/2016
f1_keywords:
- C3155
helpviewer_keywords:
- C3155
ms.assetid: b04a42e1-64e7-40f8-81fe-c7945348b2cf
ms.openlocfilehash: 92fdf24c067c26502f8d24923e7f2c77b16c7922
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242455"
---
# <a name="compiler-error-c3155"></a>Erreur du compilateur C3155

les attributs ne sont pas autorisés dans un indexeur de propriété

Une propriété indexée a été déclarée de manière incorrecte. Pour plus d’informations, consultez [Comment : utiliser des propriétés en C++/CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3155.

```cpp
// C3155.cpp
// compile with: /clr /c
using namespace System;
ref struct R {
   property int F[[ParamArray] int] {   // C3155
   // try the following line instead
   // property int F[ int] {   // OK
      int get(int i) {
         return 0;
      }
   }
};
```
