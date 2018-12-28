---
title: __unaligned
ms.date: 12/17/2018
f1_keywords:
- __unaligned_cpp
- __unaligned
- _unaligned
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
ms.openlocfilehash: 8eb1b93aa55601125600b6c69d9bff3d9ca43aa3
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53626862"
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

- [Exemples d’alignement de structure](../build/x64-software-conventions.md#examples-of-structure-alignment)

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)