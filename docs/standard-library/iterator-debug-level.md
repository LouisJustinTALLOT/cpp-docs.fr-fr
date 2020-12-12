---
description: 'En savoir plus sur : _ITERATOR_DEBUG_LEVEL'
title: _ITERATOR_DEBUG_LEVEL
ms.date: 11/04/2016
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
ms.openlocfilehash: 769b7f3a8eecd3c994ee82b67385f080f0945f33
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306636"
---
# <a name="_iterator_debug_level"></a>_ITERATOR_DEBUG_LEVEL

La macro _ITERATOR_DEBUG_LEVEL contrôle si les [itérateurs vérifiés](../standard-library/checked-iterators.md) et la [prise en charge des itérateurs de débogage](../standard-library/debug-iterator-support.md) sont activés. Cette macro remplace et combine les fonctionnalités de l’ancien _SECURE_SCL et des macros _HAS_ITERATOR_DEBUGGING.

## <a name="macro-values"></a>Valeurs de macro

Le tableau suivant récapitule les valeurs possibles de la macro _ITERATOR_DEBUG_LEVEL.

|Mode de compilation|Valeur de macro|Description|
|----------------------|----------------|-----------------|
|**Déboguer**|||
||0|Désactive les itérateurs vérifiés et désactive le débogage d’itérateur.|
||1|Active les itérateurs vérifiés et désactive le débogage d’itérateur.|
||2 (Par défaut)|Active le débogage d’itérateur. Les itérateurs vérifiés ne sont pas pertinents.|
|**Version release**|||
||0 (Par défaut)|Désactive les itérateurs vérifiés.|
||1|Active les itérateurs vérifiés. Le débogage d’itérateur n’est pas pertinent.|

En mode release, le compilateur génère une erreur si vous spécifiez _ITERATOR_DEBUG_LEVEL en tant que 2.

## <a name="remarks"></a>Notes

La macro _ITERATOR_DEBUG_LEVEL contrôle si les [itérateurs vérifiés](../standard-library/checked-iterators.md) sont activés, et en mode débogage, si la [prise en charge de l’itérateur de débogage](../standard-library/debug-iterator-support.md) est activée. Si _ITERATOR_DEBUG_LEVEL est défini sur 1 ou 2, les itérateurs vérifiés garantissent que les limites de vos conteneurs ne sont pas remplacées. Si _ITERATOR_DEBUG_LEVEL a la valeur 0, les itérateurs ne sont pas vérifiés. Lorsque _ITERATOR_DEBUG_LEVEL est défini sur 1, toute utilisation d’un itérateur non sécurisé provoque une erreur d’exécution et le programme se termine. Lorsque _ITERATOR_DEBUG_LEVEL est défini sur 2, l’utilisation d’un itérateur non sécurisé provoque une demande d’assertion et une boîte de dialogue d’erreur d’exécution qui vous permet de vous arrêter dans le débogueur.

Étant donné que la macro _ITERATOR_DEBUG_LEVEL prend en charge des fonctionnalités similaires pour les macros _SECURE_SCL et _HAS_ITERATOR_DEBUGGING, vous pouvez être sûr de la valeur de macro et de macro à utiliser dans une situation particulière. Pour éviter toute confusion, nous vous recommandons d’utiliser uniquement la macro _ITERATOR_DEBUG_LEVEL. Ce tableau décrit l’équivalent de la valeur de macro _ITERATOR_DEBUG_LEVEL à utiliser pour différentes valeurs de _SECURE_SCL et _HAS_ITERATOR_DEBUGGING dans le code existant.

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (valeur par défaut en mode Version release)|0 (désactivé)|0 (désactivé)|
|1|1 (activé)|0 (désactivé)|
|2 (valeur par défaut en mode Débogage)|(non pertinent)|1 (activé en mode Débogage)|

Pour plus d’informations sur la façon de désactiver les avertissements concernant les itérateurs vérifiés, consultez [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

### <a name="example"></a>Exemple

Pour spécifier une valeur pour la macro _ITERATOR_DEBUG_LEVEL, utilisez l’option du compilateur [/d](../build/reference/d-preprocessor-definitions.md) pour la définir sur la ligne de commande, ou utilisez `#define` avant d’inclure les en-têtes de la bibliothèque standard C++ dans vos fichiers sources. Par exemple, sur la ligne de commande, pour compiler *Sample. cpp* en mode débogage et pour utiliser la prise en charge de l’itérateur de débogage, vous pouvez spécifier la _ITERATOR_DEBUG_LEVEL définition de macro :

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

Dans un fichier source, spécifiez la macro avant les en-têtes de bibliothèque standard qui définissent les itérateurs.

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>Voir aussi

[Itérateurs vérifiés](../standard-library/checked-iterators.md)\
[Prise en charge des itérateurs de débogage](../standard-library/debug-iterator-support.md)\
[Bibliothèques sécurisées : bibliothèque standard C++](../standard-library/safe-libraries-cpp-standard-library.md)
