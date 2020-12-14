---
description: 'En savoir plus sur : erreur du compilateur C2802'
title: Erreur du compilateur C2802
ms.date: 11/04/2016
f1_keywords:
- C2802
helpviewer_keywords:
- C2802
ms.assetid: 08b68c0e-9382-40ac-8949-39a7a2749e05
ms.openlocfilehash: ff526306b89a5679147a30e7b3cd2f07ddc2b8f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297445"
---
# <a name="compiler-error-c2802"></a>Erreur du compilateur C2802

le membre static’operator opérateur’n’a pas de paramètres formels

Un opérateur déclaré par une **`static`** fonction membre doit avoir au moins un paramètre.

L’exemple suivant génère l’C2802 :

```cpp
// C2802.cpp
// compile with: /clr /c
ref class A {
   static operator+ ();   // C2802
   static operator+ (A^, A^);   // OK
};
```
