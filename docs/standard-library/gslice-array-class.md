---
description: 'En savoir plus sur : classe gslice_array'
title: gslice_array, classe
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice_array
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
ms.openlocfilehash: 2c3cf29cd80d874265ec86d5c31a10e5c8359b8e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232029"
---
# <a name="gslice_array-class"></a>gslice_array, classe

Modèle de classe auxiliaire interne qui prend en charge les objets de tranche généraux en fournissant des opérations entre les tableaux de sous-ensembles définis par le secteur général d’un valarray.

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

La classe décrit un objet qui stocke une référence à un objet `va` de classe [valarray](../standard-library/valarray-class.md) **\<Type>** , ainsi qu’un objet `gs` de classe [GSlice](../standard-library/gslice-class.md) qui décrit la séquence d’éléments à sélectionner à partir de l' `valarray<Type>` objet.

Vous construisez un `gslice_array<Type>` objet uniquement en écrivant une expression sous la forme [va&#91;GS&#93;](../standard-library/valarray-class.md#op_at). Les fonctions membres de la classe gslice_array se comportent ensuite comme les signatures de fonctions correspondantes définies pour `valarray<Type>` , sauf que seule la séquence d’éléments sélectionnés est affectée.

Le modèle de classe est créé indirectement par certaines opérations valarray et ne peut pas être utilisé directement dans le programme. Un modèle de classe auxiliaire interne est utilisé à la place par l’opérateur d’indice de secteur :

`gslice_array`\< **Type**>`valarray` \< **Type**> :: `operator[]` ( **constgslice&**).

Vous construisez un `gslice_array<Type>` objet uniquement en écrivant une expression sous la forme `va[gsl]` , pour une tranche `gsl` de valarray `va` . Les fonctions membres de la classe gslice_array se comportent ensuite comme les signatures de fonctions correspondantes définies pour `valarray<Type>` , sauf que seule la séquence d’éléments sélectionnés est affectée. La séquence contrôlée par le gslice_array est définie par les trois paramètres du constructeur slice, l’index du premier élément de la première section, le nombre d’éléments dans chaque section et la distance entre les éléments de chaque section.

Dans l’exemple suivant :

```cpp
const size_t lv[] = {2, 3};
const size_t dv[] = {7, 2};
const valarray<size_t> len(lv, 2), str(dv, 2);

// va[gslice(3, len, str)] selects elements with
//   indices 3, 5, 7, 10, 12, 14
```

Les index doivent être valides pour que la procédure soit valide.

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [gslice::gslice](../standard-library/gslice-class.md#gslice) pour savoir comment déclarer et utiliser un slice_array.

## <a name="requirements"></a>Spécifications

**En-tête :**\<valarray>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
