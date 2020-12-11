---
description: 'En savoir plus sur : classe CAtlArray'
title: Classe CAtlArray
ms.date: 11/04/2016
f1_keywords:
- CAtlArray
- ATLCOLL/ATL::CAtlArray
- ATLCOLL/ATL::Add
- ATLCOLL/ATL::Append
- ATLCOLL/ATL::AssertValid
- ATLCOLL/ATL::Copy
- ATLCOLL/ATL::FreeExtra
- ATLCOLL/ATL::GetAt
- ATLCOLL/ATL::GetCount
- ATLCOLL/ATL::GetData
- ATLCOLL/ATL::InsertArrayAt
- ATLCOLL/ATL::InsertAt
- ATLCOLL/ATL::IsEmpty
- ATLCOLL/ATL::RemoveAll
- ATLCOLL/ATL::RemoveAt
- ATLCOLL/ATL::SetAt
- ATLCOLL/ATL::SetAtGrow
- ATLCOLL/ATL::SetCount
- ATLCOLL/ATL::INARGTYPE
- ATLCOLL/ATL::OUTARGTYPE
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
ms.openlocfilehash: 0ae3f5aef84cac64adba20ef438f5063abda098e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158424"
---
# <a name="catlarray-class"></a>Classe CAtlArray

Cette classe implémente un objet de tableau.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

### <a name="parameters"></a>Paramètres

*E*<br/>
Type de données à stocker dans le tableau.

