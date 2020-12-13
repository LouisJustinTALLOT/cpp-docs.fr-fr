---
description: 'En savoir plus sur : classe slice_array'
title: slice_array, classe
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice_array
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
ms.openlocfilehash: 580a09d99b08bc563c64571247d74a980eb229f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153978"
---
# <a name="slice_array-class"></a>slice_array, classe

Modèle de classe auxiliaire interne qui prend en charge les objets Slice en fournissant des opérations entre les tableaux de sous-ensembles définis par le secteur d’un valarray.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class slice_array : public slice {
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

La classe décrit un objet qui stocke une référence à un objet de classe [valarray](../standard-library/valarray-class.md) **\<Type>** , ainsi qu’un objet de classe [Slice](../standard-library/slice-class.md), qui décrit la séquence d’éléments à sélectionner à partir de l’objet **valarray \<Type>** .

Le modèle de classe est créé indirectement par certaines opérations valarray et ne peut pas être utilisé directement dans le programme. Modèle de classe auxiliaire interne utilisé par l’opérateur d’indice de secteur :

`slice_array`\< **Type**>`valarray` <  **Tapez**:: `operator[]` ( `slice` ).

Vous construisez un `slice_array<Type>` objet uniquement en écrivant une expression sous la forme [va&#91;SL&#93;](../standard-library/valarray-class.md#op_at), pour une tranche `sl` de valarray `va` . Les fonctions membres de la classe slice_array se comportent ensuite comme les signatures de fonctions correspondantes définies pour `valarray<Type>` , sauf que seule la séquence d’éléments sélectionnés est affectée. La séquence contrôlée par le slice_array est définie par les trois paramètres du constructeur slice, l’index du premier élément dans la section (slice), le nombre d’éléments et la distance entre les éléments. Une slice_array coupée de valarray `va` déclarée par **va**[ `slice` (2, 5, 3)] sélectionne les éléments avec les index 2, 5, 8, 11 et 14 de `va` . Les index doivent être valides pour que la procédure soit valide.

## <a name="example"></a>Exemple

Consultez l’exemple [slice::slice](../standard-library/slice-class.md#slice) pour savoir comment déclarer et utiliser un slice_array.

## <a name="requirements"></a>Spécifications

**En-tête :**\<valarray>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
