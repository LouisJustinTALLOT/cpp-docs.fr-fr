---
title: '&lt;thread&gt;'
ms.date: 11/04/2016
f1_keywords:
- <thread>
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
ms.openlocfilehash: 7053402dfb566f10c7be4c0eebaef40f3d371f43
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460074"
---
# <a name="ltthreadgt"></a>&lt;thread&gt;

Incluez le thread \<d’en-tête standard > pour définir le **thread** de classe et diverses fonctions de prise en charge.

## <a name="syntax"></a>Syntaxe

```cpp
#include <thread>
```

## <a name="remarks"></a>Notes

> [!NOTE]
> Dans le code compilé à l’aide de **/CLR**, cet en-tête est bloqué.

La `__STDCPP_THREADS__` macro est définie comme une valeur différente de zéro pour indiquer que les threads sont pris en charge par cet en-tête.

## <a name="members"></a>Membres

### <a name="public-classes"></a>Classes publiques

|Nom|Description|
|----------|-----------------|
|[thread, classe](../standard-library/thread-class.md)|Définit un objet qui est utilisé pour observer et gérer un thread d’exécution dans une application.|

### <a name="public-structures"></a>Structures publiques

|Nom|Description|
|----------|-----------------|
|[hash, structure (bibliothèque standard C++)](../standard-library/hash-structure-stl.md)|Définit une fonction membre qui retourne une valeur qui est déterminée de manière unique par `thread::id`un. La fonction membre définit une fonction de [hachage](../standard-library/hash-class.md) appropriée pour mapper des valeurs de type `thread::id` à une distribution de valeurs d’index.|

### <a name="public-functions"></a>Fonctions publiques

|Nom|Description|
|----------|-----------------|
|[get_id](../standard-library/thread-functions.md#get_id)|Identifie de façon unique le thread d’exécution en cours.|
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|Bloque le thread appelant.|
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|Bloque le thread appelant au moins jusqu’à l’heure spécifiée.|
|[swap](../standard-library/thread-functions.md#swap)|Échange les États de deux objets **thread** .|
|[yield](../standard-library/thread-functions.md#yield)|Indique au système d’exploitation d’exécuter d’autres threads, même si le thread actuel continuerait normalement à s’exécuter.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[operator > =, opérateur](../standard-library/thread-operators.md#op_gt_eq)|Détermine si un objet `thread::id` est supérieur ou égal à un autre.|
|[operator >, opérateur](../standard-library/thread-operators.md#op_gt)|Détermine si un objet `thread::id` est supérieur à un autre.|
|[Operator < =, opérateur](../standard-library/thread-operators.md#op_lt_eq)|Détermine si un objet `thread::id` est inférieur ou égal à un autre.|
|[Operator <, opérateur](../standard-library/thread-operators.md#op_lt)|Détermine si un objet `thread::id` est inférieur à un autre.|
|[Operator! =, opérateur](../standard-library/thread-operators.md#op_neq)|Compare deux objets `thread::id` pour déterminer s'ils sont différents.|
|[Operator = =, opérateur](../standard-library/thread-operators.md#op_eq_eq)|Compare deux objets `thread::id` pour déterminer s’ils sont égaux.|
|[Operator < <, opérateur](../standard-library/thread-operators.md#op_lt_lt)|Insère une représentation textuelle d’un objet `thread::id` dans un flux.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
