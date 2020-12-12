---
description: 'En savoir plus sur : &lt; stdexcept&gt;'
title: '&lt;stdexcept&gt;'
ms.date: 11/04/2016
f1_keywords:
- <stdexcept>
helpviewer_keywords:
- stdexcept header
ms.assetid: 495c10b1-1e60-4514-9f8f-7fda11a2f522
ms.openlocfilehash: 07ab90442630c6dfb5a96604ba7c0cb6b214f605
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169084"
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
|[Classe domain_error](../standard-library/domain-error-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler une erreur de domaine.|
|[Classe invalid_argument](../standard-library/invalid-argument-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler un argument non valide.|
|[Classe length_error](../standard-library/length-error-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler une tentative de génération d'un objet trop long pour être spécifié.|
|[Classe logic_error](../standard-library/logic-error-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler des erreurs normalement détectables avant l'exécution du programme, telles que les violations de conditions préalables logiques.|
|[Classe out_of_range](../standard-library/out-of-range-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler un argument qui est en dehors de sa plage valide.|
|[Classe overflow_error](../standard-library/overflow-error-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler un dépassement de capacité arithmétique positif.|
|[Classe range_error](../standard-library/range-error-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler une erreur de plage.|
|[Classe runtime_error](../standard-library/runtime-error-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler des erreurs normalement détectables uniquement durant l'exécution du programme.|
|[Classe underflow_error](../standard-library/underflow-error-class.md)|Classe qui sert de classe de base pour toutes les exceptions levées pour signaler un dépassement de capacité arithmétique négatif.|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
