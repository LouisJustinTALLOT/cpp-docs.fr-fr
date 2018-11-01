---
title: _ITERATOR_DEBUG_LEVEL
ms.date: 11/04/2016
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
ms.openlocfilehash: a584fe5a97e251205e750507b27e53e6e7b9a20e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502815"
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL

Les contrôles de macro _ITERATOR_DEBUG_LEVEL si [itérateurs vérifiés](../standard-library/checked-iterators.md) et [prise en charge de l’itérateur débogage](../standard-library/debug-iterator-support.md) sont activés. Cette macro remplace et combine les fonctionnalités des anciennes macros _SECURE_SCL et _SECURE_SCL.

## <a name="macro-values"></a>Valeurs de macro

Le tableau suivant récapitule les valeurs possibles pour la macro _ITERATOR_DEBUG_LEVEL.

|Mode de compilation|Valeur de macro|Description|
|----------------------|----------------|-----------------|
|**Débogage**|||
||0|Désactive les itérateurs vérifiés et désactive le débogage d’itérateur.|
||1|Active les itérateurs vérifiés et désactive le débogage d’itérateur.|
||2 (Par défaut)|Active le débogage d’itérateur. Les itérateurs vérifiés ne sont pas pertinents.|
|**Version release**|||
||0 (Par défaut)|Désactive les itérateurs vérifiés.|
||1|Active les itérateurs vérifiés. Le débogage d’itérateur n’est pas pertinent.|

En mode de mise en production, le compilateur génère une erreur si vous spécifiez _ITERATOR_DEBUG_LEVEL comme 2.

## <a name="remarks"></a>Notes

Les contrôles de macro _ITERATOR_DEBUG_LEVEL si [itérateurs vérifiés](../standard-library/checked-iterators.md) sont activés et en mode débogage si [prise en charge de l’itérateur débogage](../standard-library/debug-iterator-support.md) est activé. Si _ITERATOR_DEBUG_LEVEL est définie comme 1 ou 2, les itérateurs vérifiés garantissent que les limites de vos conteneurs ne sont pas remplacées. Si _ITERATOR_DEBUG_LEVEL est 0, les itérateurs ne sont pas vérifiées. Lorsque _ITERATOR_DEBUG_LEVEL est définie sur 1, toute utilisation de l’itérateur unsafe provoque une erreur d’exécution et le programme se termine. Lorsque _ITERATOR_DEBUG_LEVEL est définie sur 2, itérateur unsafe utiliser provoque une assertion et une boîte de dialogue erreur runtime vous permet d’arrêteront le débogueur.

Étant donné que la macro _ITERATOR_DEBUG_LEVEL prend en charge des fonctionnalités similaires aux macros _SECURE_SCL et _SECURE_SCL, vous pouvez avoir des doutes quelle macro et une macro la valeur à utiliser dans une situation particulière. Pour éviter toute confusion, nous vous recommandons d’utiliser uniquement la macro _ITERATOR_DEBUG_LEVEL. Ce tableau décrit la valeur de macro _ITERATOR_DEBUG_LEVEL équivalent à utiliser pour différentes valeurs de _SECURE_SCL et _SECURE_SCL dans le code existant.

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (valeur par défaut en mode Version release)|0 (désactivé)|0 (désactivé)|
|1|1 (activé)|0 (désactivé)|
|2 (valeur par défaut en mode Débogage)|(non pertinent)|1 (activé en mode Débogage)|

Pour plus d’informations sur la façon de désactiver les avertissements concernant les itérateurs vérifiés, consultez [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

### <a name="example"></a>Exemple

Pour spécifier une valeur pour la macro _ITERATOR_DEBUG_LEVEL, utilisez un [/D](../build/reference/d-preprocessor-definitions.md) option du compilateur à définir sur la ligne de commande ou utilisez `#define` avant de la bibliothèque C++ Standard sont inclus dans vos fichiers sources. Par exemple, sur la ligne de commande pour compiler *sample.cpp* en mode débogage et d’utiliser des itérateurs de débogage prise en charge, vous pouvez spécifier la définition de macro _ITERATOR_DEBUG_LEVEL :

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

Dans un fichier source, spécifiez la macro avant les en-têtes de bibliothèque standard qui définissent les itérateurs.

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>Voir aussi

[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[Bibliothèques sécurisées : bibliothèque standard C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
