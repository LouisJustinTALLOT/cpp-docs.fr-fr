---
title: strict_gs_check
ms.date: 11/04/2016
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
ms.openlocfilehash: b62e1be466e65c0de6fb4eaa33ac6e99915529e6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037802"
---
# <a name="strictgscheck"></a>strict_gs_check

Ce pragma fournit une vérification de la sécurité renforcée.

## <a name="syntax"></a>Syntaxe

```
#pragma strict_gs_check([push,] on )
#pragma strict_gs_check([push,] off )
#pragma strict_gs_check(pop)
```

## <a name="remarks"></a>Notes

Indique au compilateur qu'il faut insérer un cookie aléatoire dans la pile de fonction pour faciliter la détection de certaines catégories de dépassement de mémoire tampon basé sur la pile. Par défaut, le `/GS` (vérification de la sécurité de la mémoire tampon) une option de compilateur n’insère pas un cookie pour toutes les fonctions. Pour plus d’informations, consultez l’article [/GS (vérification de la sécurité des mémoires tampons)](../build/reference/gs-buffer-security-check.md).

Vous devez compiler avec `/GS` (Buffer Security Check) pour activer **strict_gs_check**.

Utilisez ce pragma dans les modules de code qui sont exposés à des données potentiellement nuisibles. Ce pragma est très agressif. Il est appliqué à des fonctions qui peuvent ne pas avoir besoin de cette défense, mais il est optimisé pour minimiser son effet sur les performances de l'application résultante.

Même si vous utilisez ce pragma, vous devez vous efforcer d'écrire du code sécurisé. Autrement dit, assurez-vous que votre code n’a aucuns dépassements de mémoire tampon. **strict_gs_check** peut protéger votre application contre les dépassements de mémoire tampon qui restent dans votre code.

## <a name="example"></a>Exemple

Dans le code suivant, un dépassement de mémoire tampon se produit lorsque nous copions un tableau dans un tableau local. Lorsque vous compilez ce code avec `/GS`, aucun cookie n’est insérée dans la pile, car le type de données de tableau est un pointeur. Ajout de la **strict_gs_check** pragma force le cookie de pile dans la pile de fonction.

```cpp
// pragma_strict_gs_check.cpp
// compile with: /c

#pragma strict_gs_check(on)

void ** ReverseArray(void **pData,
                     size_t cData)
{
    // *** This buffer is subject to being overrun!! ***
    void *pReversed[20];

    // Reverse the array into a temporary buffer
    for (size_t j = 0, i = cData; i ; --i, ++j)
        // *** Possible buffer overrun!! ***
            pReversed[j] = pData[i];

    // Copy temporary buffer back into input/output buffer
    for (size_t i = 0; i < cData ; ++i)
        pData[i] = pReversed[i];

    return pData;
}
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[/GS (vérification de la sécurité des mémoires tampons)](../build/reference/gs-buffer-security-check.md)