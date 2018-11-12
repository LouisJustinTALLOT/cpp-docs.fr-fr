---
title: Erreur du compilateur C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: 06d4c19208bd242169e1cd07a71e8a568f46f7b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466090"
---
# <a name="compiler-error-c2383"></a>Erreur du compilateur C2383

«*symbole*' : les arguments par défaut ne sont pas autorisés sur ce symbole

Le compilateur C++ n’autorise pas les arguments par défaut pour les pointeurs de fonctions.

Ce code a été accepté par le compilateur Visual C++ dans les versions antérieures de Visual Studio 2005, mais génère maintenant une erreur. Pour le code qui fonctionne dans toutes les versions de Visual C++, n’attribuez pas une valeur par défaut à un argument de pointeur de fonction.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C2383 et montre une solution possible :

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```