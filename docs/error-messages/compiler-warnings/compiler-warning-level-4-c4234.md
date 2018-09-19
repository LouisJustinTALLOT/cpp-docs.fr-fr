---
title: Compilateur avertissement (niveau 4) C4234 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4234
dev_langs:
- C++
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6ce6ba622cb480096144706589a01dee7326f38
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118230"
---
# <a name="compiler-warning-level-4-c4234"></a>Avertissement du compilateur (niveau 4) C4234

extension non standard utilisée : mot clé 'mot_clé' réservé pour une utilisation ultérieure

Le compilateur n’implémente pas encore le mot clé que vous avez utilisé.

Cet avertissement est automatiquement promu en une erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma warning](../../preprocessor/warning.md). Par exemple, pour que C4234 soit un avertissement de problème de niveau 4

```
#pragma warning(2:4234)
```

dans votre fichier de code source.