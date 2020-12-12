---
description: 'En savoir plus sur : setlocale pragma'
title: setlocale, pragma
ms.date: 08/29/2019
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
ms.openlocfilehash: 375a2075381b39037a6a723f7d28ef73749ec08f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167303"
---
# <a name="setlocale-pragma"></a>setlocale, pragma

Définit les *paramètres régionaux*, le pays, la région et la langue à utiliser lors de la traduction des constantes à caractères larges et des littéraux de chaîne.

## <a name="syntax"></a>Syntaxe

> **#pragma setlocale ("** [ *locale-String* ] **")**

## <a name="remarks"></a>Notes

Étant donné que l’algorithme de conversion de caractères multioctets en caractères larges peut varier selon les paramètres régionaux, ou si la compilation peut avoir lieu dans des paramètres régionaux différents de l’emplacement où un fichier exécutable sera exécuté, ce pragma offre un moyen de spécifier les paramètres régionaux cibles au moment de la compilation. Elle garantit que les chaînes à caractères larges sont stockées dans le format approprié.

Les *paramètres régionaux* par défaut sont «».

Les paramètres régionaux « C » mappent chaque caractère de la chaîne à sa valeur en tant que **`wchar_t`** . Les autres valeurs valides pour `setlocale` sont les entrées trouvées dans la liste des [chaînes de langue](../c-runtime-library/language-strings.md) . Par exemple, vous pouvez spécifier :

```cpp
#pragma setlocale("dutch")
```

La possibilité de spécifier une chaîne de langue dépend de la prise en charge de la page de codes et de l’ID de langue sur votre ordinateur.

## <a name="see-also"></a>Voir aussi

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
