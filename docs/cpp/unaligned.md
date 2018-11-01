---
title: __unaligned
ms.date: 10/10/2018
f1_keywords:
- __unaligned_cpp
- __unaligned
- _unaligned
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
ms.openlocfilehash: 8abe64a8eb82188ab86c91a023254b3a4106797c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487007"
---
# <a name="unaligned"></a>__unaligned

**Spécifique à Microsoft**. Lorsque vous déclarez un pointeur avec la **__unaligned** modificateur, le compilateur suppose que le pointeur adresse des données qui ne sont pas alignées. Par conséquent, approprié à la plateforme de code est généré pour gérer des lectures non alignés et écrit par le pointeur.

## <a name="remarks"></a>Notes

Ce modificateur décrit l’alignement des données adressées par le pointeur ; le pointeur lui-même est considéré comme aligné.

La nécessité pour le **__unaligned** mot clé varie selon la plateforme et l’environnement. Échec pour marquer les données correctement peut entraîner des problèmes, allant de la dégradation des performances pour les défaillances matérielles. Le **__unaligned** modificateur n’est pas valide pour le x86 plateforme.

Pour assurer la compatibilité avec les versions précédentes, **_unaligned** est un synonyme de **__unaligned** , sauf si option du compilateur [/Za \(désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifié.

Pour plus d'informations sur l'alignement, consultez :

- [align](../cpp/align-cpp.md)

- [__alignof, opérateur](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (Alignement des membres de la structure)](../build/reference/zp-struct-member-alignment.md)

- [Exemples d’alignement de structure](../build/examples-of-structure-alignment.md)

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)