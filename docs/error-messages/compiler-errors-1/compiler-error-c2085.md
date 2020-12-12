---
description: 'En savoir plus sur : erreur du compilateur C2085'
title: Erreur du compilateur C2085
ms.date: 11/04/2016
f1_keywords:
- C2085
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
ms.openlocfilehash: 2cd828c9a18c06c5794bef01ba861f702af2e096
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97252114"
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

Avec le point-virgule manquant, `func1()` qui ressemble à une définition de fonction, et non à un prototype, `main` est défini dans `func1()` , générant l’erreur C2085 pour l’identificateur `main` .
