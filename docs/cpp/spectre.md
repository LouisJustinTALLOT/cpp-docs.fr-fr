---
title: spectre | Documents Microsoft
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- spectre_cpp
- spectre
- nomitigation
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword (C++), spectre
- spectre __declspec keyword
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 153ff690b975ecb442c260fcebce73acd32d03fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32422408"
---
# <a name="spectre"></a>spectre

**Section spécifique à Microsoft**

Indique au compilateur de ne pas insérer des instructions barrière exécution spéculative du Spectre variante 1 pour une fonction.

## <a name="syntax"></a>Syntaxe

> **__declspec (spectre(nomitigation))**  

## <a name="remarks"></a>Notes

Le [/Qspectre](../build/reference/qspectre.md) option du compilateur, le compilateur insérer des instructions de cloisonnement d’exécution spéculatif où analyse indique un problème de sécurité de variante 1 Spectre. Les instructions spécifiques émises varient selon le processeur. Alors que ces instructions doivent avoir un impact minime sur la taille du code ou des performances, il peut arriver dans lequel votre code n’est pas affectée par la vulnérabilité et nécessite des performances maximales.

Analyse experte peut déterminer qu’une fonction est protégée contre une défaillance de contournement Spectre variante 1 limites à cocher. Dans ce cas, vous pouvez supprimer la génération de code dans une fonction d’atténuation en appliquant `__declspec(spectre(nomitigation))` à la déclaration de fonction.

> [!CAUTION]
> Le **/Qspectre** spéculatif exécuter les instructions de cloisonnement assurer une protection importante et ont un impact négligeable sur les performances. Par conséquent, nous vous recommandons de ne pas les supprimer, sauf dans la rare éventualité où les performances d'une fonction est un problème critique et où la fonction est réputée pour être sécurisée.

## <a name="example"></a>Exemple

Le code suivant montre comment utiliser `__declspec(spectre(nomitigation))`.

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

[__declspec](../cpp/declspec.md)  
[Mots clés](../cpp/keywords-cpp.md)  
[/Qspectre](../build/reference/qspectre.md)  
