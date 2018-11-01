---
title: spectre
ms.date: 1/23/2018
f1_keywords:
- spectre_cpp
- spectre
- nomitigation
helpviewer_keywords:
- __declspec keyword (C++), spectre
- spectre __declspec keyword
ms.openlocfilehash: 2377a3c23be1e27bfe4f2df23eb00823635fa05d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592008"
---
# <a name="spectre"></a>spectre

**Section spécifique à Microsoft**

Indique au compilateur de ne pas insérer des instructions de cloisonnement Spectre variante 1 exécution spéculative pour une fonction.

## <a name="syntax"></a>Syntaxe

> **__declspec (spectre(nomitigation))**

## <a name="remarks"></a>Notes

Le [/qspectre](../build/reference/qspectre.md) option du compilateur, le compilateur insérer des instructions de cloisonnement de l’exécution spéculative où analyse indique un problème de sécurité Spectre variante 1. Les instructions spécifiques émises varient selon le processeur. Bien que ces instructions doivent avoir un impact minime sur la taille du code ou des performances, il peut arriver dans lequel votre code n’est pas affectée par la vulnérabilité et nécessite des performances maximales.

Analyses d’experts peuvent déterminer qu’une fonction est protégée à partir d’un défaut de contournement de vérification de Spectre variante 1 limites. Dans ce cas, vous pouvez supprimer la génération de code d’atténuation dans une fonction en appliquant `__declspec(spectre(nomitigation))` à la déclaration de fonction.

> [!CAUTION]
> Le **/qspectre** obtenir des instructions de l’exécution spéculative barrière assure la protection de sécurité importants et ont un impact négligeable sur les performances. Par conséquent, nous vous recommandons de ne pas les supprimer, sauf dans la rare éventualité où les performances d'une fonction est un problème critique et où la fonction est réputée pour être sécurisée.

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

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[/Qspectre](../build/reference/qspectre.md)
