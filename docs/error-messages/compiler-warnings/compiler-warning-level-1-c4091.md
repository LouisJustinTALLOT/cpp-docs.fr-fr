---
title: Avertissement du compilateur (niveau 1) C4091
ms.date: 11/04/2016
f1_keywords:
- C4091
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
ms.openlocfilehash: 1a9fef0a825f98ab3ce8d935c98eefe1866be6cf
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684688"
---
# <a name="compiler-warning-level-1-c4091"></a>Avertissement du compilateur (niveau 1) C4091

'keyword' : ignoré à gauche de’type’quand aucune variable n’est déclarée

Le compilateur a détecté une situation dans laquelle l’utilisateur souhaitait probablement déclarer une variable, mais le compilateur n’a pas pu déclarer la variable.

## <a name="examples"></a>Exemples

Un **`__declspec`** attribut au début d’une déclaration de type défini par l’utilisateur s’applique à la variable de ce type. C4091 indique qu’aucune variable n’est déclarée. L’exemple suivant génère l’C4091.

```cpp
// C4091.cpp
// compile with: /W1 /c
__declspec(dllimport) class X {}; // C4091

// __declspec attribute applies to varX
__declspec(dllimport) class X2 {} varX;

// __declspec attribute after the class or struct keyword
// applies to user defined type
class __declspec(dllimport) X3 {};
```

Si un identificateur est un typedef, il ne peut pas également être un nom de variable. L’exemple suivant génère l’C4091.

```cpp
// C4091_b.cpp
// compile with: /c /W1 /WX
#define LIST 4
typedef struct _LIST {} LIST;   // C4091
```
