---
description: 'En savoir plus sur : erreur du compilateur C2008'
title: Erreur du compilateur C2008
ms.date: 11/04/2016
f1_keywords:
- C2008
helpviewer_keywords:
- C2008
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
ms.openlocfilehash: 3fcde1885fd752a03a1285470a232f1daaa27df2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298524"
---
# <a name="compiler-error-c2008"></a>Erreur du compilateur C2008

'character' : inattendu dans la définition d’une macro

Le caractère s’affiche immédiatement après le nom de la macro. Pour résoudre l’erreur, il doit y avoir un espace après le nom de la macro.

L’exemple suivant génère l’C2008 :

```cpp
// C2008.cpp
#define TEST1"mytest1"    // C2008
```

Solution possible :

```cpp
// C2008b.cpp
// compile with: /c
#define TEST2 "mytest2"
```
