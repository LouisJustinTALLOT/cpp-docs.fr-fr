---
title: Erreur du compilateur C3152
ms.date: 11/04/2016
f1_keywords:
- C3152
helpviewer_keywords:
- C3152
ms.assetid: 4ee6e2cd-5d19-4b73-833d-765c35797e4b
ms.openlocfilehash: 270d2fb02365f9c2460257d96bb5f6028707553e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374883"
---
# <a name="compiler-error-c3152"></a>Erreur du compilateur C3152

'construction' : 'mot clé' ne peut s'appliquer qu'à une classe, une structure ou une fonction membre virtuelle

Certains mots clés ne peuvent être appliqués qu'à une classe C++.

L'exemple suivant génère l'erreur C3152 et montre comment la corriger :

```
// C3152.cpp
// compile with: /clr /c
ref class C {
   int (*pfn)() sealed;   // C3152
   virtual int g() sealed;   // OK
};
```
