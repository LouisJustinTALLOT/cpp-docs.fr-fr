---
title: Erreur du compilateur C2869
ms.date: 11/04/2016
f1_keywords:
- C2869
helpviewer_keywords:
- C2869
ms.assetid: 6e30c001-47f3-4101-b9f1-cc542c9fffae
ms.openlocfilehash: c543a0a4afc0d24205e5afd57cf6ca0732f3edf4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755042"
---
# <a name="compiler-error-c2869"></a>Erreur du compilateur C2869

'name' : a déjà été défini pour être un espace de noms

Vous ne pouvez pas réutiliser un nom déjà utilisé en tant qu’espace de noms.

L’exemple suivant génère l’C2869 :

```cpp
// C2869.cpp
// compile with: /c
namespace A { int i; };

class A {};   // C2869, A is already used
```
