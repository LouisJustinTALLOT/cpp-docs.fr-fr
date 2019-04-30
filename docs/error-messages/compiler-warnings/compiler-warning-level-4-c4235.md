---
title: Avertissement du compilateur (niveau 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: 80ad388b26b2b972aa1301c1f335d0361a75f15f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401044"
---
# <a name="compiler-warning-level-4-c4235"></a>Avertissement du compilateur (niveau 4) C4235

extension non standard utilisée : mot clé 'mot_clé' non pris en charge sur cette architecture

Le compilateur ne prend pas en charge le mot clé que vous avez utilisé.

Cet avertissement est automatiquement promu en une erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma warning](../../preprocessor/warning.md). Par exemple, pour transformer C4235 en un avertissement de niveau 2, utilisez la ligne de code suivante

```
#pragma warning(2:4235)
```

dans votre fichier de code source.