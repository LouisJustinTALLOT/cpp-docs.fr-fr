---
description: 'En savoir plus sur : erreur du compilateur C2383'
title: Erreur du compilateur C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: 862346d7f2bfe92a5d2182a7fe53f260b357ad0b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185932"
---
# <a name="compiler-error-c2383"></a>Erreur du compilateur C2383

'*symbol*' : les arguments par défaut ne sont pas autorisés sur ce symbole

Le compilateur C++ n’autorise pas les arguments par défaut des pointeurs vers les fonctions.

Ce code a été accepté par le compilateur Microsoft C++ dans les versions antérieures à Visual Studio 2005, mais il génère désormais une erreur. Pour le code qui fonctionne dans toutes les versions de Visual C++, n’assignez pas de valeur par défaut à un argument pointeur vers fonction.

## <a name="example"></a>Exemple

L’exemple suivant génère C2383 et affiche une solution possible :

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```
