---
title: Erreur du compilateur C2002 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2002
dev_langs:
- C++
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b87a7fe1513c695344676624ae1968060097c885
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116917"
---
# <a name="compiler-error-c2002"></a>Erreur du compilateur C2002

constante à caractères larges non valide

La constante à caractères multioctets n’est pas valide.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. La constante à caractères larges contient davantage d’octets que prévu.

1. L’en-tête standard STDDEF.h n’est pas inclus.

1. Caractères larges ne peut pas être concaténés avec des littéraux de chaîne ordinaires.

1. Une constante à caractères larges doit être précédée par le caractère « L » :

    ```
    L'mbconst'
    ```

1. Pour Microsoft C++, les arguments de texte d’une directive de préprocesseur doivent être ASCII. Par exemple, la directive, `#pragma message(L"string")`, n’est pas valide.