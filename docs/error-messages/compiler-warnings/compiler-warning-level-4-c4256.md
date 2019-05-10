---
title: Avertissement du compilateur (niveau 4) C4256
ms.date: 11/04/2016
f1_keywords:
- C4256
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
ms.openlocfilehash: 3e8a3ab1b11c719730016e6a0cd248770cd89af8
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447777"
---
# <a name="compiler-warning-level-4-c4256"></a>Avertissement du compilateur (niveau 4) C4256

'fonction' : constructeur de classe avec bases virtuelles a '...' ; appels ne seront ne peut-être pas compatibles avec les versions antérieures de Visual C++

Incompatibilité possible.

Prenons l’exemple de code suivant. Si la définition du constructeur S2::S2 (int i,...) a été compilé à l’aide d’une version de Microsoft C++ compilateur avant version 7, mais l’exemple suivant est compilé à l’aide de la version actuelle, l’appel au constructeur pour S3 ne fonctionnerait pas correctement en raison d’une modification de la convention d’appel de cas spéciaux. Si les deux ont été compilés à l’aide de Visual C++ 6.0, l’appel fonctionnerait pas tout à fait à droite, sauf si aucun paramètre ont été passés pour les points de suspension.

Pour résoudre cet avertissement,

1. N’utilisez pas dans un constructeur de points de suspension.

1. Assurez-vous que tous les composants dans leur projet sont générés avec la version actuelle (y compris les bibliothèques pouvant définir ou référencer cette classe), puis désactivez l’avertissement à l’aide de la [avertissement](../../preprocessor/warning.md) pragma.

L’exemple suivant génère l’erreur C4256 :

```
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