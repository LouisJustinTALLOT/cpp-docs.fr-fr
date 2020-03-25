---
title: type_info, classe
ms.date: 11/04/2016
f1_keywords:
- type_info
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
ms.openlocfilehash: 7a016fe8fee4e5765e6172184bfa9c90eecbc687
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160669"
---
# <a name="type_info-class"></a>type_info, classe

La classe **type_info** décrit les informations de type générées dans le programme par le compilateur. Les objets de cette classe stockent efficacement un pointeur dans un nom pour le type. La classe **type_info** stocke également une valeur encodée adaptée à la comparaison de deux types d’égalité ou d’ordre de classement. Les règles d'encodage et la séquence de classement pour les types ne sont pas spécifiées et peuvent différer entre les programmes.

Le fichier d’en-tête `<typeinfo>` doit être inclus pour pouvoir utiliser la classe **type_info** . L’interface de la classe **type_info** est :

```cpp
class type_info {
public:
    type_info(const type_info& rhs) = delete; // cannot be copied
    virtual ~type_info();
    size_t hash_code() const;
    _CRTIMP_PURE bool operator==(const type_info& rhs) const;
    type_info& operator=(const type_info& rhs) = delete; // cannot be copied
    _CRTIMP_PURE bool operator!=(const type_info& rhs) const;
    _CRTIMP_PURE int before(const type_info& rhs) const;
    size_t hash_code() const noexcept;
    _CRTIMP_PURE const char* name() const;
    _CRTIMP_PURE const char* raw_name() const;
};
```

Vous ne pouvez pas instancier directement des objets de la classe **type_info** , car la classe a un seul constructeur de copie privé. La seule façon de construire un objet de **type_info** (temporaire) consiste à utiliser l’opérateur [typeid](../cpp/typeid-operator.md) . Étant donné que l’opérateur d’assignation est également privé, vous ne pouvez pas copier ou assigner des objets de classe **type_info**.

`type_info::hash_code` définit une fonction de hachage appropriée pour mapper des valeurs de type **TypeInfo** à une distribution de valeurs d’index.

Les opérateurs `==` et `!=` peuvent être utilisés pour comparer l’égalité et l’inégalité avec d’autres objets **type_info** , respectivement.

Il n'existe aucun lien entre l'ordre de classement des types et les relations d'héritage. Utilisez la fonction membre `type_info::before` pour déterminer la séquence de classement des types. Il n’existe aucune garantie que `type_info::before` produise le même résultat dans des programmes différents ou même des exécutions différentes du même programme. De cette façon, `type_info::before` est semblable à l’opérateur address-of `(&)`.

La fonction membre `type_info::name` retourne un `const char*` à une chaîne terminée par le caractère null qui représente le nom explicite du type. La mémoire désignée est mise en cache et ne doit jamais être directement libérée.

La fonction membre `type_info::raw_name` retourne un `const char*` à une chaîne se terminant par un caractère null qui représente le nom décoré du type d’objet. Le nom est réellement stocké sous sa forme décorée pour économiser de l'espace. Par conséquent, cette fonction est plus rapide que `type_info::name`, car elle n’a pas besoin de dédécorer le nom. La chaîne retournée par la fonction `type_info::raw_name` est utile dans les opérations de comparaison, mais n’est pas lisible. Si vous avez besoin d’une chaîne explicite, utilisez plutôt la fonction `type_info::name`.

Les informations de type sont générées pour les classes polymorphes uniquement si l’option de compilateur [/gr (activer les informations de type au moment de l’exécution)](../build/reference/gr-enable-run-time-type-information.md) est spécifiée.

## <a name="see-also"></a>Voir aussi

[Informations de type au moment de l’exécution](../cpp/run-time-type-information.md)
