---
title: Erreur du compilateur C3132
ms.date: 11/04/2016
f1_keywords:
- C3132
helpviewer_keywords:
- C3132
ms.assetid: d54a3d12-336a-4ed0-ad4e-43cddac33b5e
ms.openlocfilehash: 1a97e04747cb92909380e66d1f4ea8ca62183054
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424169"
---
# <a name="compiler-error-c3132"></a>Erreur du compilateur C3132

'paramètre de fonction' : les tableaux de paramètres peuvent uniquement être appliqués à un argument formel de type 'single-dimensional managed array'

Le <xref:System.ParamArrayAttribute> attribut a été appliqué à un paramètre qui n’était pas un tableau unidimensionnel.

L’exemple suivant génère l’erreur C3132 :

```
// C3132.cpp
// compile with: /clr /c
using namespace System;
void f( [ParamArray] Int32[,] );   // C3132
void g( [ParamArray] Int32[] );   // C3132

void h( [ParamArray] array<Char ^> ^ MyArray );   // OK
```