---
title: noexcept (C++) | Microsoft Docs
ms.custom: ''
ms.date: 01/12/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noexcept_cpp
dev_langs:
- C++
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 100be1808a9a45079dba1b6cee805b3f3e6dc534
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079534"
---
# <a name="noexcept-c"></a>noexcept (C++)

**C ++ 11 :** Spécifie si une fonction peut lever des exceptions.

## <a name="syntax"></a>Syntaxe

> *expression de noexcept*: &nbsp; &nbsp; &nbsp; &nbsp; **noexcept** &nbsp; &nbsp; &nbsp; &nbsp; **noexcept (** *expression constante* **)**

### <a name="parameters"></a>Paramètres

*constant-expression*<br/>
Une expression constante de type **bool** qui indique si l’ensemble des types d’exception potentielle est vide. La version non conditionnelle est équivalente à `noexcept(true)`.

## <a name="remarks"></a>Notes

Un *noexcept expression* est une sorte de *spécification d’exception*, un suffixe à une déclaration de fonction qui représente un ensemble de types qui peuvent être mis en correspondance par un gestionnaire d’exceptions pour toute exception qui se termine un fonction. Opérateur conditionnel unaire `noexcept(` *constant_expression* `)` où *constant_expression* yeilds **true**et son synonyme inconditionnel **noexcept**, spécifiez que le jeu de types d’exception potentielle qui peut quitter une fonction est vide. Autrement dit, la fonction lève jamais d’exception et n’autorise jamais une exception d’être propagées à l’extérieur de son étendue. L’opérateur `noexcept(` *constant_expression* `)` où *constant_expression* yeilds **false**, ou l’absence d’une spécification d’exception (autres que pour une fonction destructeur ou de désallocation), indique que le jeu d’exceptions potentielles que vous pouvez quitter la fonction est l’ensemble de tous les types.

Marquer une fonction comme **noexcept** uniquement si toutes les fonctions qu’elle appelle, directement ou indirectement, sont également **noexcept** ou **const**. Le compilateur ne vérifie pas nécessairement chaque chemin d’accès du code pour les exceptions susceptibles d’atteindre un **noexcept** (fonction). Si une exception quitte la portée externe d’une fonction marquée `noexcept`, [std::terminate](../standard-library/exception-functions.md#terminate) est appelé immédiatement, et il n’existe aucune garantie que les destructeurs de tous les objets dans l’étendue seront appelées. Utilisez **noexcept** au lieu du spécificateur d’exception dynamiques `throw()`, qui est maintenant déconseillé dans la norme. Nous vous recommandons `noexcept` à n’importe quelle fonction qui ne laisse une exception se propager dans la pile des appels. Quand une fonction est déclarée **noexcept**, il permet au compilateur de générer un code plus performant dans plusieurs contextes différents. Pour plus d’informations, consultez [les spécifications d’exceptions](exception-specifications-throw-cpp.md).

## <a name="example"></a>Exemple

Une fonction de modèle qui copie son argument peut être déclarée **noexcept** à condition que l’objet copié est un type de données ancienne simple (POD). Cette fonction peut être déclarée comme suit :

```cpp
#include <type_traits>

template <typename T>
T copy_object(const T& obj) noexcept(std::is_pod<T>)
{
   // ...
}
```

## <a name="see-also"></a>Voir aussi

[Gestion d’exceptions C++](cpp-exception-handling.md)<br/>
[Spécifications d’exception (throw, noexcept)](exception-specifications-throw-cpp.md)