---
description: 'En savoir plus sur : avertissement du compilateur (niveau 2) C4094'
title: Avertissement du compilateur (niveau 2) C4094
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: 63c554703c1eb6f7ecb831d1046641a0cde2094a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326529"
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
