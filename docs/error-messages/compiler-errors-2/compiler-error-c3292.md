---
title: Erreur du compilateur C3292
ms.date: 11/04/2016
f1_keywords:
- C3292
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
ms.openlocfilehash: a68d3e922532480063fe4c294e40f453885743e8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58780650"
---
# <a name="compiler-error-c3292"></a>Erreur du compilateur C3292

impossible de rouvrir l'espace de noms cli

L’espace de noms cli ne peut pas être déclaré dans votre code.  Pour plus d’informations, consultez [plateforme, par défaut et espaces de noms cli](../../extensions/platform-default-and-cli-namespaces-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3292.

```
// C3292.cpp
// compile with: /clr /c
namespace cli {};   // C3292
```