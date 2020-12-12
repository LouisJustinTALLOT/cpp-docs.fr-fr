---
description: 'En savoir plus sur : erreur du compilateur C2012'
title: Erreur du compilateur C2012
ms.date: 11/04/2016
f1_keywords:
- C2012
helpviewer_keywords:
- C2012
ms.assetid: 9f0d8162-c0b3-4234-a41f-836fdb75c84e
ms.openlocfilehash: 82f2a5660ec3920c9ff3db57c6ed0b70516c4531
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221005"
---
# <a name="compiler-error-c2012"></a>Erreur du compilateur C2012

nom manquant après' < '

Une directive `#include` ne contient pas le nom de fichier nécessaire.

L’exemple suivant génère l’erreur C2012 :

```cpp
// C2012.cpp
#include <   // C2012 include the filename to resolve
```

Solution possible :

```cpp
// C2012b.cpp
// compile with: /c
#include <stdio.h>
```
