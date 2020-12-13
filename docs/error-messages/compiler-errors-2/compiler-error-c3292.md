---
description: 'En savoir plus sur : erreur du compilateur C3292'
title: Erreur du compilateur C3292
ms.date: 11/04/2016
f1_keywords:
- C3292
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
ms.openlocfilehash: 5c20ae5a03fd6eab442384c91c3357c2d9edb214
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97144688"
---
# <a name="compiler-error-c3292"></a>Erreur du compilateur C3292

impossible de rouvrir l'espace de noms cli

L’espace de noms cli ne peut pas être déclaré dans votre code.  Consultez [Plateforme, valeur par défaut et espaces de noms cli](../../extensions/platform-default-and-cli-namespaces-cpp-component-extensions.md) pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3292.

```cpp
// C3292.cpp
// compile with: /clr /c
namespace cli {};   // C3292
```
