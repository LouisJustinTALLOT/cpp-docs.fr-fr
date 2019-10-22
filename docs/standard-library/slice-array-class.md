---
title: slice_array, classe
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice_array
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
ms.openlocfilehash: 358348a57b823fcea82cd296967c83778819361d
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688962"
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

La classe décrit un objet qui stocke une référence à un objet de la classe [valarray](../standard-library/valarray-class.md) **\<Type>** , ainsi qu’un objet de la classe [slice](../standard-library/slice-class.md), qui décrit la séquence d’éléments à sélectionner à partir de l’objet **valarray\<Type>** .

Le modèle de classe est créé indirectement par certaines opérations valarray et ne peut pas être utilisé directement dans le programme. Modèle de classe auxiliaire interne utilisé par l’opérateur d’indice de secteur :

`slice_array`\< **Type**> `valarray`< **Type**:: `operator[]` ( `slice`).

Vous construisez un objet `slice_array<Type>` uniquement en écrivant une expression de [la&#91;forme&#93;va SL](../standard-library/valarray-class.md#op_at), pour une tranche `sl` de valarray `va`. Les fonctions membres de la classe slice_array se comportent ensuite comme les signatures de fonctions correspondantes définies pour `valarray<Type>`, sauf que seule la séquence d’éléments sélectionnés est affectée. La séquence contrôlée par le slice_array est définie par les trois paramètres du constructeur slice, l’index du premier élément dans la section (slice), le nombre d’éléments et la distance entre les éléments. Un slice_array Cut from valarray `va` déclaré par la fonction **va**[`slice` (2, 5, 3)] sélectionne les éléments avec les index 2, 5, 8, 11 et 14 de `va`. Les index doivent être valides pour que la procédure soit valide.

## <a name="example"></a>Exemple

Consultez l’exemple [slice::slice](../standard-library/slice-class.md#slice) pour savoir comment déclarer et utiliser un slice_array.

## <a name="requirements"></a>spécifications

**En-tête :** \<valarray>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
