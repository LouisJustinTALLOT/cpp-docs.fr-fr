---
title: Erreur du compilateur C2057
ms.date: 11/04/2016
f1_keywords:
- C2057
helpviewer_keywords:
- C2057
ms.assetid: 038a99d6-1f5a-42fa-8449-03b4ff11ee0b
ms.openlocfilehash: 6c8b171a878a8f370a024fa7374be6925695bd4d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548705"
---
# <a name="compiler-error-c2057"></a>Erreur du compilateur C2057

expression constante attendue

Le contexte requiert une expression constante, une expression dont la valeur est connue au moment de la compilation.

Le compilateur doit connaître la taille d'un type au moment de la compilation pour allouer de l'espace pour une instance de ce type.

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C2057 et montre comment la corriger :

```
// C2057.cpp
int i;
int b[i];   // C2057 - value of i is unknown at compile time
int main() {
   const int i = 8;
   int b[i]; // OK - value of i is fixed and known to compiler
}
```

## <a name="example"></a>Exemple

C possède des règles plus restrictives pour les expressions constantes.  L'exemple suivant génère l'erreur C2057 et montre comment la corriger :

```
// C2057b.c
#define ArraySize1 10
int main() {
   const int ArraySize2 = 10;
   int h[ArraySize2];   // C2057 - C does not allow variables here
   int h[ArraySize1];   // OK - uses preprocessor constant
}
```