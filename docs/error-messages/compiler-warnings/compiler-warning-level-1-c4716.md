---
title: Avertissement du compilateur (niveau 1) C4716
ms.date: 11/04/2016
f1_keywords:
- C4716
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
ms.openlocfilehash: 91e836c9bb606d7759206788d1e3abd63b293fa8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175309"
---
# <a name="compiler-warning-level-1-c4716"></a>Avertissement du compilateur (niveau 1) C4716

'fonction' doit retourner une valeur

La fonction donnée n’a pas retourné de valeur.

Seules les fonctions dont le type de retour est void peuvent utiliser la commande return sans valeur de retour associée.

Une valeur non définie est retournée lorsque cette fonction est appelée.

Cet avertissement est automatiquement promu en erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma AVERTISSEMENT](../../preprocessor/warning.md).

L’exemple suivant génère l’C4716 :

```cpp
// C4716.cpp
// compile with: /c /W1
// C4716 expected
#pragma warning(default:4716)
int test() {
   // uncomment the following line to resolve
   // return 0;
}
```
