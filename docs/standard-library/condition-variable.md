---
title: '&lt;condition_variable&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <condition_variable>
dev_langs:
- C++
ms.assetid: 8567f7cc-20bd-42a7-9137-87c46f878009
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a54045dfdebf3ab7c9f7ad04611bc9e267faea0d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845724"
---
# <a name="ltconditionvariablegt"></a>&lt;condition_variable&gt;

Définit les classes [condition_variable](../standard-library/condition-variable-class.md) et [condition_variable_any](../standard-library/condition-variable-any-class.md) servant à créer des objets qui attendent qu’une condition soit true.

Cet en-tête utilise le runtime d’accès concurrentiel (ConcRT) pour pouvoir l’utiliser avec d’autres mécanismes ConcRT. Pour plus d’informations sur ConcRT, consultez [Runtime d’accès concurrentiel](../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Syntaxe

```cpp
#include <condition_variable>
```

> [!NOTE]
> Dans le code est compilé à l’aide de **/CLR**, cet en-tête est bloqué.

### <a name="remarks"></a>Notes

Le code qui attend une variable conditionnelle doit également utiliser un `mutex`. Un thread appelant doit verrouiller le `mutex` avant d’appeler les fonctions qui attendent la variable conditionnelle. Le `mutex` est verrouillé quand la fonction appelée retourne une valeur. Le `mutex` n’est pas verrouillé pendant que le thread attend que la condition devienne true. Pour éviter les résultats imprévisibles, chaque thread qui attend une variable conditionnelle doit utiliser le même objet `mutex`.

Les objets de type `condition_variable_any` peuvent être utilisés avec un mutex de tout type. Le type du mutex utilisé n’a pas besoin de fournir la méthode `try_lock`. Les objets de type `condition_variable` peuvent uniquement être utilisés avec un mutex de type `unique_lock<mutex>`. Les objets de ce type peuvent être plus rapides que les objets de type `condition_variable_any<unique_lock<mutex>>`.

Pour attendre un événement, verrouillez d’abord le mutex, puis appelez l’une des méthodes `wait` sur la variable conditionnelle. L’appel de `wait` se bloque jusqu’à ce qu’un autre thread signale la variable conditionnelle.

Les *éveils sans motif* se produisent quand les threads qui attendent des variables conditionnelles sont débloqués sans les notifications appropriées. Pour reconnaître ces éveils sans motif, le code qui attend qu’une condition devienne true doit vérifier explicitement cette condition quand il est retourné par une fonction d’attente. Cela s’effectue habituellement en utilisant une boucle ; vous pouvez utiliser `wait(unique_lock<mutex>& lock, Predicate pred)` pour effectuer cette boucle à votre place.

```cpp
while (condition is false)
    wait for condition variable;
```

Les classes `condition_variable_any` et `condition_variable` ont chacune trois méthodes qui attendent une condition.

- `wait` attend pendant une période de temps illimitée.

- `wait_until` attend jusqu’à une valeur `time` spécifiée.

- `wait_for` attend pendant une valeur `time interval` spécifiée.

Chacune de ces méthodes a deux versions surchargées. L’une se contente d’attendre et peut s’éveiller sans motif. L’autre accepte un argument de modèle supplémentaire qui définit un prédicat. La méthode ne retourne pas de valeur tant que le prédicat est `true`.

Chaque classe a également deux méthodes qui sont utilisées pour informer une variable conditionnelle que sa condition est `true`.

- `notify_one` éveille un des threads en attente de la variable conditionnelle.

- `notify_all` éveille tous les threads en attente de la variable conditionnelle.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[condition_variable, classe](../standard-library/condition-variable-class.md)<br/>
[condition_variable_any, classe](../standard-library/condition-variable-any-class.md)<br/>
