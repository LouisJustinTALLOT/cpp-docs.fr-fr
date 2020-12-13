---
description: 'En savoir plus sur : erreur du compilateur C2869'
title: Erreur du compilateur C2869
ms.date: 11/04/2016
f1_keywords:
- C2869
helpviewer_keywords:
- C2869
ms.assetid: 6e30c001-47f3-4101-b9f1-cc542c9fffae
ms.openlocfilehash: 53171af019de9e099e2135747a8ce4d63c526b1e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333773"
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
