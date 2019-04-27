---
title: Erreur du compilateur C2002
ms.date: 11/04/2016
f1_keywords:
- C2002
helpviewer_keywords:
- C2002
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
ms.openlocfilehash: 30f472aa7a9475a19eea0e92fe5c2ea0d54e382b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209034"
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