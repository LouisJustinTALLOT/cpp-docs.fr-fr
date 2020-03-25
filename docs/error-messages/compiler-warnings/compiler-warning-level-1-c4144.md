---
title: Avertissement du compilateur (niveau 1) C4144
ms.date: 11/04/2016
f1_keywords:
- C4144
helpviewer_keywords:
- C4144
ms.assetid: a37b445d-dbc6-43b4-8d95-ffd0e4225464
ms.openlocfilehash: 99902edee371704c57a772e1b62f7ec4f41afb36
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163687"
---
# <a name="compiler-warning-level-1-c4144"></a>Avertissement du compilateur (niveau 1) C4144

'expression' : expression relationnelle comme expression de switch

L’expression relationnelle spécifiée a été utilisée en tant qu’expression de contrôle d’une instruction [switch](../../cpp/switch-statement-cpp.md) . Les instructions case associées recevront des valeurs booléennes. L’exemple suivant génère l’C4144 :

```cpp
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
