---
title: _ITERATOR_DEBUG_LEVEL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
dev_langs:
- C++
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7219ed039e77d0857151c54e73a03a0d1f6a3f5e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864136"
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL

La macro `_ITERATOR_DEBUG_LEVEL` contrôle si les [itérateurs vérifiés](../standard-library/checked-iterators.md) et la [prise en charge d’itérateur de débogage](../standard-library/debug-iterator-support.md) sont activés. Cette macro remplace et combine les fonctionnalités des anciennes macros `_SECURE_SCL` et `_HAS_ITERATOR_DEBUGGING`.

## <a name="macro-values"></a>Valeurs de macro

Le tableau suivant récapitule les valeurs possibles de la macro `_ITERATOR_DEBUG_LEVEL`.

|Mode de compilation|Valeur de macro|Description|
|----------------------|----------------|-----------------|
|**Débogage**|||
||0|Désactive les itérateurs vérifiés et désactive le débogage d’itérateur.|
||1|Active les itérateurs vérifiés et désactive le débogage d’itérateur.|
||2 (Par défaut)|Active le débogage d’itérateur. Les itérateurs vérifiés ne sont pas pertinents.|
|**Version release**|||
||0 (Par défaut)|Désactive les itérateurs vérifiés.|
||1|Active les itérateurs vérifiés. Le débogage d’itérateur n’est pas pertinent.|

En mode Version release, le compilateur génère une erreur si vous affectez la valeur 2 à `_ITERATOR_DEBUG_LEVEL`.

## <a name="remarks"></a>Notes

La macro `_ITERATOR_DEBUG_LEVEL` contrôle si les [itérateurs vérifiés](../standard-library/checked-iterators.md) sont activés et, en mode Débogage, si la [prise en charge d’itérateur de débogage](../standard-library/debug-iterator-support.md) est activée. Si `_ITERATOR_DEBUG_LEVEL` a la valeur 1 ou 2, les itérateurs vérifiés garantissent que les limites de vos conteneurs ne sont pas remplacées. Si `_ITERATOR_DEBUG_LEVEL` a la valeur 0, les itérateurs ne sont pas vérifiés. Si `_ITERATOR_DEBUG_LEVEL` a la valeur 1, toute utilisation non sécurisée d’un itérateur provoque une erreur d’exécution et le programme se termine. Quand `_ITERATOR_DEBUG_LEVEL` a la valeur 2, toute utilisation non sécurisée d’un itérateur provoque une assertion et l’affichage d’une boîte de dialogue d’erreur d’exécution qui vous permet de travailler dans le débogueur.

Étant donné que la macro `_ITERATOR_DEBUG_LEVEL` prend en charge des fonctionnalités similaires aux macros `_SECURE_SCL` et `_HAS_ITERATOR_DEBUGGING`, vous pouvez avoir des doutes quant à la macro et à la valeur de macro à utiliser dans une situation particulière. Pour éviter toute confusion, nous vous recommandons d’utiliser uniquement la macro `_ITERATOR_DEBUG_LEVEL`. Le tableau suivant décrit la valeur de macro `_ITERATOR_DEBUG_LEVEL` équivalente à utiliser pour différentes valeurs de `_SECURE_SCL` et `_HAS_ITERATOR_DEBUGGING` dans le code existant.

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (valeur par défaut en mode Version release)|0 (désactivé)|0 (désactivé)|
|1|1 (activé)|0 (désactivé)|
|2 (valeur par défaut en mode Débogage)|(non pertinent)|1 (activé en mode Débogage)|

Pour plus d’informations sur la façon de désactiver les avertissements concernant les itérateurs vérifiés, consultez [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).

### <a name="example"></a>Exemple

Pour spécifier une valeur pour la macro `_ITERATOR_DEBUG_LEVEL`, utilisez une option du compilateur [/D](../build/reference/d-preprocessor-definitions.md) pour la définir sur la ligne de commande, ou utilisez `#define` avant que les en-têtes de la bibliothèque standard C++ soient inclus dans vos fichiers sources. Par exemple, sur la ligne de commande, pour compiler *sample.cpp* en mode Débogage et pour utiliser la prise en charge d’itérateur de débogage, vous pouvez spécifier la définition de macro `_ITERATOR_DEBUG_LEVEL` :

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
