---
title: Erreur du compilateur C3292 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3292
dev_langs:
- C++
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8fc5f89978a7ecaff526fa05ca7a47494aada987
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112458"
---
# <a name="compiler-error-c3292"></a>Erreur du compilateur C3292

impossible de rouvrir l'espace de noms cli

L’espace de noms cli ne peut pas être déclaré dans votre code.  Pour plus d’informations, consultez [plateforme, par défaut et espaces de noms cli](../../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3292.

```
// C3292.cpp
// compile with: /clr /c
namespace cli {};   // C3292
```