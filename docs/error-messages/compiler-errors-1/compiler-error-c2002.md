---
description: 'En savoir plus sur : erreur du compilateur C2002'
title: Erreur du compilateur C2002
ms.date: 11/04/2016
f1_keywords:
- C2002
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
ms.openlocfilehash: acf6e0679f2579d25d37ccf0c11965bc1d8b436a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298615"
---
# <a name="compiler-error-c2002"></a>Erreur du compilateur C2002

constante à caractères larges non valide

La constante à caractères multioctets n’est pas valide.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. La constante à caractères larges contient plus d’octets que prévu.

1. L’en-tête standard STDDEF. h n’est pas inclus.

1. Les caractères larges ne peuvent pas être concaténés avec des littéraux de chaîne ordinaires.

1. Une constante à caractères larges doit être précédée du caractère « L » :

    ```
    L'mbconst'
    ```

1. Pour Microsoft C++, les arguments de texte d’une directive de préprocesseur doivent être au format ASCII. Par exemple, la directive, `#pragma message(L"string")` , n’est pas valide.
