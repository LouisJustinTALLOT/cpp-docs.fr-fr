---
title: Erreur du compilateur C2085
ms.date: 11/04/2016
f1_keywords:
- C2085
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
ms.openlocfilehash: 7dbf7266a6330a1fdb46d7f2df90e7684f026d9a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301962"
---
# <a name="compiler-error-c2085"></a>Erreur du compilateur C2085

'identificateur' : pas dans la liste de paramètres formels

L’identificateur a été déclaré dans une définition de fonction, mais pas dans la liste de paramètres formels. (C ANSI uniquement)

L’exemple suivant génère l’C2085 :

```c
// C2085.c
void func1( void )
int main( void ) {}   // C2085
```

Solution possible :

```c
// C2085b.c
void func1( void );
int main( void ) {}
```

Avec le point-virgule manquant, `func1()` ressemble à une définition de fonction, pas à un prototype, donc `main` est défini dans `func1()`, générant l’erreur C2085 pour l’identificateur `main`.
