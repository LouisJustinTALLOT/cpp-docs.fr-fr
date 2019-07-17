---
title: mem_fun_ref_t, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun_ref_t
helpviewer_keywords:
- mem_fun_ref_t class
ms.assetid: 7dadcac3-8d33-4e4b-a792-81bd53d3df39
ms.openlocfilehash: 0879736863a9b8052d19cc86dc5636ba14bcf993
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240609"
---
# <a name="memfunreft-class"></a>mem_fun_ref_t, classe

Classe d’adaptateur qui permet un `non_const` fonction membre qui n’accepte aucun argument d’être appelée comme objet de fonction unaire lors de l’initialisation avec un argument de référence. Dépréciées dans C ++ 11, supprimée dans C ++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Result, class Type>
class mem_fun_ref_t : public unary_function<Type, Result> {
    explicit mem_fun_ref_t(
    Result (Type::* _Pm)());

    Result operator()(Type& left) const;
};
```

### <a name="parameters"></a>Paramètres

*_Pm*\
Pointeur vers la fonction membre de la classe `Type` à convertir en objet de fonction.

*Gauche*\
L’objet qui le *_Pm* fonction membre est appelée sur.

## <a name="return-value"></a>Valeur de retour

Fonction unaire adaptable.

## <a name="remarks"></a>Notes

La classe de modèle stocke une copie de *_Pm*, qui doit être un pointeur vers une fonction membre de classe `Type`, dans un objet de membre privé. Elle définit sa fonction membre `operator()` comme retournant (**gauche**. * `_Pm`) ().

## <a name="example"></a>Exemples

Le constructeur de `mem_fun_ref_t` n’est généralement pas utilisé directement ; la fonction d’assistance `mem_fun_ref` est utilisée pour adapter les fonctions membres. Pour obtenir un exemple d’utilisation des adaptateurs de fonction membre, consultez [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref).
