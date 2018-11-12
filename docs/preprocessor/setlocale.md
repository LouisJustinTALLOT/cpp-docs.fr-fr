---
title: setlocale
ms.date: 11/04/2016
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
ms.openlocfilehash: e5a190e18dd38c5d2b6e03703c5ee08043cd6e41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487956"
---
# <a name="setlocale"></a>setlocale

Définit les paramètres régionaux (pays/région et langue) à utiliser lors de la conversion des constantes à caractères larges et des littéraux de chaîne.

## <a name="syntax"></a>Syntaxe

```
#pragma setlocale( "[locale-string]" )
```

## <a name="remarks"></a>Notes

Étant donné que l'algorithme de conversion des caractères multioctets en caractères larges peut varier selon les paramètres régionaux ou que la compilation peut avoir lieu sous des paramètres régionaux différents de ceux sous lesquels un fichier exécutable sera exécuté, ce pragma permet de spécifier les paramètres régionaux cibles au moment de la compilation. Cela garantit que les chaînes à caractères larges seront stockées au format correct.

La valeur par défaut *chaîne de paramètres régionaux* est « ».

Les paramètres régionaux « C » mappent chaque caractère dans la chaîne en sa valeur comme un **wchar_t** (court non signé). Autres valeurs qui sont valides pour `setlocale` sont les entrées qui sont trouvent dans le [chaînes de langue](../c-runtime-library/language-strings.md) liste. Par exemple, vous pouvez émettre la commande suivante :

```cpp
#pragma setlocale("dutch")
```

La capacité à publier une chaîne de langue dépend de la prise en charge des pages de codes et des ID de langue sur votre ordinateur.

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)