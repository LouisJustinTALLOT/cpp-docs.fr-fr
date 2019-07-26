---
title: slice_array, classe
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice_array
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
ms.openlocfilehash: cf33c5f627a88698c84947f9b803edaebccf5566
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450401"
---
# <a name="slicearray-class"></a>slice_array, classe

Classe de modèle interne auxiliaire qui prend en charge les objets de secteurs en fournissant des opérations entre des tableaux de sous-ensembles définis par le secteur d'un valarray.

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

La classe décrit un objet qui stocke une référence à un objet de la classe [valarray](../standard-library/valarray-class.md) **\<Type>** , ainsi qu’un objet de la classe [slice](../standard-library/slice-class.md), qui décrit la séquence d’éléments à sélectionner à partir de l’objet **valarray\<Type>** .

La classe de modèle est créée indirectement par certaines opérations valarray. Elle ne peut pas être utilisée directement dans le programme. Classe de modèle interne auxiliaire qui est utilisée par l’opérateur slice subscript :

`slice_array`\< **Type**> `valarray`< **Type**:: `operator[]` ( `slice`).

Vous construisez `slice_array<Type>` un objet uniquement en écrivant une expression de la forme [va&#91;SL&#93;](../standard-library/valarray-class.md#op_at), pour `sl` une tranche `va`de valarray. Les fonctions membres de la classe slice_array se comportent ensuite comme les signatures `valarray<Type>`de fonctions correspondantes définies pour, sauf que seule la séquence d’éléments sélectionnés est affectée. La séquence contrôlée par le slice_array est définie par les trois paramètres du constructeur slice, l’index du premier élément dans la section (slice), le nombre d’éléments et la distance entre les éléments. Un slice_array Cut from valarray `va` déclaré par **va**[ `slice`(2, 5, 3)] sélectionne les éléments avec les index 2, 5, 8, 11 et 14 de. `va` Les index doivent être valides pour que la procédure soit valide.

## <a name="example"></a>Exemples

Consultez l’exemple [slice::slice](../standard-library/slice-class.md#slice) pour savoir comment déclarer et utiliser un slice_array.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<valarray>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
