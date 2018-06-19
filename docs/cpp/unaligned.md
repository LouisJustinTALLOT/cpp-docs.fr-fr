---
title: __unaligned | Documents Microsoft
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
ms.openlocfilehash: d73b082b9f41d03eb0b1a8c9fe772351ff4da91f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420906"
---
# <a name="unaligned"></a>__unaligned

**Spécifique à Microsoft**. Lorsque vous déclarez un pointeur avec le modificateur `__unaligned`, le compilateur suppose que le pointeur adresse des données non alignées. Par conséquent, approprié à la plateforme de code est généré pour gérer des lectures non alignés et écrit par l’intermédiaire du pointeur.

## <a name="remarks"></a>Notes

Ce modificateur décrit l’alignement des données traitées par le pointeur ; le pointeur lui-même est considéré comme aligné.

La nécessité pour le `__unaligned` mot clé varie selon la plate-forme et l’environnement. Échec pour marquer des données de façon appropriée peut entraîner des problèmes, allant de trop handicaper les performances pour les défaillances matérielles. Le `__unaligned` modificateur n’est pas valide pour le x86 plateforme.

Pour plus d'informations sur l'alignement, consultez :

- [align](../cpp/align-cpp.md)

- [__alignof, opérateur](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (Alignement des membres de la structure)](../build/reference/zp-struct-member-alignment.md)

- [Exemples d’alignement de structure](../build/examples-of-structure-alignment.md)

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)
