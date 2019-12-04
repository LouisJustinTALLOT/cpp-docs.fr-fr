---
title: Erreur du compilateur C3163
ms.date: 11/04/2016
f1_keywords:
- C3163
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
ms.openlocfilehash: 436fb112758dfdec9997ff7e6dd7ef8f9dcdc66e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761775"
---
# <a name="compiler-error-c3163"></a>Erreur du compilateur C3163

'Construct' : les attributs ne sont pas cohérents avec la déclaration précédente

Le ou les attributs appliqués à une définition sont en conflit avec les attributs qui sont appliqués à une déclaration.

Une façon de résoudre C3163 consiste à éliminer les attributs de la déclaration anticipée. Les attributs d’une déclaration anticipée doivent être inférieurs aux attributs de la définition ou, au plus, égaux.

Une cause possible de l’erreur C3163 implique le langage SAL (Microsoft source code annotation Language). Les macros SAL ne se développent pas, sauf si vous compilez votre projet à l’aide de l’indicateur **/analyze** . Un programme qui se compile correctement sans/Analyze peut lever C3163 si vous tentez de le recompiler avec l’option/Analyze. Pour plus d’informations sur SAL, consultez [Annotations SAL](../../c-runtime-library/sal-annotations.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3163.

```cpp
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
