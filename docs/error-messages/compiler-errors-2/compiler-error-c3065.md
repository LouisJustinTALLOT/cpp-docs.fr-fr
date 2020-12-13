---
description: 'En savoir plus sur : erreur du compilateur C3065'
title: Erreur du compilateur C3065
ms.date: 11/04/2016
f1_keywords:
- C3065
helpviewer_keywords:
- C3065
ms.assetid: e7a0bc69-1c68-459e-a7c4-93c65609ff7c
ms.openlocfilehash: 9c3c2ef0d788a193f2f2d61bf76e7672d1deda87
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341150"
---
# <a name="compiler-error-c3065"></a>Erreur du compilateur C3065

la déclaration de propriété au niveau d'une portée sans classe n'est pas autorisée

Le modificateur __declspec de [property](../../cpp/property-cpp.md) a été utilisé en dehors d’une classe.  Une propriété ne peut être déclarée qu’à l’intérieur d’une classe.

L’exemple suivant génère l’erreur C3065 :

```cpp
// C3065.cpp
// compile with: /c
__declspec(property(get=get_i)) int i;   // C3065

class x {
public:
   __declspec(property(get=get_i)) int i;   // OK
};
```
