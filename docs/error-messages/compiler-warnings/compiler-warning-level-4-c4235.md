---
title: Avertissement du compilateur (niveau 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: 3e3cb2e40ed42b24ee52252003b26ec09cd86710
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541757"
---
# <a name="compiler-warning-level-4-c4235"></a>Avertissement du compilateur (niveau 4) C4235

extension non standard utilisée : mot clé’keyword’non pris en charge dans cette architecture

Le compilateur ne prend pas en charge le mot clé que vous avez utilisé.

Cet avertissement est automatiquement promu en erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma AVERTISSEMENT](../../preprocessor/warning.md). Par exemple, pour faire de C4235 dans un avertissement de niveau 2, utilisez la ligne de code suivante

```cpp
#pragma warning(2:4235)
```

dans votre fichier de code source.