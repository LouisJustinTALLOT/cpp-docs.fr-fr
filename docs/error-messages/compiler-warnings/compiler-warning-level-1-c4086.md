---
title: Avertissement du compilateur (niveau 1) C4086
ms.date: 11/04/2016
f1_keywords:
- C4086
helpviewer_keywords:
- C4086
ms.assetid: 9248831b-22bf-47af-8684-bfadb17e94fc
ms.openlocfilehash: dc841016218efa365f7cd9c098efbfe6748cca5d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626848"
---
# <a name="compiler-warning-level-1-c4086"></a>Avertissement du compilateur (niveau 1) C4086

le paramètre pragma attendu doit être '1', '2', '4', '8', ou '16'

Le paramètre pragma n’a pas la valeur requise (1, 2, 4, 8 ou 16).

## <a name="example"></a>Exemple

```cpp
// C4086.cpp
// compile with: /W1 /LD
#pragma pack( 3 ) // C4086
```