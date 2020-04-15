---
title: Classe CSimpleArray
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
ms.openlocfilehash: e45c9b3fd778aacd3a3e2d5d3696661afa0c6fb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330903"
---
# <a name="csimplearray-class"></a>Classe CSimpleArray

Cette classe fournit des méthodes pour gérer un tableau simple.

## <a name="syntax"></a>Syntaxe

```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>
class CSimpleArray
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données à stocker dans le tableau.

*TEqual (TEqual)*<br/>
Un objet trait, définissant le critère d’égalité pour les éléments de type *T*.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleArray::CSimpleArray](#csimplearray)|Le constructeur pour le tableau simple.|
|[CSimpleArray: :CSimpleArray](#dtor)|Le destructeur pour le tableau simple.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleArray::Ajouter](#add)|Ajoute un nouvel élément au tableau.|
|[CSimpleArray::Trouver](#find)|Trouve un élément dans le tableau.|
|[CSimpleArray::GetData](#getdata)|Renvoie un pointeur aux données stockées dans le tableau.|
|[CSimpleArray::GetSize](#getsize)|Retourne le nombre d’éléments stockés dans le tableau.|
|[CSimpleArray::Supprimer](#remove)|Supprime un élément donné du tableau.|
|[CSimpleArray::RemoveAll](#removeall)|Supprime tous les éléments du tableau.|
|[CSimpleArray::RemoveAt](#removeat)|Supprime l’élément spécifié du tableau.|
|[CSimpleArray::SetAtIndex](#setatindex)|Définit l’élément spécifié dans le tableau.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CSimpleArray::operator\[\]](#operator_at)|Récupère un élément du tableau.|
|[CSimpleArray::opérateur](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

`CSimpleArray`fournit des méthodes pour créer et gérer `T`un tableau simple, de n’importe quel type donné.

Le `TEqual` paramètre fournit un moyen de définir `T`une fonction d’égalité pour deux éléments de type . En créant une classe similaire à [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md), il est possible de modifier le comportement du test d’égalité pour n’importe quel tableau donné. Par exemple, lorsqu’il s’agit d’un tableau de pointeurs, il peut être utile de définir l’égalité comme en fonction des valeurs de référence des pointeurs. La mise en œuvre par défaut utilise **l’opérateur ()**.

Les `CSimpleArray` deux et [CSimpleMap](../../atl/reference/csimplemap-class.md) sont conçus pour un petit nombre d’éléments. [CAtlArray](../../atl/reference/catlarray-class.md) et [CAtlMap](../../atl/reference/catlmap-class.md) doivent être utilisés lorsque le tableau contient un grand nombre d’éléments.

## <a name="requirements"></a>Spécifications

**En-tête:** atlsimpcoll.h

## <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]

## <a name="csimplearrayadd"></a><a name="add"></a>CSimpleArray::Ajouter

Ajoute un nouvel élément au tableau.

```
BOOL Add(const T& t);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
L’élément à ajouter au tableau.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’élément est ajouté avec succès à la gamme, FALSE autrement.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]

## <a name="csimplearraycsimplearray"></a><a name="csimplearray"></a>CSimpleArray::CSimpleArray

Le constructeur de l’objet de tableau.

```
CSimpleArray(const CSimpleArray<T, TEqual>& src);
CSimpleArray();
```

### <a name="parameters"></a>Paramètres

*src*<br/>
Objet `CSimpleArray` existant.

### <a name="remarks"></a>Notes

Initialise les membres des données, `CSimpleArray` créant un nouvel objet `CSimpleArray` vide, ou une copie d’un objet existant.

## <a name="csimplearraycsimplearray"></a><a name="dtor"></a>CSimpleArray: :CSimpleArray

Destructeur.

```
~CSimpleArray();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

## <a name="csimplearrayfind"></a><a name="find"></a>CSimpleArray::Trouver

Trouve un élément dans le tableau.

```
int Find(const T& t) const;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
L’élément pour lequel rechercher.

### <a name="return-value"></a>Valeur de retour

Retourne l’index de l’élément trouvé, ou -1 si l’élément n’est pas trouvé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]

## <a name="csimplearraygetdata"></a><a name="getdata"></a>CSimpleArray::GetData

Renvoie un pointeur aux données stockées dans le tableau.

```
T* GetData() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur aux données du tableau.

## <a name="csimplearraygetsize"></a><a name="getsize"></a>CSimpleArray::GetSize

Retourne le nombre d’éléments stockés dans le tableau.

```
int GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’éléments stockés dans le tableau.

## <a name="csimplearrayoperator-"></a><a name="operator_at"></a>CSimpleArray::opérateur\[\]

Récupère un élément du tableau.

```
T& operator[](int nindex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’indice d’élément.

### <a name="return-value"></a>Valeur de retour

Retourne l’élément du tableau référencé par *nIndex*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]

## <a name="csimplearrayoperator-"></a><a name="operator_eq"></a>CSimpleArray::opérateur

Opérateur d'assignation.

```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
Tableau à copier.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur `CSimpleArray` à l’objet mis à jour.

### <a name="remarks"></a>Notes

Copie tous les `CSimpleArray` éléments de l’objet référencé par src dans *l’objet* de tableau actuel, remplaçant toutes les données existantes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]

## <a name="csimplearrayremove"></a><a name="remove"></a>CSimpleArray::Supprimer

Supprime un élément donné du tableau.

```
BOOL Remove(const T& t);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
L’élément à supprimer du tableau.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’élément est trouvé et supprimé, FALSE autrement.

### <a name="remarks"></a>Notes

Lorsqu’un élément est enlevé, les éléments restants du tableau sont renumbered pour remplir l’espace vide.

## <a name="csimplearrayremoveall"></a><a name="removeall"></a>CSimpleArray::RemoveAll

Supprime tous les éléments du tableau.

```
void RemoveAll();
```

### <a name="remarks"></a>Notes

Supprime tous les éléments actuellement stockés dans le tableau.

## <a name="csimplearrayremoveat"></a><a name="removeat"></a>CSimpleArray::RemoveAt

Supprime l’élément spécifié du tableau.

```
BOOL RemoveAtint nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index pointant vers l’élément à supprimer.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’élément a été supprimé, FALSE si l’index était invalide.

### <a name="remarks"></a>Notes

Lorsqu’un élément est enlevé, les éléments restants du tableau sont renumbered pour remplir l’espace vide.

## <a name="csimplearraysetatindex"></a><a name="setatindex"></a>CSimpleArray::SetAtIndex

Réglez l’élément spécifié dans le tableau.

```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index de l’élément à modifier.

*T*<br/>
Valeur à assigner à l’élément spécifié.

### <a name="return-value"></a>Valeur de retour

Rendements VRAI en cas de succès, FALSE si l’indice n’était pas valide.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
