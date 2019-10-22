---
title: mem_fun_ref_t, classe
ms.date: 02/21/2019
f1_keywords:
- functional/std::mem_fun_ref_t
helpviewer_keywords:
- mem_fun_ref_t class
ms.assetid: 7dadcac3-8d33-4e4b-a792-81bd53d3df39
ms.openlocfilehash: d8f5ef05d1bdeec694cdf22d7e7a163478127dfc
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687757"
---
# <a name="mem_fun_ref_t-class"></a>mem_fun_ref_t, classe

Classe d’adaptateur qui permet à une fonction membre `non_const` qui n’accepte aucun argument d’être appelée comme objet de fonction unaire en cas d’initialisation avec un argument de référence. Déconseillé dans C++ 11, supprimé en C++ 17.

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

*_Pm* \
Pointeur vers la fonction membre de la classe `Type` à convertir en objet de fonction.

\ *gauche*
Objet sur lequel la fonction membre *_Pm* est appelée.

## <a name="return-value"></a>Valeur de retour

Fonction unaire adaptable.

## <a name="remarks"></a>Notes

Le modèle de classe stocke une copie de *_Pm*, qui doit être un pointeur vers une fonction membre de la classe `Type`, dans un objet membre privé. Elle définit sa fonction membre `operator()` comme retournant (**Left**. * `_Pm`) ().

## <a name="example"></a>Exemple

Le constructeur de `mem_fun_ref_t` n’est généralement pas utilisé directement ; la fonction d’assistance `mem_fun_ref` est utilisée pour adapter les fonctions membres. Pour obtenir un exemple d’utilisation des adaptateurs de fonction membre, consultez [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref).
