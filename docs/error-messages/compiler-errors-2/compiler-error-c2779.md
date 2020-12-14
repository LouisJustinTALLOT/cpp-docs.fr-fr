---
description: 'En savoir plus sur : erreur du compilateur C2779'
title: Erreur du compilateur C2779
ms.date: 11/04/2016
f1_keywords:
- C2779
helpviewer_keywords:
- C2779
ms.assetid: 4a00e492-855a-41f3-8a18-5f60ee20c2f2
ms.openlocfilehash: 88acf83feb7a5aece8f05431eec7c70869cba6a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298043"
---
# <a name="compiler-error-c2779"></a>Erreur du compilateur C2779

'Déclaration' : les méthodes de propriété ne peuvent être associées qu’à des données membres non statiques

L' **`property`** attribut étendu est appliqué de façon incorrecte à un membre de données statique.

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
