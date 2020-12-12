---
description: 'En savoir plus sur : erreur du compilateur C2092'
title: Erreur du compilateur C2092
ms.date: 11/04/2016
f1_keywords:
- C2092
helpviewer_keywords:
- C2092
ms.assetid: 037e44ae-16c8-489a-a512-dcdf7f7795a6
ms.openlocfilehash: 3f89d735d44b3cc0b2c28013ab957bf433159afb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251880"
---
# <a name="compiler-error-c2092"></a>Erreur du compilateur C2092

le type d’élément de tableau’array Name’ne peut pas être une fonction

Les tableaux de fonctions ne sont pas autorisés. Utilisez un tableau de pointeurs vers des fonctions.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C2092 :

```cpp
// C2092.cpp
typedef void (F) ();
typedef F AT[10];   // C2092
```

Solution possible :

```cpp
// C2092b.cpp
// compile with: /c
typedef void (F) ();
typedef F * AT[10];
```
