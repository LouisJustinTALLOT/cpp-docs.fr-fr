---
title: Erreur du compilateur C3163
ms.date: 11/04/2016
f1_keywords:
- C3163
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
ms.openlocfilehash: eda3910c99f4c8ea96568f2d475c5d6a1e4cdc7c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041044"
---
# <a name="compiler-error-c3163"></a>Erreur du compilateur C3163

'construct' : attributs non cohérents avec la déclaration précédente

L’ou les attributs qui sont appliqué à une définition en conflit avec l’ou les attributs qui sont appliqué à une déclaration.

Pour résoudre C3163 consiste à éliminer les attributs de la déclaration anticipée. Tous les attributs sur une déclaration anticipée doivent être inférieure aux attributs sur la définition ou égaux pour eux.

Une cause possible de l’erreur C3163 implique le langage d’annotation du code source Microsoft (SAL). Les macros SAL ne développez pas sauf si vous compilez votre projet à l’aide de la **/ analyze** indicateur. Un programme qui se compile correctement sans /ANALYZE peut lever C3163 si vous tentez de le recompiler avec l’option /Analyze. Pour plus d’informations sur SAL, consultez [Annotations SAL](../../c-runtime-library/sal-annotations.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3163.

```
// C3163.cpp
// compile with: /clr /c
using namespace System;

[CLSCompliant(true)] void f();
[CLSCompliant(false)] void f() {}   // C3163
// try the following line instead
// [CLSCompliant(true)] void f() {}
```

## <a name="see-also"></a>Voir aussi

[Annotations SAL](../../c-runtime-library/sal-annotations.md)