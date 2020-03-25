---
title: Erreur du compilateur C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: 2aa922ebeadb374a7eac73a0f452376472b00984
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206026"
---
# <a name="compiler-error-c2383"></a>Erreur du compilateur C2383

'*symbol*' : les arguments par défaut ne sont pas autorisés sur ce symbole

Le C++ compilateur n’autorise pas les arguments par défaut des pointeurs vers les fonctions.

Ce code a été accepté par le C++ compilateur Microsoft dans les versions antérieures à Visual Studio 2005, mais il génère désormais une erreur. Pour le code qui fonctionne dans toutes les versions C++de Visual, n’assignez pas de valeur par défaut à un argument pointeur vers fonction.

## <a name="example"></a>Exemple

L’exemple suivant génère C2383 et affiche une solution possible :

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```
