---
title: Avertissement du compilateur (niveau 2) C4094
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: c90ad202e193f21955d396dd2aff6b39d3a968c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174334"
---
# <a name="compiler-warning-level-2-c4094"></a>Avertissement du compilateur (niveau 2) C4094

'Token’sans balise n’a déclaré aucun symbole

Le compilateur a détecté une déclaration vide à l’aide d’une structure, d’une Union ou d’une classe sans balise. La déclaration est ignorée.

## <a name="example"></a>Exemple

```cpp
// C4094.cpp
// compile with: /W2
struct
{
};   // C4094

int main()
{
}
```

Cette condition génère une erreur sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
