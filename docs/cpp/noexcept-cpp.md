---
title: noexcept (C++)
ms.date: 11/19/2019
f1_keywords:
- noexcept_cpp
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
ms.openlocfilehash: 2618c7e9b35e4ba50ad1bda20a8694dd829ec2d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223640"
---
# <a name="noexcept-c"></a>noexcept (C++)

**C++ 11 :** Spécifie si une fonction peut lever des exceptions.

## <a name="syntax"></a>Syntaxe

> *noexcept-expression*: \
> &nbsp;&nbsp;&nbsp;&nbsp;**`noexcept`**\
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept (** *constante-expression* **)**

### <a name="parameters"></a>Paramètres

*constant-expression*<br/>
Expression constante de type **`bool`** qui indique si l’ensemble des types d’exception potentiels est vide. La version inconditionnelle est équivalente à `noexcept(true)` .

## <a name="remarks"></a>Notes

Une *expression noexcept* est un type de *spécification d’exception*, un suffixe à une déclaration de fonction qui représente un ensemble de types qui peuvent être mis en correspondance par un gestionnaire d’exceptions pour toute exception qui quitte une fonction. Opérateur conditionnel unaire `noexcept(` *constant_expression* `)` où *constant_expression* produit **`true`** , et son synonyme **`noexcept`** non conditionnel, spécifie que l’ensemble des types d’exception potentiels qui peuvent quitter une fonction est vide. Autrement dit, la fonction ne lève jamais d’exception et n’autorise jamais la propagation d’une exception en dehors de sa portée. L’opérateur `noexcept(` *constant_expression* `)` où *constant_expression* produit **`false`** , ou l’absence d’une spécification d’exception (autre que pour un destructeur ou une fonction de désallocation), indique que l’ensemble des exceptions potentielles qui peuvent quitter la fonction est l’ensemble de tous les types.

Marquer une fonction comme **`noexcept`** uniquement si toutes les fonctions qu’elle appelle, directement ou indirectement, sont également **`noexcept`** ou **`const`** . Le compilateur ne vérifie pas nécessairement chaque chemin d’accès du code pour les exceptions susceptibles de se propager vers une **`noexcept`** fonction. Si une exception quitte la portée externe d’une fonction marquée **`noexcept`** , [std :: Terminate](../standard-library/exception-functions.md#terminate) est appelé immédiatement, et il n’y a aucune garantie que les destructeurs de tous les objets dans la portée seront appelés. Utilisez **`noexcept`** à la place du spécificateur d’exception dynamique `throw()` , qui est maintenant déconseillé dans la norme. Nous vous recommandons **`noexcept`** d’appliquer à n’importe quelle fonction qui n’autorise jamais une exception à se propager vers le haut de la pile des appels. Lorsqu’une fonction est déclarée **`noexcept`** , elle permet au compilateur de générer du code plus efficace dans plusieurs contextes différents. Pour plus d’informations, consultez [spécifications d’exception](exception-specifications-throw-cpp.md).

## <a name="example"></a>Exemple

Une fonction de modèle qui copie son argument peut être déclarée **`noexcept`** dans la condition que l’objet en cours de copie est un type de données (Pod) ordinaire. Cette fonction peut être déclarée comme suit :

```cpp
#include <type_traits>

template <typename T>
T copy_object(const T& obj) noexcept(std::is_pod<T>)
{
   // ...
}
```

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques C++ modernes pour les exceptions et la gestion des erreurs](errors-and-exception-handling-modern-cpp.md)<br/>
[Spécifications d’exception (throw, noexcept)](exception-specifications-throw-cpp.md)
