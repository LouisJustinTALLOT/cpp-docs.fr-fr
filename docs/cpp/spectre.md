---
description: 'En savoir plus sur : spectre'
title: spectre
ms.date: 01/23/2018
f1_keywords:
- spectre_cpp
- spectre
- nomitigation
helpviewer_keywords:
- __declspec keyword (C++), spectre
- spectre __declspec keyword
ms.openlocfilehash: fc1f56a59dea1eaa3596a6f7a7c0347ab822e302
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113816"
---
# <a name="spectre"></a>spectre

**Spécifique à Microsoft**

Indique au compilateur de ne pas insérer d’instructions de barrière d’exécution spéculative spectre variant 1 pour une fonction.

## <a name="syntax"></a>Syntaxe

> **__declspec (spectre (nomitigation))**

## <a name="remarks"></a>Notes

Avec l’option [/Qspectre](../build/reference/qspectre.md) du compilateur, le compilateur insère des instructions de barrière d’exécution spéculative. Ils sont insérés là où l’analyse indique qu’une faille de sécurité de la variante spectre 1 existe. Les instructions spécifiques émises dépendent du processeur. Bien que ces instructions aient un impact minimal sur la taille du code ou les performances, il peut arriver que votre code ne soit pas affecté par la vulnérabilité et nécessite des performances maximales.

L’analyse d’experts peut déterminer qu’une fonction est sécurisée à partir d’une erreur de contournement de validation de la variante spectre 1. Dans ce cas, vous pouvez supprimer la génération du code d’atténuation dans une fonction en appliquant `__declspec(spectre(nomitigation))` à la déclaration de fonction.

> [!CAUTION]
> Les instructions de barrière d’exécution spéculative **/Qspectre** fournissent une protection de sécurité importante et ont une incidence négligeable sur les performances. Par conséquent, nous vous recommandons de ne pas les supprimer, sauf dans la rare éventualité où les performances d'une fonction est un problème critique et où la fonction est réputée pour être sécurisée.

## <a name="example"></a>Exemple

Le code suivant illustre l’utilisation de `__declspec(spectre(nomitigation))`.

```cpp
// compile with: /c /Qspectre
static __declspec(spectre(nomitigation))
int noSpectreIssues() {
    // No Spectre variant 1 vulnerability here
    // ...
    return 0;
}

int main() {
    noSpectreIssues();
    return 0;
}
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[/Qspectre](../build/reference/qspectre.md)
