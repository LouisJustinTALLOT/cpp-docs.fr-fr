---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4608'
title: Avertissement du compilateur (niveau 3) C4608
ms.date: 11/04/2016
f1_keywords:
- C4608
helpviewer_keywords:
- C4608
ms.assetid: 8b8f5f28-8ce9-457e-9d3d-a8c0efce9b6a
ms.openlocfilehash: 988a51a84e807a342553bc6f1787bd4e2c20d3cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339876"
---
# <a name="compiler-warning-level-3-c4608"></a>Avertissement du compilateur (niveau 3) C4608

'union_member' a déjà été initialisé par un autre membre union dans la liste des initialiseurs, 'union_member'

Deux membres de la même union ont été initialisés dans une liste d'initialisations. Vous ne pouvez accéder qu'à un seul membre de l'union.

L'exemple suivant génère l'erreur C4608 :

```cpp
// C4608.cpp
// compile with: /W3 /c
class X {
public:
   X(char c) : m_i( c + 1), m_c(c) {}   // C4608
   // try the following line instead
   // X(char c) : m_c(c) {}

private:
   union {
      int m_i;
      char m_c;
   };
};

union Y {
public:
   Y(char * name) : m_number(0.3), m_string( name ) {} // C4608

private:
   double m_number;
   char * m_string;
};
```
