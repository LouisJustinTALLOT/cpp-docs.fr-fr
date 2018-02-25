---
title: slice_array, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- valarray/std::slice_array
dev_langs:
- C++
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f2f9ae76aad8078511ed2c37e8f15efcee361cc4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="slicearray-class"></a>slice_array, classe
Classe de modèle interne auxiliaire qui prend en charge les objets de secteurs en fournissant des opérations entre des tableaux de sous-ensembles définis par le secteur d'un valarray.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 La classe décrit un objet qui stocke une référence à un objet de la classe [valarray](../standard-library/valarray-class.md)**\<Type>**, ainsi qu’un objet de la classe [slice](../standard-library/slice-class.md), qui décrit la séquence d’éléments à sélectionner à partir de l’objet **valarray\<Type>**.  
  
 La classe de modèle est créée indirectement par certaines opérations valarray. Elle ne peut pas être utilisée directement dans le programme. Classe de modèle interne auxiliaire qui est utilisée par l’opérateur slice subscript :  
  
 `slice_array`\< **Type**> `valarray`< **Type**:: `operator[]` ( `slice`).  
  
 Vous construisez un objet **slice_array\<Type>** uniquement en écrivant une expression sous la forme [va&#91;sl&#93;](../standard-library/valarray-class.md#op_at), pour une section **sl** du valarray **va**. Les fonctions membres de la classe slice_array se comportent ensuite comme les signatures de fonctions correspondantes définies pour **valarray\<Type>**, sauf que seule la séquence d’éléments sélectionnée est affectée. La séquence contrôlée par le slice_array est définie par les trois paramètres du constructeur slice, l’index du premier élément dans la section (slice), le nombre d’éléments et la distance entre les éléments. Un slice_array coupé du valarray **va** déclaré par **va**[ `slice`(2, 5, 3)] sélectionne les éléments ayant les index 2, 5, 8, 11 et 14 dans **va**. Les index doivent être valides pour que la procédure soit valide.  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple [slice::slice](../standard-library/slice-class.md#slice) pour savoir comment déclarer et utiliser un slice_array.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<valarray>  
  
 **Espace de noms :** std  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

