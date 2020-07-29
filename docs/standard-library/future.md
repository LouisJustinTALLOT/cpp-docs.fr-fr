---
title: '&lt;future&gt;'
ms.date: 11/04/2016
f1_keywords:
- <future>
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
ms.openlocfilehash: b5f18de772ea2221ecbd4098b94e0b4f14c0484c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220923"
---
# <a name="ltfuturegt"></a>&lt;future&gt;

Incluez l’en-tête standard \<future> pour définir des modèles de classe et des modèles de prise en charge qui simplifient l’exécution d’une fonction, éventuellement dans un thread séparé, et la récupération de son résultat. Le résultat est la valeur retournée par la fonction ou une exception émise par la fonction, mais qui n’est pas interceptée dans la fonction.

Cet en-tête utilise le runtime d’accès concurrentiel (ConcRT) pour pouvoir l’utiliser avec d’autres mécanismes ConcRT. Pour plus d’informations sur ConcRT, consultez [Runtime d’accès concurrentiel](../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Syntaxe

```cpp
#include <future>
```

## <a name="remarks"></a>Notes

> [!NOTE]
> Dans le code compilé à l’aide de **/CLR**, cet en-tête est bloqué.

Un *fournisseur asynchrone* stocke le résultat d’un appel de fonction. Un *objet de retour asynchrone* est utilisé pour récupérer le résultat d’un appel de fonction. Un *état asynchrone associé* permet la communication entre un fournisseur asynchrone et un ou plusieurs objets de retour asynchrones.

Un programme ne crée pas directement les objets d’état asynchrone associé. Le programme crée un fournisseur asynchrone chaque fois qu’il en a besoin, puis il crée un objet de retour asynchrone qui partage son état asynchrone associé avec le fournisseur. Les fournisseurs asynchrones et les objets de retour asynchrones gèrent les objets qui contiennent leur état asynchrone associé partagé. Quand le dernier objet qui référence l’état asynchrone associé le libère, l’objet qui contient l’état asynchrone associé est détruit.

Un fournisseur asynchrone ou un objet de retour asynchrone qui n’a aucun état asynchrone associé est *vide*.

Un état asynchrone associé est *prêt* uniquement si son fournisseur asynchrone a stocké une valeur de retour ou si une exception a été stockée.

La fonction de modèle `async` et les modèles de classe `promise` et `packaged_task` sont des fournisseurs asynchrones. Les modèles `future` de classe et `shared_future` décrivent les objets retournés asynchrones.

Chacun des modèles de classe `promise` , `future` et `shared_future` a une spécialisation pour le type **`void`** et une spécialisation partielle pour le stockage et la récupération d’une valeur par référence. Ces spécialisations diffèrent du modèle principal uniquement dans les signatures et la sémantique des fonctions qui stockent et récupèrent la valeur retournée.

Les modèles `future` de classe et `shared_future` ne sont jamais bloqués dans leurs destructeurs, sauf dans un cas qui est conservé pour la compatibilité descendante : contrairement à tous les autres futurs, pour un `future` (ou le dernier `shared_future` ) qui est attaché à une tâche démarrée avec `std::async` , le destructeur `.get()` se bloque si la tâche n’est pas terminée `.wait()` La note d’utilisation suivante a été ajoutée à la description de `std::async` dans le projet de norme : « [Remarque : Si un objet future obtenu à partir de std::async est déplacé en dehors de la portée locale, tout autre code qui utilise l’objet future doit être conscient que le destructeur de cet objet peut empêcher l’état partagé d’être prêt. Fin de la remarque] ». Dans tous les autres cas, les destructeurs `future` et `shared_future` sont nécessaires et ne se bloquent jamais.

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|Nom|Description|
|----------|-----------------|
|[future (classe)](../standard-library/future-class.md)|Décrit un objet de retour asynchrone.|
|[Classe future_error](../standard-library/future-error-class.md)|Décrit un objet d’exception qui peut être levé par des méthodes dont les types gèrent les objets `future`.|
|[Classe packaged_task](../standard-library/packaged-task-class.md)|Décrit un fournisseur asynchrone qui est un wrapper d’appel dont la signature d’appel est `Ty(ArgTypes...)`. Son état asynchrone associé contient une copie de l’objet pouvant être appelé, ainsi que le résultat potentiel.|
|[promesse (classe)](../standard-library/promise-class.md)|Décrit un fournisseur asynchrone.|
|[Classe shared_future](../standard-library/shared-future-class.md)|Décrit un objet de retour asynchrone. Contrairement à un objet `future`, un fournisseur asynchrone peut être associé à un nombre quelconque d’objets `shared_future`.|

### <a name="structures"></a>Structures

|Nom|Description|
|----------|-----------------|
|[is_error_code_enum, structure](../standard-library/is-error-code-enum-structure.md)|Spécialisation qui indique que `future_errc` est adapté au stockage d’un `error_code`.|
|[uses_allocator, structure](../standard-library/uses-allocator-structure.md)|Spécialisation qui contient toujours la valeur true.|

### <a name="functions"></a>Fonctions

|Nom|Description|
|----------|-----------------|
|[Suppr](../standard-library/future-functions.md#async)|Représente un fournisseur asynchrone.|
|[future_category](../standard-library/future-functions.md#future_category)|Retourne une référence à l’objet `error_category` qui caractérise les erreurs associées aux objets `future`.|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|Crée un `error_code` dont l’objet `error_category` caractérise les erreurs de `future`.|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|Crée un `error_condition` dont l’objet `error_category` caractérise les erreurs de `future`.|
|[swap](../standard-library/future-functions.md#swap)|Échange l’état asynchrone associé d’un objet `promise` avec celui d’un autre.|

### <a name="enumerations"></a>Énumérations

|Nom|Description|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|Fournit des noms symboliques pour toutes les erreurs signalées par la classe `future_error`.|
|[future_status](../standard-library/future-enums.md#future_status)|Fournit les noms symboliques pour les raisons qu’une fonction d’attente chronométrée peut retourner.|
|[lancer](../standard-library/future-enums.md#launch)|Représente un type de masque de bits qui décrit les modes possibles pour la fonction de modèle `async`.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
