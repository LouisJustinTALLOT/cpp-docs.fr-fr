---
title: Avertissement du compilateur (niveau 4) C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: 63a22fed0832677837eb786268fc92946d295b79
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541773"
---
# <a name="compiler-warning-level-4-c4234"></a>Avertissement du compilateur (niveau 4) C4234

extension non standard utilisée : mot clé’keyword’réservé pour un usage ultérieur

Le compilateur n’implémente pas encore le mot clé que vous avez utilisé.

Cet avertissement est automatiquement promu en erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma AVERTISSEMENT](../../preprocessor/warning.md). Par exemple, pour faire de C4234 dans un numéro d’avertissement de niveau 4,

```cpp
#pragma warning(2:4234)
```

dans votre fichier de code source.