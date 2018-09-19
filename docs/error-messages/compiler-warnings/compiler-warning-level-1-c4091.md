---
title: Compilateur avertissement (niveau 1) C4091 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4091
dev_langs:
- C++
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b8fd377ed8b1f6425f0a1c13a83531fca1b797f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114096"
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