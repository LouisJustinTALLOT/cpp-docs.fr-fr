---
description: 'En savoir plus sur : bibliothèques sécurisées : bibliothèque standard C++'
title: 'Bibliothèques sécurisées : bibliothèque C++ standard'
ms.date: 11/04/2016
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
ms.assetid: 3993340f-1f29-4d81-b3f5-52a52bc8e148
ms.openlocfilehash: 7027031054bf9ef7c2a157d6162539bc3801dec4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148887"
---
# <a name="safe-libraries-c-standard-library"></a>Bibliothèques sécurisées : bibliothèque C++ standard

Plusieurs améliorations ont été apportées aux bibliothèques fournies avec Microsoft C++, y compris la bibliothèque C++ standard, pour les rendre plus sécurisées.

Plusieurs méthodes de la bibliothèque standard C++ ont été identifiés comme potentiellement dangereuses, car elles peuvent entraîner un dépassement de mémoire tampon ou d’autre défauts dans le code. L’utilisation de ces méthodes est déconseillée : de nouvelles méthodes plus sécurisées des méthodes ont été créées pour les remplacer. Ces nouvelles méthodes se trouvent toutes dans `_s`.

Plusieurs améliorations ont également été apportées pour renforcer la sécurité des itérateurs et des algorithmes. Pour plus d’informations, consultez [Checked Iterators](../standard-library/checked-iterators.md), [Debug Iterator Support](../standard-library/debug-iterator-support.md) et [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="remarks"></a>Notes

Le tableau suivant répertorie les méthodes de la bibliothèque C++ standard qui sont potentiellement dangereuses, ainsi que leur équivalent plus sécurisé :

|Méthode potentiellement dangereuse|Équivalent plus sécurisé|
|-------------------------------|----------------------|
|[copy](../standard-library/basic-string-class.md#copy)|[basic_string :: _Copy_s](../standard-library/basic-string-class.md#copy_s)|
|[copy](../standard-library/char-traits-struct.md#copy)|[char_traits :: _Copy_s](../standard-library/char-traits-struct.md#copy_s)|

Si vous appelez une des méthodes potentiellement dangereuses ci-dessus, ou si vous utilisez incorrectement des itérateurs, le compilateur génère l’[avertissement du compilateur (niveau 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Pour plus d’informations sur la désactivation de ces avertissements, consultez [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

## <a name="in-this-section"></a>Dans cette section

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)

[_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)

[Itérateurs vérifiés](../standard-library/checked-iterators.md)

[Prise en charge des itérateurs de débogage](../standard-library/debug-iterator-support.md)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)
