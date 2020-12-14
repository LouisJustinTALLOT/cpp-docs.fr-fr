---
description: 'En savoir plus sur : erreur du compilateur C3163'
title: Erreur du compilateur C3163
ms.date: 11/04/2016
f1_keywords:
- C3163
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
ms.openlocfilehash: 53d0135e3083de7727b2a6c7f51a3f75e7314405
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203950"
---
# <a name="compiler-error-c3163"></a>Erreur du compilateur C3163

> '*Construct*' : les attributs ne sont pas cohérents avec la déclaration précédente

Le ou les attributs appliqués à une définition sont en conflit avec les attributs qui sont appliqués à une déclaration.

Une façon de résoudre C3163 consiste à éliminer les attributs de la déclaration anticipée. Les attributs d’une déclaration anticipée doivent être inférieurs aux attributs de la définition ou, au plus, égaux.

Une cause possible de l’erreur C3163 implique le langage SAL (Microsoft source code annotation Language). Les macros SAL ne se développent pas, sauf si vous compilez votre projet à l’aide de l' **`/analyze`** indicateur. Programme qui se compile correctement sans **`/analyze`** peut lever C3163 si vous tentez de le recompiler avec l' **`/analyze`** option. Pour plus d’informations sur SAL, consultez [Annotations SAL](../../c-runtime-library/sal-annotations.md).

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
