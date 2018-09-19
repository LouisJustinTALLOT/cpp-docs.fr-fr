---
title: Erreur du compilateur C2085 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2085
dev_langs:
- C++
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d88968e49e38a13782dde2d905a614ad4d177e81
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082376"
---
# <a name="compiler-error-c2085"></a>Erreur du compilateur C2085

'identificateur' : pas dans la liste de paramètres formels

L’identificateur a été déclaré dans une définition de fonction mais pas dans la liste de paramètres formels. (C ANSI uniquement)

L’exemple suivant génère l’erreur C2085 :

```
// C2085.c
void func1( void )
int main( void ) {}   // C2085
```

Solution possible :

```
// C2085b.c
void func1( void );
int main( void ) {}
```

Sans le point-virgule, `func1()` ressemble à une définition de fonction, pas un prototype, donc `main` est défini dans `func1()`, erreur C2085 pour l’identificateur `main`.