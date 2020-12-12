---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4928'
title: Avertissement du compilateur (niveau 1) C4928
ms.date: 11/04/2016
f1_keywords:
- C4928
helpviewer_keywords:
- C4928
ms.assetid: 77235d7f-9360-45cb-8348-d148c605c4a3
ms.openlocfilehash: 15cf688a01ef62b6c76b8be5a61d43d436cfe790
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203612"
---
# <a name="compiler-warning-level-1-c4928"></a>Avertissement du compilateur (niveau 1) C4928

initialisation de copie non conforme ; plusieurs conversions définies par l'utilisateur ont été appliquées implicitement

Plusieurs routines de conversion définies par l’utilisateur ont été trouvées. Le compilateur a exécuté le code dans toutes les routines de ce type.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’C4928 :

```cpp
// C4928.cpp
// compile with: /W1
#pragma warning(default: 4928)

struct I
{
};

struct I1 : I
{
};

struct I2 : I
{
};

template <class T>
struct Ptr
{
   operator T*()
   {
      return 0;
   }

   Ptr()
   {
   }

   Ptr(I*)
   {
   }
};

int main()
{
   Ptr<I1> p1;
   Ptr<I2> p2 = p1;   // C4928
   // try one of the following two lines to resolve this error
   // Ptr<I2> p2(p1);
   // Ptr<I2> p2 = (I1*) p1;
}
```
