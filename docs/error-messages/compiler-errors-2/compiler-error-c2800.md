---
description: 'En savoir plus sur : erreur du compilateur C2800'
title: Erreur du compilateur C2800
ms.date: 11/04/2016
f1_keywords:
- C2800
helpviewer_keywords:
- C2800
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
ms.openlocfilehash: 7adcb8e24bd7b3f3941260a9cceaa5157334ae8d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297503"
---
# <a name="compiler-error-c2800"></a>Erreur du compilateur C2800

'operator opérateur’ne peut pas être surchargé

Les opérateurs suivants ne peuvent pas être surchargés : accès au membre de classe ( `.` ), pointeur vers membre ( `.*` ), résolution de portée ( `::` ), expression conditionnelle ( `? :` ) et **`sizeof`** .

L’exemple suivant génère l’C2800 :

```cpp
// C2800.cpp
// compile with: /c
class C {
   operator:: ();   // C2800
};
```
