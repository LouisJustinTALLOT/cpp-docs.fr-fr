---
title: Erreur du compilateur C2633
ms.date: 11/04/2016
f1_keywords:
- C2633
helpviewer_keywords:
- C2633
ms.assetid: a7aceb65-4255-42d6-a8fb-e3cb6c4d2270
ms.openlocfilehash: a2e4ca81194968fb50a5442cab3d229a25b8be1b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754678"
---
# <a name="compiler-error-c2633"></a>Erreur du compilateur C2633

'identifier' : 'inline’est la seule classe de stockage autorisée pour les constructeurs

Un constructeur est déclaré comme une classe de stockage autre que Inline.

L’exemple suivant génère l’C2633 :

```cpp
// C2633.cpp
// compile with: /c
class C {
   extern C();   // C2633, not inline
   inline C();   // OK
};
```
