---
title: Compilateur avertissement (niveau 4) C4233 | Documents Microsoft
ms.custom: ''
ms.date: 10/25/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4233
dev_langs:
- C++
helpviewer_keywords:
- C4233
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a933d41fd8e7cf3b94e458efff72193b8ce5e187
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297834"
---
# <a name="compiler-warning-level-4-c4233"></a>Avertissement du compilateur (niveau 4) C4233

> extension non standard utilisée : '*mot clé*' mot clé uniquement pris en charge en C++, non en C

Le compilateur a compilé votre code source C plutôt que C++, et que vous avez utilisé un mot clé qui n’est pas valide en C++. Le compilateur compile votre fichier source en C si l’extension du fichier source est .c ou si vous utilisez [/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md).

Cet avertissement est automatiquement promu en une erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma warning](../../preprocessor/warning.md). Par exemple, pour que C4233 soit un problème d’avertissement de niveau 4, ajoutez cette ligne à votre fichier de code source :

```cpp
#pragma warning(4:4233)
```
