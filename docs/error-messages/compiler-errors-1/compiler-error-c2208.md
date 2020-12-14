---
description: 'En savoir plus sur : erreur du compilateur C2208'
title: Erreur du compilateur C2208
ms.date: 11/04/2016
f1_keywords:
- C2208
helpviewer_keywords:
- C2208
ms.assetid: 9ae704bc-bf70-45f1-8e47-0470f21edd4e
ms.openlocfilehash: 76452c504e5f90857b15c5fc9250923705d3d20c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245640"
---
# <a name="compiler-error-c2208"></a>Erreur du compilateur C2208

'type' : aucun membre défini à l’aide de ce type

Un identificateur résolu en un nom de type se trouve dans une déclaration d’agrégation, mais le compilateur ne peut pas déclarer un membre.

L’exemple suivant génère l’C2208 :

```cpp
// C2208.cpp
class C {
   C;   // C2208
   C(){}   // OK
};
```
