---
title: Erreur du compilateur C3183
ms.date: 11/04/2016
f1_keywords:
- C3183
helpviewer_keywords:
- C3183
ms.assetid: dbd0f020-c739-43c9-947e-9ce21537331b
ms.openlocfilehash: ff48c9a084049efe5520e39a269be5c2abcd40a6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761645"
---
# <a name="compiler-error-c3183"></a>Erreur du compilateur C3183

impossible de définir une classe, un struct ou une union sans nom à l'intérieur du type managé ou WinRT 'type'

Un type qui est incorporé dans un type managé ou WinRT doit être nommé.

L'exemple suivant génère l'erreur C3183 :

```cpp
// C3183a.cpp
// compile with: /clr /c
ref class Test
{
   ref class
   {  // C3183, delete class or name it
      int a;
      int b;
   };
};
```