*ETraits*<br/>
Code utilisé pour copier ou déplacer des éléments.

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|Fonction|Description|
|-|-|
|[Ajouter](#add)|Appelez cette méthode pour ajouter un élément à l’objet tableau.|
|[Append](#append)|Appelez cette méthode pour ajouter le contenu d’un tableau à la fin d’un autre.|
|[AssertValid](#assertvalid)|Appelez cette méthode pour confirmer que l’objet tableau est valide.|
|[CAtlArray](#catlarray)|Constructeur.|
|[~ CAtlArray](#dtor)|Destructeur.|
|[Copy](#copy)|Appelez cette méthode pour copier les éléments d’un tableau dans un autre.|
|[FreeExtra](#freeextra)|Appelez cette méthode pour supprimer tous les éléments vides du tableau.|
|[GetAt](#getat)|Appelez cette méthode pour récupérer un élément unique de l’objet de tableau.|
|[GetCount](#getcount)|Appelez cette méthode pour retourner le nombre d’éléments stockés dans le tableau.|
|[GetData](#getdata)|Appelez cette méthode pour retourner un pointeur vers le premier élément du tableau.|
|[InsertArrayAt](#insertarrayat)|Appelez cette méthode pour insérer un tableau dans un autre.|
|[InsertAt](#insertat)|Appelez cette méthode pour insérer un nouvel élément (ou plusieurs copies d’un élément) dans l’objet tableau.|
|[IsEmpty](#isempty)|Appelez cette méthode pour tester si le tableau est vide.|
|[RemoveAll](#removeall)|Appelez cette méthode pour supprimer tous les éléments de l’objet tableau.|
|[RemoveAt](#removeat)|Appelez cette méthode pour supprimer un ou plusieurs éléments du tableau.|
|[SetAt](#setat)|Appelez cette méthode pour définir la valeur d’un élément dans l’objet tableau.|
|[SetAtGrow](#setatgrow)|Appelez cette méthode pour définir la valeur d’un élément dans l’objet de tableau, en développant le tableau selon les besoins.|
|[SetCount](#setcount)|Appelez cette méthode pour définir la taille de l’objet tableau.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[ &#91;&#93;d’opérateur ](#operator_at)|Appelez cet opérateur pour retourner une référence à un élément dans le tableau.|

### <a name="typedefs"></a>Typedefs

|Typedef|Description|
|-|-|
|[INARGTYPE](#inargtype)|Type de données à utiliser pour ajouter des éléments au tableau.|
|[OUTARGTYPE](#outargtype)|Type de données à utiliser pour récupérer des éléments du tableau.|

## <a name="remarks"></a>Notes

`CAtlArray` fournit des méthodes pour créer et gérer un tableau d’éléments d’un type défini par l’utilisateur. Bien qu’elles soient similaires aux tableaux C standard, l' `CAtlArray` objet peut se réduire et croître de manière dynamique selon les besoins. L’index de tableau commence toujours à la position 0, et la limite supérieure peut être fixe ou autorisée à se développer au fur et à mesure que de nouveaux éléments sont ajoutés.

Pour les tableaux comportant un petit nombre d’éléments, la classe ATL [CSimpleArray](../../atl/reference/csimplearray-class.md) peut être utilisée.

`CAtlArray` est étroitement lié à la classe de MFC `CArray` et fonctionnera dans un projet MFC, mais sans prise en charge de la sérialisation.

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="catlarrayadd"></a><a name="add"></a> CAtlArray :: Add

Appelez cette méthode pour ajouter un élément à l’objet tableau.

```cpp
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>Paramètres

*appartient*<br/>
Élément à ajouter au tableau.

### <a name="return-value"></a>Valeur renvoyée

Retourne l’index de l’élément ajouté.

### <a name="remarks"></a>Notes

Le nouvel élément est ajouté à la fin du tableau. Si aucun élément n’est fourni, un élément vide est ajouté ; autrement dit, la taille du tableau est augmentée comme si un élément réel a été ajouté. Si l’opération échoue, [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) est appelé avec l’argument E_OUTOFMEMORY.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

## <a name="catlarrayappend"></a><a name="append"></a> CAtlArray :: Append

Appelez cette méthode pour ajouter le contenu d’un tableau à la fin d’un autre.

```cpp
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Paramètres

*aSrc*<br/>
Tableau à ajouter.

### <a name="return-value"></a>Valeur renvoyée

Retourne l’index du premier élément ajouté.

### <a name="remarks"></a>Notes

Les éléments du tableau fourni sont ajoutés à la fin du tableau existant. Si nécessaire, la mémoire sera allouée pour prendre en charge les nouveaux éléments.

Les tableaux doivent être du même type et il n’est pas possible d’ajouter un tableau à lui-même.

Dans les versions Debug, un ATLASSERT est déclenché si l' `CAtlArray` argument n’est pas un tableau valide ou si *aSrc* fait référence au même objet. Dans les versions release, les arguments non valides peuvent entraîner un comportement imprévisible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

## <a name="catlarrayassertvalid"></a><a name="assertvalid"></a> CAtlArray :: AssertValid

Appelez cette méthode pour confirmer que l’objet tableau est valide.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Notes

Si l’objet tableau n’est pas valide, ATLASSERT lèvera une assertion. Cette méthode est disponible uniquement si _DEBUG est défini.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

## <a name="catlarraycatlarray"></a><a name="catlarray"></a> CAtlArray :: CAtlArray

Constructeur.

```cpp
CAtlArray() throw();
```

### <a name="remarks"></a>Notes

Initialise l’objet tableau.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

## <a name="catlarraycatlarray"></a><a name="dtor"></a> CAtlArray :: ~ CAtlArray

Destructeur.

```cpp
~CAtlArray() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources utilisées par l’objet de tableau.

## <a name="catlarraycopy"></a><a name="copy"></a> CAtlArray :: Copy

Appelez cette méthode pour copier les éléments d’un tableau dans un autre.

```cpp
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Paramètres

*aSrc*<br/>
Source des éléments à copier dans un tableau.

### <a name="remarks"></a>Notes

Appelez cette méthode pour remplacer les éléments d’un tableau par les éléments d’un autre tableau. Si nécessaire, la mémoire sera allouée pour prendre en charge les nouveaux éléments. Il n’est pas possible de copier des éléments d’un tableau vers lui-même.

Si le contenu existant du tableau doit être conservé, utilisez [CAtlArray :: Append](#append) à la place.

Dans les versions Debug, un ATLASSERT est déclenché si l' `CAtlArray` objet existant n’est pas valide ou si *aSrc* fait référence au même objet. Dans les versions release, les arguments non valides peuvent entraîner un comportement imprévisible.

> [!NOTE]
> `CAtlArray::Copy` ne prend pas en charge les tableaux constitués d’éléments créés avec la classe [CAutoPtr](../../atl/reference/cautoptr-class.md) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

## <a name="catlarrayfreeextra"></a><a name="freeextra"></a> CAtlArray :: FreeExtra

Appelez cette méthode pour supprimer tous les éléments vides du tableau.

```cpp
void FreeExtra() throw();
```

### <a name="remarks"></a>Notes

Tous les éléments vides sont supprimés, mais la taille et la limite supérieure du tableau restent inchangées.

Dans les versions Debug, un ATLASSERT est déclenché si l’objet CAtlArray n’est pas valide ou si le tableau dépasse sa taille maximale.

## <a name="catlarraygetat"></a><a name="getat"></a> CAtlArray :: GetAt

Appelez cette méthode pour récupérer un élément unique de l’objet de tableau.

```cpp
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>Paramètres

*iElement*<br/>
Valeur d’index de l’élément de tableau à retourner.

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence à l’élément de tableau requis.

### <a name="remarks"></a>Notes

Dans les versions Debug, un ATLASSERT est déclenché si *IElement* dépasse le nombre d’éléments dans le tableau. Dans les versions release, un argument non valide peut entraîner un comportement imprévisible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

## <a name="catlarraygetcount"></a><a name="getcount"></a> CAtlArray :: GetCount

Appelez cette méthode pour retourner le nombre d’éléments stockés dans le tableau.

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre d’éléments stockés dans le tableau.

### <a name="remarks"></a>Notes

Comme le premier élément du tableau est à la position 0, la valeur retournée par `GetCount` est toujours égale à 1 par rapport à l’index le plus grand.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CAtlArray :: GetAt](#getat).

## <a name="catlarraygetdata"></a><a name="getdata"></a> CAtlArray :: GetData

Appelez cette méthode pour retourner un pointeur vers le premier élément du tableau.

```cpp
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers l’emplacement de mémoire qui stocke le premier élément dans le tableau. Si aucun élément n’est disponible, la valeur NULL est retournée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

## <a name="catlarrayinargtype"></a><a name="inargtype"></a> CAtlArray :: INARGTYPE

Type de données à utiliser pour ajouter des éléments au tableau.

```cpp
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catlarrayinsertarrayat"></a><a name="insertarrayat"></a> CAtlArray :: InsertArrayAt

Appelez cette méthode pour insérer un tableau dans un autre.

```cpp
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>Paramètres

*iStart*<br/>
Index auquel le tableau doit être inséré.

*paNew*<br/>
Tableau à insérer.

### <a name="remarks"></a>Notes

Les éléments du tableau *paNew* sont copiés dans l’objet tableau, en commençant à l’élément *iStart*. Les éléments de tableau existants sont déplacés pour éviter d’être remplacés.

Dans les versions Debug, un ATLASSERT est déclenché si l' `CAtlArray` objet n’est pas valide ou si le pointeur *paNew* a une valeur null ou n’est pas valide.

> [!NOTE]
> `CAtlArray::InsertArrayAt` ne prend pas en charge les tableaux constitués d’éléments créés avec la classe [CAutoPtr](../../atl/reference/cautoptr-class.md) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

## <a name="catlarrayinsertat"></a><a name="insertat"></a> CAtlArray :: InsertAt

Appelez cette méthode pour insérer un nouvel élément (ou plusieurs copies d’un élément) dans l’objet tableau.

```cpp
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>Paramètres

*iElement*<br/>
Index où l’élément ou les éléments doivent être insérés.

*appartient*<br/>
Valeur de l’élément ou des éléments à insérer.

*nCount*<br/>
Nombre d’éléments à ajouter.

### <a name="remarks"></a>Notes

Insère un ou plusieurs éléments dans le tableau, en commençant à l’index *IElement*. Les éléments existants sont déplacés pour éviter d’être remplacés.

Dans les versions Debug, un ATLASSERT est déclenché si l' `CAtlArray` objet n’est pas valide, si le nombre d’éléments à ajouter est égal à zéro ou si le nombre combiné d’éléments est trop grand pour le tableau à contenir. Dans les versions commerciales, le passage de paramètres non valides peut provoquer des résultats imprévisibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

## <a name="catlarrayisempty"></a><a name="isempty"></a> CAtlArray :: IsEmpty

Appelez cette méthode pour tester si le tableau est vide.

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si le tableau est vide ; sinon, false.

### <a name="remarks"></a>Notes

Le tableau est dit vide s’il ne contient aucun élément. Par conséquent, même si le tableau contient des éléments vides, il n’est pas vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

## <a name="catlarrayoperator-"></a><a name="operator_at"></a> CAtlArray :: Operator []

Appelez cet opérateur pour retourner une référence à un élément dans le tableau.

```cpp
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>Paramètres

*iElement*<br/>
Valeur d’index de l’élément de tableau à retourner.

### <a name="return-value"></a>Valeur renvoyée

Retourne une référence à l’élément de tableau requis.

### <a name="remarks"></a>Notes

Exécute une fonction similaire à [CAtlArray :: GetAt](#getat). Contrairement à la classe MFC [CArray](../../mfc/reference/carray-class.md), cet opérateur ne peut pas être utilisé comme substitut pour [CAtlArray :: setat](#setat).

Dans les versions Debug, un ATLASSERT est déclenché si *IElement* dépasse le nombre total d’éléments dans le tableau. Dans les versions commerciales, un paramètre non valide peut provoquer des résultats imprévisibles.

## <a name="catlarrayoutargtype"></a><a name="outargtype"></a> CAtlArray :: OUTARGTYPE

Type de données à utiliser pour récupérer des éléments du tableau.

```cpp
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

## <a name="catlarrayremoveall"></a><a name="removeall"></a> CAtlArray :: RemoveAll

Appelez cette méthode pour supprimer tous les éléments de l’objet tableau.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Notes

Supprime tous les éléments de l’objet tableau.

Cette méthode appelle [CAtlArray :: SetCount](#setcount) pour redimensionner le tableau et libère par la suite toute mémoire allouée.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CAtlArray :: IsEmpty](#isempty).

## <a name="catlarrayremoveat"></a><a name="removeat"></a> CAtlArray :: RemoveAt

Appelez cette méthode pour supprimer un ou plusieurs éléments du tableau.

```cpp
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>Paramètres

*iElement*<br/>
Index du premier élément à supprimer.

*nCount*<br/>
Nombre d'éléments à supprimer.

### <a name="remarks"></a>Notes

Supprime un ou plusieurs éléments du tableau. Les éléments restants sont décalés vers le dessous. La limite supérieure est décrémentée, mais la mémoire n’est pas libérée tant qu’un appel à [CAtlArray :: FreeExtra](#freeextra) n’est pas effectué.

Dans les versions Debug, un ATLASSERT est déclenché si l' `CAtlArray` objet n’est pas valide ou si le total combiné de *IElement* et de *nCount* dépasse le nombre total d’éléments dans le tableau. Dans les versions commerciales, les paramètres non valides peuvent entraîner des résultats imprévisibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

## <a name="catlarraysetat"></a><a name="setat"></a> CAtlArray :: SetAt

Appelez cette méthode pour définir la valeur d’un élément dans l’objet tableau.

```cpp
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Paramètres

*iElement*<br/>
Index pointant vers l’élément de tableau à définir.

*appartient*<br/>
Nouvelle valeur de l'élément spécifié.

### <a name="remarks"></a>Notes

Dans les versions Debug, un ATLASSERT est déclenché si *IElement* dépasse le nombre d’éléments dans le tableau. Dans les versions commerciales, un paramètre non valide peut entraîner des résultats imprévisibles.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CAtlArray :: GetAt](#getat).

## <a name="catlarraysetcount"></a><a name="setcount"></a> CAtlArray :: SetCount

Appelez cette méthode pour définir la taille de l’objet tableau.

```cpp
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>Paramètres

*nNewSize*<br/>
Taille requise du tableau.

*nGrowBy*<br/>
Valeur utilisée pour déterminer la taille de la mémoire tampon. La valeur-1 provoque l’utilisation d’une valeur calculée en interne.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si le tableau est correctement redimensionné ; sinon, false.

### <a name="remarks"></a>Notes

La taille du tableau peut être augmentée ou réduite. En cas d’augmentation, des éléments vides supplémentaires sont ajoutés au tableau. En cas de diminution, les éléments ayant les plus grands index seront supprimés et la mémoire libérée.

Utilisez cette méthode pour définir la taille du tableau avant de l’utiliser. Si `SetCount` n’est pas utilisé, le processus d’ajout d’éléments (et l’allocation de mémoire suivante effectuée) réduira les performances et la mémoire de fragments.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CAtlArray :: GetData](#getdata).

## <a name="catlarraysetatgrow"></a><a name="setatgrow"></a> CAtlArray :: SetAtGrow

Appelez cette méthode pour définir la valeur d’un élément dans l’objet de tableau, en développant le tableau selon les besoins.

```cpp
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Paramètres

*iElement*<br/>
Index pointant vers l’élément de tableau à définir.

*appartient*<br/>
Nouvelle valeur de l'élément spécifié.

### <a name="remarks"></a>Notes

Remplace la valeur de l’élément vers lequel pointe l’index. Si *IElement* est plus grand que la taille actuelle du tableau, le tableau est automatiquement augmenté à l’aide d’un appel à [CAtlArray :: SetCount](#setcount). Dans les versions Debug, un ATLASSERT est déclenché si l' `CAtlArray` objet n’est pas valide. Dans les versions commerciales, les paramètres non valides peuvent entraîner des résultats imprévisibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MMXSwarm](../../overview/visual-cpp-samples.md)<br/>
[DynamicConsumer, exemple](../../overview/visual-cpp-samples.md)<br/>
[Exemple UpdatePV](../../overview/visual-cpp-samples.md)<br/>
[Exemple de texte défilant](../../overview/visual-cpp-samples.md)<br/>
[CArray (classe)](../../mfc/reference/carray-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
