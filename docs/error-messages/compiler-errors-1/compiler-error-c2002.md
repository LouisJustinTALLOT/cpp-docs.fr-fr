---
title: Erreur du compilateur C2002
ms.date: 11/04/2016
f1_keywords:
- C2002
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
ms.openlocfilehash: c37a9b94be837248c8025a4fc069d8a242128542
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208245"
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

1. Pour Microsoft C++, les arguments de texte d’une directive de préprocesseur doivent être au format ASCII. Par exemple, la directive, `#pragma message(L"string")`, n’est pas valide.
