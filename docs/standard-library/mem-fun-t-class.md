---
title: mem_fun_t, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun_t
helpviewer_keywords:
- mem_fun_t class
ms.assetid: 242566d4-750c-4c87-9d63-2e2c9d19ca2a
ms.openlocfilehash: 19ccd4835c4257a7f409bcf0f7bda1a898567458
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245084"
---
# <a name="memfunt-class"></a>mem_fun_t, classe

Classe d’adaptateur qui permet un `non_const` fonction membre qui n’accepte aucun argument d’être appelée comme objet de fonction unaire lors de l’initialisation avec un argument de pointeur. Dépréciées dans C ++ 11, supprimée dans C ++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type>
class mem_fun_t : public unary_function<Type *, Result> {
    explicit mem_fun_t(Result (Type::* _Pm)());

    Result operator()(Type* _Pleft) const;
};
```

### <a name="parameters"></a>Paramètres

*_Pm*\
Pointeur vers la fonction membre de la classe `Type` à convertir en objet de fonction.

*_Pleft*\
L’objet qui le *_Pm* fonction membre est appelée sur.

## <a name="return-value"></a>Valeur de retour

Fonction unaire adaptable.

## <a name="remarks"></a>Notes

La classe de modèle stocke une copie de *_Pm*, qui doit être un pointeur vers une fonction membre de classe `Type`, dans un objet de membre privé. Elle définit sa fonction membre `operator()` comme retournant (`_Pleft`->* `_Pm`) ().

## <a name="example"></a>Exemple

Le constructeur de `mem_fun_t` n’est généralement pas utilisé directement ; la fonction d’assistance `mem_fun` est utilisée pour adapter les fonctions membres. Pour obtenir un exemple d’utilisation des adaptateurs de fonction membre, consultez [mem_fun](../standard-library/functional-functions.md#mem_fun).
