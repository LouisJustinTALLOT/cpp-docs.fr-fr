---
title: gslice_array, classe
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice_array
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
ms.openlocfilehash: 37c54d09fdfe920c832c4baa7984fee4e090d04a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448919"
---
# <a name="gslicearray-class"></a>gslice_array, classe

Classe de modèle interne auxiliaire qui prend en charge les objets de secteurs généraux en fournissant des opérations entre des tableaux de sous-ensembles définis par le secteur général d'un valarray.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class gslice_array : public gsplice {
public:
    typedef Type value_type;
    void operator=(const valarray<Type>& x) const;

    void operator=(const Type& x) const;

    void operator*=(const valarray<Type>& x) const;

    void operator/=(const valarray<Type>& x) const;

    void operator%=(const valarray<Type>& x) const;

    void operator+=(const valarray<Type>& x) const;

    void operator-=(const valarray<Type>& x) const;

    void operator^=(const valarray<Type>& x) const;

    void operator&=(const valarray<Type>& x) const;

    void operator|=(const valarray<Type>& x) const;

    void operator<<=(const valarray<Type>& x) const;

    void operator>>=(const valarray<Type>& x) const;

// The rest is private or implementation defined
}
```

## <a name="remarks"></a>Notes

La classe décrit un objet qui stocke une référence à un `va` objet de classe [valarray](../standard-library/valarray-class.md) **\<de type >** , ainsi qu' `gs` un objet de classe [GSlice](../standard-library/gslice-class.md) qui décrit la séquence d’éléments à sélectionner. `valarray<Type>` objet.

Vous construisez `gslice_array<Type>` un objet uniquement en écrivant une expression de la forme [va&#91;GS&#93;](../standard-library/valarray-class.md#op_at). Les fonctions membres de la classe gslice_array se comportent ensuite comme les signatures `valarray<Type>`de fonctions correspondantes définies pour, sauf que seule la séquence d’éléments sélectionnés est affectée.

La classe de modèle est créée indirectement par certaines opérations valarray et ne peut pas être utilisée directement dans le programme. Une classe de modèle interne auxiliaire est utilisée à la place par l’opérateur d’indice slice :

`gslice_array`\< **Type**> `valarray`\< **Type**>:: `operator[]` ( **constgslice&** ).

Vous construisez `gslice_array<Type>` un objet uniquement en écrivant une expression sous `va[gsl]`la forme, pour `gsl` une tranche `va`de valarray. Les fonctions membres de la classe gslice_array se comportent ensuite comme les signatures `valarray<Type>`de fonctions correspondantes définies pour, sauf que seule la séquence d’éléments sélectionnés est affectée. La séquence contrôlée par le gslice_array est définie par les trois paramètres du constructeur slice, l’index du premier élément de la première section, le nombre d’éléments dans chaque section et la distance entre les éléments de chaque section.

Dans l’exemple suivant :

```cpp
const size_t lv[] = {2, 3};
const size_t dv[] = {7, 2};
const valarray<size_t> len(lv, 2), str(dv, 2);

// va[gslice(3, len, str)] selects elements with
//   indices 3, 5, 7, 10, 12, 14
```

Les index doivent être valides pour que la procédure soit valide.

## <a name="example"></a>Exemples

Consultez l’exemple relatif à [gslice::gslice](../standard-library/gslice-class.md#gslice) pour savoir comment déclarer et utiliser un slice_array.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<valarray>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
