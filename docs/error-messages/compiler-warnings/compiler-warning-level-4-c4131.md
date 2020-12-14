---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4131'
title: Avertissement du compilateur (niveau 4) C4131
ms.date: 11/04/2016
f1_keywords:
- C4131
helpviewer_keywords:
- C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
ms.openlocfilehash: b4b54a38ad634b1cc0d444b0b6d5136b6a208626
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261786"
---
# <a name="compiler-warning-level-4-c4131"></a>Avertissement du compilateur (niveau 4) C4131

'fonction' : utilise un déclarateur obsolète

La déclaration de fonction spécifiée n’est pas sous forme de prototype.

Les anciennes déclarations de fonction doivent être converties sous forme de prototypes.

L’exemple suivant montre une ancienne déclaration de fonction :

```c
// C4131.c
// compile with: /W4 /c
void addrec( name, id ) // C4131 expected
char *name;
int id;
{ }
```

L’exemple suivant montre une forme de prototype :

```c
void addrec( char *name, int id )
{ }
```
