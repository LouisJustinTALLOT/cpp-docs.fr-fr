---
description: 'En savoir plus sur : erreur du compilateur C2879'
title: Erreur du compilateur C2879
ms.date: 11/04/2016
f1_keywords:
- C2879
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
ms.openlocfilehash: 6060678f71bf36d0af2e94e380a046ea7916ef05
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194369"
---
# <a name="compiler-error-c2879"></a>Erreur du compilateur C2879

'Symbol' : seul un espace de noms existant peut être attribué à un autre nom par une définition d’alias d’espace de noms

Vous ne pouvez pas créer un [alias d’espace de noms](../../cpp/namespaces-cpp.md#namespace_aliases) pour un autre symbole qu’un espace de noms.

L’exemple suivant génère l’C2879 :

```cpp
// C2879.cpp
int main() {
   int i;
   namespace A = i;   // C2879 i is not a namespace
}
```
