---
title: Avertissement du compilateur (niveau 4) C4233
ms.date: 10/25/2017
f1_keywords:
- C4233
helpviewer_keywords:
- C4233
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
ms.openlocfilehash: 361e00b7361aab51ea077d7e248503f3654e5e58
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516517"
---
# <a name="compiler-warning-level-4-c4233"></a>Avertissement du compilateur (niveau 4) C4233

> extension non standard utilisée : '*mot clé*' mot clé uniquement pris en charge en C++, non en C

Le compilateur a compilé votre code source en tant que C plutôt que C++, et que vous avez utilisé un mot clé qui est uniquement valide en C++. Le compilateur compile votre fichier source en C si l’extension du fichier source est .c ou si vous utilisez [TP](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md).

Cet avertissement est automatiquement promu en une erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma warning](../../preprocessor/warning.md). Par exemple, pour que C4233 un niveau 4 avertissement, ajoutez cette ligne à votre fichier de code source :

```cpp
#pragma warning(4:4233)
```
