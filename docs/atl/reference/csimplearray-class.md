---
description: 'En savoir plus sur : classe CSimpleArray'
title: CSimpleArray, classe
ms.date: 11/04/2016
f1_keywords:
- CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::Add
- ATLSIMPCOLL/ATL::CSimpleArray::Find
- ATLSIMPCOLL/ATL::CSimpleArray::GetData
- ATLSIMPCOLL/ATL::CSimpleArray::GetSize
- ATLSIMPCOLL/ATL::CSimpleArray::Remove
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleArray::SetAtIndex
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
ms.openlocfilehash: 95750662587c7ab47500a338c3ecd7e74a92eb34
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140788"
---
# <a name="csimplearray-class"></a>CSimpleArray, classe

Cette classe fournit des méthodes pour gérer un tableau simple.

## <a name="syntax"></a>Syntaxe

```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>
class CSimpleArray
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données à stocker dans le tableau.

*TEqual*<br/>
Objet de trait, définissant le test d’égalité pour les éléments de type *T*.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleArray::CSimpleArray](#csimplearray)|Constructeur pour le tableau simple.|
|[CSimpleArray :: ~ CSimpleArray](#dtor)|Destructeur pour le tableau simple.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleArray :: Add](#add)|Ajoute un nouvel élément au tableau.|
|[CSimpleArray :: find](#find)|Recherche un élément dans le tableau.|
|[CSimpleArray :: GetData](#getdata)|Retourne un pointeur vers les données stockées dans le tableau.|
|[CSimpleArray :: est à obtenir](#getsize)|Retourne le nombre d’éléments stockés dans le tableau.|
|[CSimpleArray :: Remove](#remove)|Supprime un élément donné du tableau.|
|[CSimpleArray :: RemoveAll](#removeall)|Supprime tous les éléments du tableau.|
|[CSimpleArray :: RemoveAt](#removeat)|Supprime l’élément spécifié du tableau.|
|[CSimpleArray :: SetAtIndex (](#setatindex)|Définit l’élément spécifié dans le tableau.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleArray::operator\[\]](#operator_at)|Récupère un élément du tableau.|
|[CSimpleArray :: Operator =](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

`CSimpleArray` fournit des méthodes pour créer et gérer un tableau simple, d’un type donné `T` .

Le paramètre `TEqual` fournit un moyen de définir une fonction d’égalité pour deux éléments de type `T` . En créant une classe similaire à [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md), il est possible de modifier le comportement du test d’égalité pour un tableau donné. Par exemple, lors de la gestion d’un tableau de pointeurs, il peut être utile de définir l’égalité comme en fonction des valeurs référencées par les pointeurs. L’implémentation par défaut utilise **Operator = ()**.

`CSimpleArray`Et [CSimpleMap](../../atl/reference/csimplemap-class.md) sont conçus pour un petit nombre d’éléments. [CAtlArray](../../atl/reference/catlarray-class.md) et [CAtlMap](../../atl/reference/catlmap-class.md) doivent être utilisés lorsque le tableau contient un grand nombre d’éléments.

## <a name="requirements"></a>Spécifications

**En-tête :** atlsimpcoll. h

## <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]

## <a name="csimplearrayadd"></a><a name="add"></a> CSimpleArray :: Add

Ajoute un nouvel élément au tableau.

```
BOOL Add(const T& t);
```

### <a name="parameters"></a>Paramètres

*t*<br/>
Élément à ajouter au tableau.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si l’élément est correctement ajouté au tableau ; sinon, FALSe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]

## <a name="csimplearraycsimplearray"></a><a name="csimplearray"></a> CSimpleArray::CSimpleArray

Constructeur de l’objet tableau.

```
CSimpleArray(const CSimpleArray<T, TEqual>& src);
CSimpleArray();
```

### <a name="parameters"></a>Paramètres

*src*<br/>
Objet `CSimpleArray` existant.

### <a name="remarks"></a>Notes

Initialise les membres de données, en créant un nouvel `CSimpleArray` objet vide ou en créant une copie d’un `CSimpleArray` objet existant.

## <a name="csimplearraycsimplearray"></a><a name="dtor"></a> CSimpleArray :: ~ CSimpleArray

Destructeur.

```
~CSimpleArray();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="csimplearrayfind"></a><a name="find"></a> CSimpleArray :: find

Recherche un élément dans le tableau.

```
int Find(const T& t) const;
```

### <a name="parameters"></a>Paramètres

*t*<br/>
Élément à rechercher.

### <a name="return-value"></a>Valeur renvoyée

Retourne l’index de l’élément trouvé, ou-1 si l’élément est introuvable.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]

## <a name="csimplearraygetdata"></a><a name="getdata"></a> CSimpleArray :: GetData

Retourne un pointeur vers les données stockées dans le tableau.

```
T* GetData() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers les données dans le tableau.

## <a name="csimplearraygetsize"></a><a name="getsize"></a> CSimpleArray :: est à obtenir

Retourne le nombre d’éléments stockés dans le tableau.

```
int GetSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre d’éléments stockés dans le tableau.

## <a name="csimplearrayoperator-"></a><a name="operator_at"></a> CSimpleArray ::, opérateur \[\]

Récupère un élément du tableau.

```
T& operator[](int nindex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’élément.

### <a name="return-value"></a>Valeur renvoyée

Retourne l’élément du tableau référencé par *nIndex*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]

## <a name="csimplearrayoperator-"></a><a name="operator_eq"></a> CSimpleArray :: Operator =

Opérateur d'assignation.

```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
Tableau à copier.

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers l’objet mis à jour `CSimpleArray` .

### <a name="remarks"></a>Notes

Copie tous les éléments de l' `CSimpleArray` objet référencé par *src* dans l’objet de tableau actuel, en remplaçant toutes les données existantes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]

## <a name="csimplearrayremove"></a><a name="remove"></a> CSimpleArray :: Remove

Supprime un élément donné du tableau.

```
BOOL Remove(const T& t);
```

### <a name="parameters"></a>Paramètres

*t*<br/>
Élément à supprimer du tableau.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si l’élément est trouvé et supprimé ; sinon, FALSe.

### <a name="remarks"></a>Notes

Lorsqu’un élément est supprimé, les éléments restants dans le tableau sont renumérotés pour remplir l’espace vide.

## <a name="csimplearrayremoveall"></a><a name="removeall"></a> CSimpleArray :: RemoveAll

Supprime tous les éléments du tableau.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Notes

Supprime tous les éléments actuellement stockés dans le tableau.

## <a name="csimplearrayremoveat"></a><a name="removeat"></a> CSimpleArray :: RemoveAt

Supprime l’élément spécifié du tableau.

```
BOOL RemoveAtint nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index pointant vers l’élément à supprimer.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE si l’élément a été supprimé, FALSe si l’index n’est pas valide.

### <a name="remarks"></a>Notes

Lorsqu’un élément est supprimé, les éléments restants dans le tableau sont renumérotés pour remplir l’espace vide.

## <a name="csimplearraysetatindex"></a><a name="setatindex"></a> CSimpleArray :: SetAtIndex (

Définit l’élément spécifié dans le tableau.

```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de l’élément à modifier.

*t*<br/>
Valeur à assigner à l’élément spécifié.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur TRUE en cas de réussite, FALSe si l’index n’est pas valide.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
