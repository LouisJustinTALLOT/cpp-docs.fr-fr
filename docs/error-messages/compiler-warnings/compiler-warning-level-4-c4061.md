---
title: Avertissement du compilateur (niveau 4) C4061
ms.date: 04/05/2019
f1_keywords:
- C4061
helpviewer_keywords:
- C4061
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
ms.openlocfilehash: 18c5a51e24af36c5a330e10a66ce3dcc38295fb1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225278"
---
# <a name="compiler-warning-level-4-c4061"></a>Avertissement du compilateur (niveau 4) C4061

> l’énumérateur'*identifier*'dans le commutateur de l’enum'*Enumeration*'n’est pas géré explicitement par une étiquette case

L' *identificateur* d’énumérateur spécifié n’est associé à aucun gestionnaire dans une **`switch`** instruction qui a un **`default`** cas. Il se peut que le cas manquant soit un point de vue ou qu’il ne s’agit pas d’un problème. Elle peut dépendre du fait que l’énumérateur est ou non géré par le cas par défaut. Pour obtenir un avertissement connexe sur les énumérateurs inutilisés dans les **`switch`** instructions qui n’ont pas de **`default`** cas, consultez [C4062](compiler-warning-level-4-c4062.md).

Cet avertissement est désactivé par défaut. Pour plus d’informations sur l’activation des avertissements désactivés par défaut, consultez [avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4061 ; Ajoutez un cas pour l’énumérateur manquant à corriger :

```cpp
// C4061.cpp
// compile with: /W4
#pragma warning(default : 4061)

enum E { a, b, c };
void func ( E e )
{
   switch(e)
   {
      case a:
      case b:
      default:
         break;
   }   // C4061 c' not handled
}

int main()
{
}
```

## <a name="see-also"></a>Voir aussi

[Avertissement du compilateur (niveau 4) C4062](compiler-warning-level-4-c4062.md)
