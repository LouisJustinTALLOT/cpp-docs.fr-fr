---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4235'
title: Avertissement du compilateur (niveau 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: 011586efb311cab1da5cd4452bbbc03a942a5045
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334891"
---
# <a name="compiler-warning-level-4-c4235"></a>Avertissement du compilateur (niveau 4) C4235

extension non standard utilisée : mot clé’keyword’non pris en charge dans cette architecture

Le compilateur ne prend pas en charge le mot clé que vous avez utilisé.

Cet avertissement est automatiquement promu en erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma AVERTISSEMENT](../../preprocessor/warning.md). Par exemple, pour faire de C4235 dans un avertissement de niveau 2, utilisez la ligne de code suivante

```cpp
#pragma warning(2:4235)
```

dans votre fichier de code source.
