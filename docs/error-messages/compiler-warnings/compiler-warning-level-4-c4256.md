---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4256'
title: Avertissement du compilateur (niveau 4) C4256
ms.date: 11/04/2016
f1_keywords:
- C4256
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
ms.openlocfilehash: 3ccd8447f930f40df5e488714cdcfb52e54d9928
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189299"
---
# <a name="compiler-warning-level-4-c4256"></a>Avertissement du compilateur (niveau 4) C4256

'fonction' : le constructeur pour la classe avec des bases virtuelles a'... '; les appels peuvent ne pas être compatibles avec les versions antérieures de Visual C++

Incompatibilité possible.

Considérez l’exemple de code suivant. Si la définition du constructeur S2 :: S2 (int i,...) a été compilée à l’aide d’une version du compilateur Microsoft C++ antérieure à la version 7, mais que l’exemple suivant est compilé à l’aide de la version actuelle, l’appel au constructeur pour S3 ne fonctionnera pas correctement en raison d’une modification de convention d’appel de cas spécial. Si les deux étaient compilés à l’aide de Visual C++ 6,0, l’appel ne fonctionnerait pas non plus correctement, à moins qu’aucun paramètre ne soit passé pour les points de suspension.

Pour résoudre cet avertissement,

1. N’utilisez pas de points de suspension dans un constructeur.

1. Assurez-vous que tous les composants de leur projet sont générés avec la version actuelle (y compris toutes les bibliothèques pouvant définir ou référencer cette classe), puis désactivez l’avertissement à l’aide du pragma [Warning](../../preprocessor/warning.md) .

L’exemple suivant génère l’C4256 :

```cpp
// C4256.cpp
// compile with: /W4
// #pragma warning(disable : 4256)
struct S1
{
};

struct S2: virtual public S1
{
   S2( int i, ... )    // C4256
   {
      i = 0;
   }
   /*
   // try the following line instead
   S2( int i)
   {
      i = 0;
   }
   */
};

void func1()
{
   S2 S3( 2, 1, 2 );   // C4256
   // try the following line instead
   // S2 S3( 2 );
}

int main()
{
}
```
