---
title: Avertissement du compilateur (niveau 4) C4256
ms.date: 11/04/2016
f1_keywords:
- C4256
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
ms.openlocfilehash: e087e3cd36ab85d6f3f6b5cfed1b55cac66ea142
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541701"
---
# <a name="compiler-warning-level-4-c4256"></a>Avertissement du compilateur (niveau 4) C4256

'fonction' : le constructeur pour la classe avec des bases virtuelles a'... '; les appels peuvent ne pas être compatibles avec les versions antérieures de VisualC++

Incompatibilité possible.

Prenez l'exemple du code suivant. Si la définition du constructeur S2 :: S2 (int i,...) a été compilée à l’aide d’une version C++ du compilateur Microsoft antérieure à la version 7, mais que l’exemple suivant est compilé à l’aide de la version actuelle, l’appel au constructeur pour S3 ne fonctionnera pas correctement en raison d’une modification de convention d’appel de cas spécial. Si les deux étaient compilés à C++ l’aide de Visual 6,0, l’appel ne fonctionnerait pas non plus correctement, à moins qu’aucun paramètre ne soit passé pour les points de suspension.

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