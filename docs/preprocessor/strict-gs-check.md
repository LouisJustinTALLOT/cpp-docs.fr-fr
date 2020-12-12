---
description: 'En savoir plus sur : pragma strict_gs_check'
title: strict_gs_check, pragma
ms.date: 08/29/2019
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
ms.openlocfilehash: 3fa1600bba59077ff66bfb0184bdd3ca4fe0e326
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197307"
---
# <a name="strict_gs_check-pragma"></a>strict_gs_check, pragma

Ce pragma fournit une vérification de la sécurité renforcée.

## <a name="syntax"></a>Syntaxe

> **#pragma strict_gs_check (** [ **push,** ] { **on**  |  **off** } **)**\
> **strict_gs_check #pragma (POP)**

## <a name="remarks"></a>Notes

Indique au compilateur qu'il faut insérer un cookie aléatoire dans la pile de fonction pour faciliter la détection de certaines catégories de dépassement de mémoire tampon basé sur la pile. Par défaut, l' `/GS` option du compilateur (vérification de la sécurité des tampons) n’insère pas de cookie pour toutes les fonctions. Pour plus d’informations, consultez [/GS (vérification de la sécurité des tampons)](../build/reference/gs-buffer-security-check.md).

Compilez à l’aide `/GS` de pour activer **strict_gs_check**.

Utilisez ce pragma dans les modules de code qui sont exposés à des données potentiellement nuisibles. **strict_gs_check** est un pragma agressif et est appliqué aux fonctions qui n’ont peut-être pas besoin de cette défense, mais qui est optimisée pour réduire son effet sur les performances de l’application résultante.

Même si vous utilisez ce pragma, vous devez vous efforcer d'écrire du code sécurisé. Autrement dit, assurez-vous que votre code n’a pas de dépassements de mémoire tampon. **strict_gs_check** pouvez protéger votre application contre les dépassements de mémoire tampon qui restent dans votre code.

## <a name="example"></a>Exemple

Dans cet exemple, un dépassement de mémoire tampon se produit lorsque nous copions un tableau dans un tableau local. Quand vous compilez ce code avec `/GS` , aucun cookie n’est inséré dans la pile, car le type de données du tableau est un pointeur. L’ajout du **strict_gs_check** pragma force le cookie de la pile dans la pile des fonctions.

```cpp
// pragma_strict_gs_check.cpp
// compile with: /c

#pragma strict_gs_check(on)

void ** ReverseArray(void **pData,
                     size_t cData)
{
    // **_ This buffer is subject to being overrun!! _*_
    void _pReversed[20];

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

[Directives pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[/GS (Vérification de la sécurité des mémoires tampons)](../build/reference/gs-buffer-security-check.md)
