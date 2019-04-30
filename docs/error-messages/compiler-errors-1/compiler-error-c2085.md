---
title: Erreur du compilateur C2085
ms.date: 11/04/2016
f1_keywords:
- C2085
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
ms.openlocfilehash: a65e3c0ea622950b99b9ba83fc168b4718d13e46
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345707"
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