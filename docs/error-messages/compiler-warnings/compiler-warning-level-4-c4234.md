---
title: Avertissement du compilateur (niveau 4) C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: c27f16f7d2933ca1860b304afa6e04f96f0687f0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173905"
---
# <a name="compiler-warning-level-4-c4234"></a>Avertissement du compilateur (niveau 4) C4234

extension non standard utilisée : mot clé’keyword’réservé pour un usage ultérieur

Le compilateur n’implémente pas encore le mot clé que vous avez utilisé.

Cet avertissement est automatiquement promu en erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma AVERTISSEMENT](../../preprocessor/warning.md). Par exemple, pour faire de C4234 dans un numéro d’avertissement de niveau 4,

```cpp
#pragma warning(2:4234)
```

dans votre fichier de code source.
