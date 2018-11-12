---
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
ms.openlocfilehash: 6395e324d5efdba208a7f77d86ca466fb7cdbb5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460461"
---
# <a name="csimplearray-class"></a>CSimpleArray, classe

Cette classe fournit des méthodes pour la gestion d’un tableau simple.

## <a name="syntax"></a>Syntaxe

```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>
class CSimpleArray
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données à stocker dans le tableau.

*TEqual*<br/>
Un objet de trait, en définissant le test d’égalité pour les éléments de type *T*.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleArray::CSimpleArray](#csimplearray)|Le constructeur pour le tableau simple.|
|[CSimpleArray :: ~ CSimpleArray](#dtor)|Le destructeur de tableau simple.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleArray::Add](#add)|Ajoute un nouvel élément dans le tableau.|
|[CSimpleArray::Find](#find)|Recherche un élément dans le tableau.|
|[CSimpleArray::GetData](#getdata)|Retourne un pointeur vers les données stockées dans le tableau.|
|[CSimpleArray::GetSize](#getsize)|Retourne le nombre d’éléments stockés dans le tableau.|
|[CSimpleArray::Remove](#remove)|Supprime un élément donné du tableau.|
|[CSimpleArray::RemoveAll](#removeall)|Supprime tous les éléments du tableau.|
|[CSimpleArray::RemoveAt](#removeat)|Supprime l’élément spécifié du tableau.|
|[CSimpleArray::SetAtIndex](#setatindex)|Définit l’élément spécifié dans le tableau.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleArray::operator\[\]](#operator_at)|Récupère un élément du tableau.|
|[CSimpleArray::operator =](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

`CSimpleArray` Fournit des méthodes pour créer et gérer un simple tableau, d’un type donné `T`.

Le paramètre `TEqual` fournit un moyen de définir une fonction d’égalité pour les deux éléments de type `T`. En créant une classe similaire à [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md), il est possible de modifier le comportement du test d’égalité pour n’importe quel tableau donné. Par exemple, lorsque vous travaillez avec un tableau de pointeurs, il peut être utile définir l’égalité en tant qu’en fonction des valeurs que les pointeurs de référence. L’implémentation par défaut utilise **operator=()**.

Les deux `CSimpleArray` et [CSimpleMap](../../atl/reference/csimplemap-class.md) sont conçus pour un petit nombre d’éléments. [CAtlArray](../../atl/reference/catlarray-class.md) et [CAtlMap](../../atl/reference/catlmap-class.md) doit être utilisé lorsque le tableau contient un grand nombre d’éléments.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsimpcoll.h

## <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]

##  <a name="add"></a>  CSimpleArray::Add

Ajoute un nouvel élément dans le tableau.

```
BOOL Add(const T& t);
```

### <a name="parameters"></a>Paramètres

*t*<br/>
L’élément à ajouter au tableau.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’élément est correctement ajouté dans le tableau, FALSE sinon.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]

##  <a name="csimplearray"></a>  CSimpleArray::CSimpleArray

Le constructeur de l’objet de tableau.

```
CSimpleArray(const CSimpleArray<T, TEqual>& src);
CSimpleArray();
```

### <a name="parameters"></a>Paramètres

*src*<br/>
Objet `CSimpleArray` existant.

### <a name="remarks"></a>Notes

Initialise les membres de données, création d’un nouveau vide `CSimpleArray` objet ou une copie d’un existant `CSimpleArray` objet.

##  <a name="dtor"></a>  CSimpleArray :: ~ CSimpleArray

Destructeur.

```
~CSimpleArray();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

##  <a name="find"></a>  CSimpleArray::Find

Recherche un élément dans le tableau.

```
int Find(const T& t) const;
```

### <a name="parameters"></a>Paramètres

*t*<br/>
L’élément à rechercher.

### <a name="return-value"></a>Valeur de retour

Retourne l’index de l’élément est trouvé, ou -1 si l’élément est introuvable.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]

##  <a name="getdata"></a>  CSimpleArray::GetData

Retourne un pointeur vers les données stockées dans le tableau.

```
T* GetData() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers les données dans le tableau.

##  <a name="getsize"></a>  CSimpleArray::GetSize

Retourne le nombre d’éléments stockés dans le tableau.

```
int GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’éléments stockés dans le tableau.

##  <a name="operator_at"></a>  CSimpleArray::operator \[\]

Récupère un élément du tableau.

```
T& operator[](int nindex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index d’élément.

### <a name="return-value"></a>Valeur de retour

Retourne l’élément de tableau référencé par *nIndex*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]

##  <a name="operator_eq"></a>  CSimpleArray::operator =

Opérateur d'assignation.

```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
Tableau dans lequel copier.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la mise à jour `CSimpleArray` objet.

### <a name="remarks"></a>Notes

Copie tous les éléments à partir de la `CSimpleArray` objet référencé par *src* dans l’objet de tableau actuel, en remplaçant toutes les données existantes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]

##  <a name="remove"></a>  CSimpleArray::Remove

Supprime un élément donné du tableau.

```
BOOL Remove(const T& t);
```

### <a name="parameters"></a>Paramètres

*t*<br/>
L’élément à supprimer du tableau.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’élément est trouvé et supprimé, FALSE sinon.

### <a name="remarks"></a>Notes

Lorsqu’un élément est supprimé, les éléments restants dans le tableau sont alors renumérotés pour remplir l’espace vide.

##  <a name="removeall"></a>  CSimpleArray::RemoveAll

Supprime tous les éléments du tableau.

```
void RemoveAll();
```

### <a name="remarks"></a>Notes

Supprime tous les éléments actuellement stockés dans le tableau.

##  <a name="removeat"></a>  CSimpleArray::RemoveAt

Supprime l’élément spécifié du tableau.

```
BOOL RemoveAtint nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index qui pointe vers l’élément à supprimer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’élément a été supprimé, FALSE si l’index n’est pas valide.

### <a name="remarks"></a>Notes

Lorsqu’un élément est supprimé, les éléments restants dans le tableau sont alors renumérotés pour remplir l’espace vide.

##  <a name="setatindex"></a>  CSimpleArray::SetAtIndex

Définir l’élément spécifié dans le tableau.

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

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si réussi et FALSE si l’index n’est pas valide.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
