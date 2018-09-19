---
title: __unaligned | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __unaligned_cpp
dev_langs:
- C++
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9593a0b3c6e6980f5be2ce9dcf13e505e94dcace
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040194"
---
# <a name="unaligned"></a>__unaligned

**Spécifique à Microsoft**. Lorsque vous déclarez un pointeur avec la **__unaligned** modificateur, le compilateur suppose que le pointeur adresse des données qui ne sont pas alignées. Par conséquent, approprié à la plateforme de code est généré pour gérer des lectures non alignés et écrit par le pointeur.

## <a name="remarks"></a>Notes

Ce modificateur décrit l’alignement des données adressées par le pointeur ; le pointeur lui-même est considéré comme aligné.

La nécessité pour le **__unaligned** mot clé varie selon la plateforme et l’environnement. Échec pour marquer les données correctement peut entraîner des problèmes, allant de la dégradation des performances pour les défaillances matérielles. Le **__unaligned** modificateur n’est pas valide pour le x86 plateforme.

Pour plus d'informations sur l'alignement, consultez :

- [align](../cpp/align-cpp.md)

- [__alignof, opérateur](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (Alignement des membres de la structure)](../build/reference/zp-struct-member-alignment.md)

- [Exemples d’alignement de structure](../build/examples-of-structure-alignment.md)

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)