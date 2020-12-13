---
description: 'En savoir plus sur : erreur du compilateur C3132'
title: Erreur du compilateur C3132
ms.date: 11/04/2016
f1_keywords:
- C3132
helpviewer_keywords:
- C3132
ms.assetid: d54a3d12-336a-4ed0-ad4e-43cddac33b5e
ms.openlocfilehash: e81ddcb977342a687dce329239a590f90eca67ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177391"
---
# <a name="compiler-error-c3132"></a>Erreur du compilateur C3132

'fonction-Parameter' : les tableaux de paramètres ne peuvent être appliqués qu’à un argument formel de type’Single-Dimensional Managed array'

L' <xref:System.ParamArrayAttribute> attribut a été appliqué à un paramètre qui n’est pas un tableau à une seule dimension.

L’exemple suivant génère l’C3132 :

```cpp
// C3132.cpp
// compile with: /clr /c
using namespace System;
void f( [ParamArray] Int32[,] );   // C3132
void g( [ParamArray] Int32[] );   // C3132

void h( [ParamArray] array<Char ^> ^ MyArray );   // OK
```
