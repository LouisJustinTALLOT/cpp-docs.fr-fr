---
title: Erreur du compilateur C3914
ms.date: 11/04/2016
f1_keywords:
- C3914
helpviewer_keywords:
- C3914
ms.assetid: 8f3190e6-ee50-4916-9ecc-3b8748b2e1e7
ms.openlocfilehash: 6f7da67871b5e6b9d7da9a9aa4eebeb761f8cc50
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737996"
---
# <a name="compiler-error-c3914"></a>Erreur du compilateur C3914

une propriété par défaut ne peut pas être static

Une propriété par défaut a été déclarée de manière incorrecte.  Pour plus d’informations, consultez [Comment : utiliser des propriétés C++dans/CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3914 et montre comment la corriger.

```cpp
// C3914.cpp
// compile with: /clr /c
ref struct X {
   static property int default[int] {   // C3914
   // try the following line instead
   // property int default[int] {
      int get(int) { return 0; }
      void set(int, int) {}
   }
};
```
