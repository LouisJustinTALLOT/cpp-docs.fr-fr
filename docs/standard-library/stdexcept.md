---
title: '&lt;stdexcept&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <stdexcept>
dev_langs:
- C++
helpviewer_keywords:
- stdexcept header
ms.assetid: 495c10b1-1e60-4514-9f8f-7fda11a2f522
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c28e4bbccb3c28c314226b8f215407292d5e200
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863619"
---
# <a name="ltstdexceptgt"></a>&lt;stdexcept&gt;

Définit plusieurs classes standard utilisées pour les rapports d'exceptions. Les classes forment une hiérarchie de dérivation dérivée de la classe [exception](../standard-library/exception-class.md) et incluent deux types généraux d’exceptions : les erreurs logiques et les erreurs d’exécution. Les erreurs logiques sont dues à des erreurs de programmeur. Elles dérivent de la classe de base logic_error et incluent :

- `domain_error`

- `invalid_argument`

- `length_error`

- `out_of_range`

Les erreurs d'exécution sont dues à des erreurs dans les fonctions de bibliothèque ou dans le système d'exécution. elles dérivent de la classe de base runtime_error et incluent :

- `overflow_error`

- `range_error`

- `underflow_error`

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[domain_error, classe](../standard-library/domain-error-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler une erreur de domaine.|
|[invalid_argument, classe](../standard-library/invalid-argument-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler un argument non valide.|
|[length_error, classe](../standard-library/length-error-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler une tentative de génération d'un objet trop long pour être spécifié.|
|[logic_error, classe](../standard-library/logic-error-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler des erreurs normalement détectables avant l'exécution du programme, telles que les violations de conditions préalables logiques.|
|[out_of_range, classe](../standard-library/out-of-range-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler un argument qui est en dehors de sa plage valide.|
|[overflow_error, classe](../standard-library/overflow-error-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler un dépassement de capacité arithmétique positif.|
|[range_error, classe](../standard-library/range-error-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler une erreur de plage.|
|[runtime_error, classe](../standard-library/runtime-error-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler des erreurs normalement détectables uniquement durant l'exécution du programme.|
|[underflow_error, classe](../standard-library/underflow-error-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler un dépassement de capacité arithmétique négatif.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
