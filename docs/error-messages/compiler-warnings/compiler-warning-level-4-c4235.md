---
title: Compilateur avertissement (niveau 4) C4235 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4235
dev_langs:
- C++
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9e709017e51101efe53a8697bb145014f200871
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031819"
---
# <a name="compiler-warning-level-4-c4235"></a>Avertissement du compilateur (niveau 4) C4235

extension non standard utilisée : mot clé 'mot_clé' non pris en charge sur cette architecture

Le compilateur ne prend pas en charge le mot clé que vous avez utilisé.

Cet avertissement est automatiquement promu en une erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma warning](../../preprocessor/warning.md). Par exemple, pour transformer C4235 en un avertissement de niveau 2, utilisez la ligne de code suivante

```
#pragma warning(2:4235)
```

dans votre fichier de code source.