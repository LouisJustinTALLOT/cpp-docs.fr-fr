---
title: Avertissement du compilateur (niveau 4) C4019
ms.date: 11/04/2016
f1_keywords:
- C4019
helpviewer_keywords:
- C4019
ms.assetid: 4ecfe85d-673f-4334-8154-36fe7f0b3444
ms.openlocfilehash: d2bfec799b8b2981914b76839e51b7a0d09b30ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401473"
---
# <a name="compiler-warning-level-4-c4019"></a>Avertissement du compilateur (niveau 4) C4019

instruction vide au niveau de la portée globale

Un point-virgule compris dans une portée globale n’est pas précédé d’une instruction.

Cet avertissement peut être résolu si vous supprimez le point-virgule supplémentaire.

## <a name="example"></a>Exemple

```
// C4019.c
// compile with: /Za /W4
#define declint( varname ) int varname;
declint( a );   // C4019, int a;;
declint( b )   // OK, int b;

int main()
{
}
```