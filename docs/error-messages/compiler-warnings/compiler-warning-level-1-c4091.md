---
title: Compilateur avertissement (niveau 1) C4091
ms.date: 11/04/2016
f1_keywords:
- C4091
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
ms.openlocfilehash: 87432a74dfe7c09a52f436d4e91b3f70eb66856b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491739"
---
# <a name="compiler-warning-level-1-c4091"></a>Compilateur avertissement (niveau 1) C4091

'keyword' : ignoré à gauche de 'type' quand aucune variable est déclarée.

Le compilateur a détecté une situation où l’utilisateur attendait probablement une variable qui doit être déclaré, mais le compilateur n’a pas pu déclarer la variable.

## <a name="example"></a>Exemple

Un `__declspec` attribut situé au début d’une déclaration de type défini par l’utilisateur s’applique à la variable de ce type. C4091 indique qu’aucune variable est déclarée. L’exemple suivant génère C4091.

```
// C4091.cpp
// compile with: /W1 /c
__declspec(dllimport) class X {}; // C4091

// __declspec attribute applies to varX
__declspec(dllimport) class X2 {} varX;

// __declspec attribute after the class or struct keyword
// applies to user defined type
class __declspec(dllimport) X3 {};
```

## <a name="example"></a>Exemple

Si un identificateur est un typedef, il ne peut pas également être un nom de variable. L’exemple suivant génère C4091.

```
// C4091_b.cpp
// compile with: /c /W1 /WX
#define LIST 4
typedef struct _LIST {} LIST;   // C4091
```