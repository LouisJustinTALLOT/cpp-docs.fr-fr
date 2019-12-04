---
title: Erreur du compilateur C2779
ms.date: 11/04/2016
f1_keywords:
- C2779
helpviewer_keywords:
- C2779
ms.assetid: 4a00e492-855a-41f3-8a18-5f60ee20c2f2
ms.openlocfilehash: 9b4e0f255fd62801cb2010c109d05de89362bb9f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739998"
---
# <a name="compiler-error-c2779"></a>Erreur du compilateur C2779

'Déclaration' : les méthodes de propriété ne peuvent être associées qu’à des données membres non statiques

L’attribut étendu `property` est appliqué de façon incorrecte à un membre de données statique.

L’exemple suivant génère l’C2779 :

```cpp
// C2779.cpp
struct A {
   static __declspec(property(put=PutProp))
   // try the following line instead
   __declspec(property(put=PutProp))
      int prop;   // C2779
   int PutProp(void);
};
```
