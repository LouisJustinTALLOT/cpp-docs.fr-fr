---
title: Compilateur avertissement (niveau 4) C4061
ms.date: 04/05/2019
f1_keywords:
- C4061
helpviewer_keywords:
- C4061
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
ms.openlocfilehash: 073e3e9cb1cb5bb6b0f66157c986072227960212
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59237118"
---
# <a name="compiler-warning-level-4-c4061"></a>Compilateur avertissement (niveau 4) C4061

> énumérateur '*identificateur*'dans le switch de l’enum'*énumération*' n’est pas géré explicitement par une étiquette case

L’énumérateur spécifié *identificateur* n’a aucun handler associé une `switch` instruction qui a un `default` cas. Le cas manquant peut être une supervision, ou il ne peut pas être un problème. Il dépend si l’énumérateur est géré par le cas par défaut ou non. Pour un avertissement connexe sur les énumérateurs inutilisés dans `switch` instructions qui n’ont pas `default` cas, consultez [C4062](compiler-warning-level-4-c4062.md).

Cet avertissement est désactivé par défaut. Pour plus d’informations sur la façon d’activer des avertissements qui sont désactivés par défaut, consultez [du compilateur avertissements qui sont désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C4061 ; Ajouter un cas de l’énumérateur manquante à corriger :

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

[Avertissement du compilateur (niveau 4) C4062](compiler-warning-level-4-c4062.md)
