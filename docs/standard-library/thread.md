---
title: '&lt;thread&gt;'
ms.date: 11/04/2016
f1_keywords:
- <thread>
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
ms.openlocfilehash: 43fb79ceda6de7409e6f93797ce2f4ff213c43ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487514"
---
# <a name="ltthreadgt"></a>&lt;thread&gt;

Incluez l’en-tête standard \<thread > pour définir la classe **thread** et diverses fonctions de prise en charge.

## <a name="syntax"></a>Syntaxe

```cpp
#include <thread>
```

## <a name="remarks"></a>Notes

> [!NOTE]
> Dans le code est compilé à l’aide de **/CLR**, cet en-tête est bloqué.

Le `__STDCPP_THREADS__` macro est définie comme une valeur différente de zéro pour indiquer que les threads sont pris en charge par cet en-tête.

## <a name="members"></a>Membres

### <a name="public-classes"></a>Classes publiques

|Nom|Description|
|----------|-----------------|
|[thread, classe](../standard-library/thread-class.md)|Définit un objet qui sert à observer et gérer un thread d’exécution dans une application.|

### <a name="public-structures"></a>Structures publiques

|Name|Description|
|----------|-----------------|
|[hash, structure (bibliothèque standard C++)](../standard-library/hash-structure-stl.md)|Définit une fonction membre qui retourne une valeur qui est déterminée de manière unique par un `thread::id`. La fonction membre définit un [hachage](../standard-library/hash-class.md) fonction qui est appropriée pour les valeurs de mappage de type `thread::id` pour une distribution de valeurs d’index.|

### <a name="public-functions"></a>Fonctions publiques

|Name|Description|
|----------|-----------------|
|[get_id](../standard-library/thread-functions.md#get_id)|Identifie de façon unique le thread d’exécution en cours.|
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|Bloque le thread appelant.|
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|Bloque le thread appelant au moins jusqu’à l’heure spécifiée.|
|[swap](../standard-library/thread-functions.md#swap)|Échange les États de deux **thread** objets.|
|[yield](../standard-library/thread-functions.md#yield)|Indique au système d’exploitation d’exécuter d’autres threads, même si le thread actuel continuerait normalement à s’exécuter.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[opérateur > =, opérateur](../standard-library/thread-operators.md#op_gt_eq)|Détermine si un objet `thread::id` est supérieur ou égal à un autre.|
|[opérateur > opérateur](../standard-library/thread-operators.md#op_gt)|Détermine si un objet `thread::id` est supérieur à un autre.|
|[opérateur < =, opérateur](../standard-library/thread-operators.md#op_lt_eq)|Détermine si un objet `thread::id` est inférieur ou égal à un autre.|
|[opérateur < opérateur](../standard-library/thread-operators.md#op_lt)|Détermine si un objet `thread::id` est inférieur à un autre.|
|[opérateur ! =, opérateur](../standard-library/thread-operators.md#op_neq)|Compare deux objets `thread::id` pour déterminer s'ils sont différents.|
|[opérateur ==, opérateur](../standard-library/thread-operators.md#op_eq_eq)|Compare deux objets `thread::id` pour déterminer s’ils sont égaux.|
|[opérateur << opérateur](../standard-library/thread-operators.md#op_lt_lt)|Insère une représentation textuelle d’un objet `thread::id` dans un flux.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
