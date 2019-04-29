---
title: Compilateur avertissement (niveau 1) C4144
ms.date: 11/04/2016
f1_keywords:
- C4144
helpviewer_keywords:
- C4144
ms.assetid: a37b445d-dbc6-43b4-8d95-ffd0e4225464
ms.openlocfilehash: b2406357baf70e45566f2d2f25839d151bac4186
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352947"
---
# <a name="compiler-warning-level-1-c4144"></a>Compilateur avertissement (niveau 1) C4144

'expression' : expression relationnelle comme expression de switch

L’expression relationnelle spécifiée a été utilisée comme expression de contrôle d’un [basculer](../../cpp/switch-statement-cpp.md) instruction. Les instructions case associées seront proposées dans les valeurs booléennes. L’exemple suivant génère l’erreur C4144 :

```
// C4144.cpp
// compile with: /W1
int main()
{
   int i = 0;
   switch(!i) {   // C4144, remove the ! to resolve
      case 1:
         break;
      default:
         break;
   }
}
```