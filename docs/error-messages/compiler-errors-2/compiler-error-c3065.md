---
title: Erreur du compilateur C3065
ms.date: 11/04/2016
f1_keywords:
- C3065
helpviewer_keywords:
- C3065
ms.assetid: e7a0bc69-1c68-459e-a7c4-93c65609ff7c
ms.openlocfilehash: e12f6e318d51ecaccc7c29e1e01d1aedcaac937e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404208"
---
# <a name="compiler-error-c3065"></a>Erreur du compilateur C3065

la déclaration de propriété au niveau d'une portée sans classe n'est pas autorisée

Le modificateur __declspec de [property](../../cpp/property-cpp.md) a été utilisé en dehors d’une classe.  Une propriété ne peut être déclarée qu’à l’intérieur d’une classe.

L’exemple suivant génère l’erreur C3065 :

```
// C3065.cpp
// compile with: /c
__declspec(property(get=get_i)) int i;   // C3065

class x {
public:
   __declspec(property(get=get_i)) int i;   // OK
};
```