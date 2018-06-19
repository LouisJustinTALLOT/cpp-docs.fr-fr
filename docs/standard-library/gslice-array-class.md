---
title: gslice_array, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::gslice_array
dev_langs:
- C++
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff9718a98244379fccde78b18fa70ef46c7e7a76
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845643"
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

La classe décrit un objet qui stocke une référence à un objet **va** de la classe [valarray](../standard-library/valarray-class.md)**\<Type>**, ainsi qu’un objet **gs** de la classe [gslice](../standard-library/gslice-class.md), qui décrit la séquence d’éléments à sélectionner à partir de l’objet **valarray\<Type>**.

Vous construisez un objet **gslice_array\<Type>** uniquement en écrivant une expression sous la forme [va&#91;gs&#93;](../standard-library/valarray-class.md#op_at). Les fonctions membres de la classe gslice_array se comportent ensuite comme les signatures de fonction correspondantes définies pour **valarray\<Type>**, sauf que seule la séquence d’éléments sélectionnés est affectée.

La classe de modèle est créée indirectement par certaines opérations valarray et ne peut pas être utilisée directement dans le programme. Une classe de modèle interne auxiliaire est utilisée à la place par l’opérateur d’indice slice :

`gslice_array`\< **Type**> `valarray`\< **Type**>:: `operator[]` ( **constgslice&**).

Vous construisez un objet **gslice_array\<Type>** uniquement en écrivant une expression sous la forme **va[gsl]**, pour une section **gsl** de valarray **va**. Les fonctions membres de la classe gslice_array se comportent ensuite comme les signatures de fonction correspondantes définies pour **valarray\<Type>**, sauf que seule la séquence d’éléments sélectionnés est affectée. La séquence contrôlée par le gslice_array est définie par les trois paramètres du constructeur slice, l’index du premier élément de la première section, le nombre d’éléments dans chaque section et la distance entre les éléments de chaque section.

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

**En-tête :** \<valarray>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
