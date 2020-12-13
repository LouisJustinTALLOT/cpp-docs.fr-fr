---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4233'
title: Avertissement du compilateur (niveau 4) C4233
ms.date: 10/25/2017
f1_keywords:
- C4233
helpviewer_keywords:
- C4233
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
ms.openlocfilehash: 3e797bcefeaeee615014ea8e0bd109e4cf4ffbef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344014"
---
# <a name="compiler-warning-level-4-c4233"></a>Avertissement du compilateur (niveau 4) C4233

> extension non standard utilisée : mot clé'*Keyword*'pris en charge uniquement en C++, et non en C

Le compilateur a compilé votre code source en tant que C plutôt que C++, et vous avez utilisé un mot clé qui est uniquement valide en C++. Le compilateur compile votre fichier source en tant que C si l’extension du fichier source est. c ou si vous utilisez [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md).

Cet avertissement est automatiquement promu en erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma AVERTISSEMENT](../../preprocessor/warning.md). Par exemple, pour faire de C4233 dans un numéro d’avertissement de niveau 4, ajoutez la ligne suivante à votre fichier de code source :

```cpp
#pragma warning(4:4233)
```
