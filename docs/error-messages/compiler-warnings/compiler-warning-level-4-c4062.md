---
title: Avertissement du compilateur (niveau 4) C4062
ms.date: 04/05/2019
f1_keywords:
- C4062
helpviewer_keywords:
- C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
ms.openlocfilehash: 79658afc31565b708cdbd8a88f49b887cdd10cf3
ms.sourcegitcommit: 35c4b3478f8cc310ebbd932a18963ad8ab846ed9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59237183"
---
# <a name="compiler-warning-level-4-c4062"></a>Avertissement du compilateur (niveau 4) C4062

> énumérateur '*identificateur*'dans le switch de l’enum'*énumération*' n’est pas géré

L’énumérateur *identificateur* n’a pas associé `case` gestionnaire dans un `switch` instruction et qu’il existe aucune `default` étiquette qui puisse l’intercepter. Le cas manquant peut être une supervision et est une erreur potentielle dans votre code. Pour un avertissement connexe sur les énumérateurs inutilisés dans `switch` instructions qui ont un `default` cas, consultez [C4061](compiler-warning-level-4-c4061.md).

Cet avertissement est désactivé par défaut. Pour plus d’informations sur la façon d’activer des avertissements qui sont désactivés par défaut, consultez [du compilateur avertissements qui sont désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4062 et montre comment la corriger :

```cpp
// C4062.cpp
// compile with: /EHsc /W4
#pragma warning(default : 4062)
enum E { a, b, c };
void func ( E e ) {
   switch(e) {
      case a:
      case b:
   // case c:  // to fix, uncomment this line
      break;   // no default label
   }   // C4062, enumerator 'c' not handled
}

int main() {
}
```

## <a name="see-also"></a>Voir aussi

[Compilateur avertissement (niveau 4) C4061](compiler-warning-level-4-c4061.md)
