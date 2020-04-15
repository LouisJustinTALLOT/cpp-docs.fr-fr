---
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
ms.openlocfilehash: 85168af654d3d63e06559486b464938b7fd90ad3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321570"
---
# <a name="catlarray-class"></a>Classe CAtlArray

Cette classe met en œuvre un objet de tableau.

## <a name="syntax"></a>Syntaxe

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

#### <a name="parameters"></a>Paramètres

*E*<br/>
Type de données à stocker dans le tableau.

*ETraits (ETraits)*<br/>
Le code utilisé pour copier ou déplacer des éléments.

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[Ajouter](#add)|Appelez cette méthode pour ajouter un élément à l’objet de tableau.|
|[Append](#append)|Appelez cette méthode pour ajouter le contenu d’un tableau à la fin d’un autre.|
|[AssertValid (en)](#assertvalid)|Appelez cette méthode pour confirmer que l’objet de tableau est valide.|
|[CAtlArray](#catlarray)|Constructeur.|
|[CAtlArray](#dtor)|Destructeur.|
|[Copier](#copy)|Appelez cette méthode pour copier les éléments d’un tableau à un autre.|
|[FreeExtra (FreeExtra)](#freeextra)|Appelez cette méthode pour supprimer tous les éléments vides du tableau.|
|[GetAt](#getat)|Appelez cette méthode pour récupérer un seul élément de l’objet de tableau.|
|[GetCount](#getcount)|Appelez cette méthode pour retourner le nombre d’éléments stockés dans le tableau.|
|[GetData](#getdata)|Appelez cette méthode pour retourner un pointeur au premier élément du tableau.|
|[InsertArrayAt](#insertarrayat)|Appelez cette méthode pour insérer un tableau dans un autre.|
|[InsertAt](#insertat)|Appelez cette méthode pour insérer un nouvel élément (ou plusieurs copies d’un élément) dans l’objet de tableau.|
|[IsEmpty](#isempty)|Appelez cette méthode pour tester si le tableau est vide.|
|[SupprimerTous](#removeall)|Appelez cette méthode pour supprimer tous les éléments de l’objet de tableau.|
|[RemoveAt](#removeat)|Appelez cette méthode pour supprimer un ou plusieurs éléments du tableau.|
|[SetAt](#setat)|Appelez cette méthode pour définir la valeur d’un élément dans l’objet de tableau.|
|[SetAtGrow SetAtGrow](#setatgrow)|Appelez cette méthode pour définir la valeur d’un élément dans l’objet de tableau, en élargissant le tableau au besoin.|
|[SetCount (en)](#setcount)|Appelez cette méthode pour définir la taille de l’objet de tableau.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[ &#91;&#93;de l’opérateur](#operator_at)|Appelez cet opérateur pour retourner une référence à un élément dans le tableau.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[INARGTYPE](#inargtype)|Le type de données à utiliser pour ajouter des éléments au tableau.|
|[OUTARGTYPE](#outargtype)|Le type de données à utiliser pour récupérer des éléments de la gamme.|

## <a name="remarks"></a>Notes

`CAtlArray`fournit des méthodes pour créer et gérer un éventail d’éléments d’un type défini par l’utilisateur. Bien que semblable aux tableaux `CAtlArray` C standard, l’objet peut se rétrécir dynamiquement et se développer au besoin. L’indice de tableau commence toujours à la position 0, et la limite supérieure peut être fixée, ou autorisé à se développer à mesure que de nouveaux éléments sont ajoutés.

Pour les tableaux avec un petit nombre d’éléments, la classe ATL [CSimpleArray](../../atl/reference/csimplearray-class.md) peut être utilisée.

`CAtlArray`est étroitement lié à `CArray` la classe de MFC et travaillera dans le cadre d’un projet MFC, mais sans soutien de sérialisation.

Pour plus d’informations, voir [cours de collecte ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlcoll.h

## <a name="catlarrayadd"></a><a name="add"></a>CAtlArray::Ajouter

Appelez cette méthode pour ajouter un élément à l’objet de tableau.

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>Paramètres

*Élément*<br/>
L’élément à ajouter au tableau.

### <a name="return-value"></a>Valeur de retour

Retourne l’index de l’élément ajouté.

### <a name="remarks"></a>Notes

Le nouvel élément est ajouté à la fin du tableau. Si aucun élément n’est fourni, un élément vide est ajouté; c’est-à-dire que le tableau est augmenté en taille comme si un élément réel a été ajouté. Si l’opération échoue, [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) est appelé avec l’argument E_OUTOFMEMORY.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

## <a name="catlarrayappend"></a><a name="append"></a>CAtlArray::Append

Appelez cette méthode pour ajouter le contenu d’un tableau à la fin d’un autre.

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Paramètres

*Asrc*<br/>
Le tableau à appendice.

### <a name="return-value"></a>Valeur de retour

Retourne l’index du premier élément joint.

### <a name="remarks"></a>Notes

Les éléments du tableau fourni sont ajoutés à la fin du tableau existant. Si nécessaire, la mémoire sera allouée pour accueillir les nouveaux éléments.

Les tableaux doivent être du même type, et il n’est pas possible d’ajouter un tableau à lui-même.

Dans les constructions de débog, un `CAtlArray` ATLASSERT sera soulevé si l’argument n’est pas un tableau valide ou si *aSrc* se réfère au même objet. Dans les versions, les arguments invalides peuvent conduire à un comportement imprévisible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

## <a name="catlarrayassertvalid"></a><a name="assertvalid"></a>CAtlArray::AssertValid

Appelez cette méthode pour confirmer que l’objet de tableau est valide.

```
void AssertValid() const;
```

### <a name="remarks"></a>Notes

Si l’objet de tableau n’est pas valide, ATLASSERT lancera une affirmation. Cette méthode n’est disponible que si _DEBUG est définie.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

## <a name="catlarraycatlarray"></a><a name="catlarray"></a>CAtlArray::CAtlArray

Constructeur.

```
CAtlArray() throw();
```

### <a name="remarks"></a>Notes

Initialise l’objet de tableau.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

## <a name="catlarraycatlarray"></a><a name="dtor"></a>CAtlArray: :CAtlArray

Destructeur.

```
~CAtlArray() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources utilisées par l’objet de tableau.

## <a name="catlarraycopy"></a><a name="copy"></a>CAtlArray::Copier

Appelez cette méthode pour copier les éléments d’un tableau à un autre.

```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Paramètres

*Asrc*<br/>
La source des éléments à copier à un tableau.

### <a name="remarks"></a>Notes

Appelez cette méthode pour remplacer les éléments d’un tableau avec les éléments d’un autre tableau. Si nécessaire, la mémoire sera allouée pour accueillir les nouveaux éléments. Il n’est pas possible de copier des éléments d’un tableau à lui-même.

Si le contenu existant du tableau doit être conservé, utilisez [CAtlArray::Append](#append) à la place.

Dans les constructions de débog, un ATLASSERT sera soulevé si l’objet existant `CAtlArray` n’est pas valide, ou si *aSrc* se réfère au même objet. Dans les versions, les arguments invalides peuvent conduire à un comportement imprévisible.

> [!NOTE]
> `CAtlArray::Copy`ne prend pas en charge les tableaux composés d’éléments créés avec la classe [CAutoPtr.](../../atl/reference/cautoptr-class.md)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

## <a name="catlarrayfreeextra"></a><a name="freeextra"></a>CAtlArray::FreeExtra

Appelez cette méthode pour supprimer tous les éléments vides du tableau.

```
void FreeExtra() throw();
```

### <a name="remarks"></a>Notes

Tous les éléments vides sont enlevés, mais la taille et la limite supérieure du tableau restent inchangées.

Dans les constructions de débopathie, un ATLASSERT sera soulevé si l’objet CAtlArray n’est pas valide, ou si le tableau dépasserait sa taille maximale.

## <a name="catlarraygetat"></a><a name="getat"></a>CAtlArray::GetAt

Appelez cette méthode pour récupérer un seul élément de l’objet de tableau.

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>Paramètres

*iElement (en)*<br/>
La valeur indicative de l’élément de tableau à retourner.

### <a name="return-value"></a>Valeur de retour

Renvoie une référence à l’élément de tableau requis.

### <a name="remarks"></a>Notes

Dans les constructions de débog, un ATLASSERT sera soulevé si *iElement* dépasse le nombre d’éléments dans le tableau. Dans la version s’accumule, un argument invalide peut conduire à un comportement imprévisible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

## <a name="catlarraygetcount"></a><a name="getcount"></a>CAtlArray::GetCount

Appelez cette méthode pour retourner le nombre d’éléments stockés dans le tableau.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’éléments stockés dans le tableau.

### <a name="remarks"></a>Notes

Comme le premier élément de la gamme est à `GetCount` la position 0, la valeur retournée par est toujours 1 plus grand que le plus grand indice.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlArray::GetAt](#getat).

## <a name="catlarraygetdata"></a><a name="getdata"></a>CAtlArray::GetData

Appelez cette méthode pour retourner un pointeur au premier élément du tableau.

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur à l’emplacement de mémoire en stockant le premier élément dans le tableau. Si aucun élément n’est disponible, NULL est retourné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

## <a name="catlarrayinargtype"></a><a name="inargtype"></a>CAtlArray::INARGTYPE

Le type de données à utiliser pour ajouter des éléments au tableau.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catlarrayinsertarrayat"></a><a name="insertarrayat"></a>CAtlArray::InsertArrayAt

Appelez cette méthode pour insérer un tableau dans un autre.

```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>Paramètres

*iStart (en)*<br/>
L’index auquel le tableau doit être inséré.

*paNouveau*<br/>
Le tableau à insérer.

### <a name="remarks"></a>Notes

Les éléments de la gamme *paNew* sont copiés dans l’objet de tableau, à partir de l’élément *iStart*. Les éléments de tableau existants sont déplacés pour éviter d’être écrasés.

Dans les constructions de débog, un `CAtlArray` ATLASSERT sera soulevé si l’objet n’est pas valide, ou si le pointeur *paNew* est NULL ou invalide.

> [!NOTE]
> `CAtlArray::InsertArrayAt`ne prend pas en charge les tableaux composés d’éléments créés avec la classe [CAutoPtr.](../../atl/reference/cautoptr-class.md)

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

## <a name="catlarrayinsertat"></a><a name="insertat"></a>CAtlArray::InsertAt

Appelez cette méthode pour insérer un nouvel élément (ou plusieurs copies d’un élément) dans l’objet de tableau.

```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>Paramètres

*iElement (en)*<br/>
L’index où l’élément ou les éléments doivent être insérés.

*Élément*<br/>
La valeur de l’élément ou des éléments à insérer.

*nCompte*<br/>
Le nombre d’éléments à ajouter.

### <a name="remarks"></a>Notes

Insère un ou plusieurs éléments dans le tableau, à partir de index *iElement*. Les éléments existants sont déplacés pour éviter d’être écrasés.

Dans les constructions de débog, un `CAtlArray` ATLASSERT sera soulevé si l’objet est invalide, le nombre d’éléments à ajouter est nul, ou le nombre combiné d’éléments est trop grand pour que le tableau puisse être contenu. Dans les constructions de détail, l’adoption de paramètres invalides peut entraîner des résultats imprévisibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

## <a name="catlarrayisempty"></a><a name="isempty"></a>CAtlArray::IsEmpty

Appelez cette méthode pour tester si le tableau est vide.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valeur de retour

Revient vrai si le tableau est vide, faux autrement.

### <a name="remarks"></a>Notes

Le tableau est dit être vide s’il ne contient pas d’éléments. Par conséquent, même si le tableau contient des éléments vides, il n’est pas vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

## <a name="catlarrayoperator-"></a><a name="operator_at"></a>CAtlArray::opérateur []

Appelez cet opérateur pour retourner une référence à un élément dans le tableau.

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>Paramètres

*iElement (en)*<br/>
La valeur indicative de l’élément de tableau à retourner.

### <a name="return-value"></a>Valeur de retour

Renvoie une référence à l’élément de tableau requis.

### <a name="remarks"></a>Notes

Effectue une fonction similaire à [CAtlArray::GetAt](#getat). Contrairement à la classe MFC [CArray](../../mfc/reference/carray-class.md), cet opérateur ne peut pas être utilisé comme un substitut pour [CAtlArray::SetAt](#setat).

Dans les constructions de débog, un ATLASSERT sera soulevé si *iElement* dépasse le nombre total d’éléments dans le tableau. Dans les constructions de détail, un paramètre invalide peut entraîner des résultats imprévisibles.

## <a name="catlarrayoutargtype"></a><a name="outargtype"></a>CAtlArray::OUTARGTYPE

Le type de données à utiliser pour récupérer des éléments de la gamme.

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

## <a name="catlarrayremoveall"></a><a name="removeall"></a>CAtlArray::RemoveAll

Appelez cette méthode pour supprimer tous les éléments de l’objet de tableau.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Notes

Supprime tous les éléments de l’objet de tableau.

Cette méthode appelle [CAtlArray::SetCount](#setcount) pour resize le tableau et libère par la suite toute mémoire allouée.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlArray::IsEmpty](#isempty).

## <a name="catlarrayremoveat"></a><a name="removeat"></a>CAtlArray::RemoveAt

Appelez cette méthode pour supprimer un ou plusieurs éléments du tableau.

```
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>Paramètres

*iElement (en)*<br/>
L’index du premier élément à supprimer.

*nCompte*<br/>
Nombre d'éléments à supprimer.

### <a name="remarks"></a>Notes

Supprime un ou plusieurs éléments du tableau. Tous les éléments restants sont déplacés vers le bas. La limite supérieure est décrémentée, mais la mémoire n’est pas libérée jusqu’à ce qu’un appel à [CAtlArray::FreeExtra](#freeextra) est fait.

Dans les constructions de débog, un `CAtlArray` ATLASSERT sera soulevé si l’objet n’est pas valide, ou si le total combiné *d’iElement* et *nCount* dépasse le nombre total d’éléments dans le tableau. Dans les constructions de détail, les paramètres non valides peuvent entraîner des résultats imprévisibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

## <a name="catlarraysetat"></a><a name="setat"></a>CAtlArray::SetAt

Appelez cette méthode pour définir la valeur d’un élément dans l’objet de tableau.

```
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Paramètres

*iElement (en)*<br/>
L’index pointant vers l’élément de tableau à définir.

*Élément*<br/>
Nouvelle valeur de l'élément spécifié.

### <a name="remarks"></a>Notes

Dans les constructions de débog, un ATLASSERT sera soulevé si *iElement* dépasse le nombre d’éléments dans le tableau. Dans les constructions de détail, un paramètre invalide peut entraîner des résultats imprévisibles.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlArray::GetAt](#getat).

## <a name="catlarraysetcount"></a><a name="setcount"></a>CAtlArray::SetCount

Appelez cette méthode pour définir la taille de l’objet de tableau.

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>Paramètres

*nNewSize (en)*<br/>
La taille requise du tableau.

*nGrowBy (en)*<br/>
Une valeur utilisée pour déterminer la taille de la mémoire tampon. Une valeur de -1 entraîne l’utilisation d’une valeur calculée internement.

### <a name="return-value"></a>Valeur de retour

Retourne vrai si le tableau est resized avec succès, faux autrement.

### <a name="remarks"></a>Notes

Le tableau peut être augmenté ou diminué en taille. Si elles sont augmentées, des éléments vides supplémentaires sont ajoutés au tableau. En cas de diminution, les éléments avec les plus grands indices seront supprimés et la mémoire libérée.

Utilisez cette méthode pour définir la taille du tableau avant de l’utiliser. Si `SetCount` elle n’est pas utilisée, le processus d’ajout d’éléments — et l’allocation de mémoire subséquente effectuée — réduira les performances et la mémoire des fragments.

### <a name="example"></a>Exemple

Voir l’exemple pour [CAtlArray::GetData](#getdata).

## <a name="catlarraysetatgrow"></a><a name="setatgrow"></a>CAtlArray::SetAtGrow

Appelez cette méthode pour définir la valeur d’un élément dans l’objet de tableau, en élargissant le tableau au besoin.

```
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Paramètres

*iElement (en)*<br/>
L’index pointant vers l’élément de tableau à définir.

*Élément*<br/>
Nouvelle valeur de l'élément spécifié.

### <a name="remarks"></a>Notes

Remplace la valeur de l’élément indiqué par l’indice. Si *iElement* est plus grand que la taille actuelle du tableau, le tableau est automatiquement augmenté à l’aide d’un appel à [CAtlArray::SetCount](#setcount). Dans les constructions de débogé, un `CAtlArray` ATLASSERT sera soulevé si l’objet n’est pas valide. Dans les constructions de détail, les paramètres non valides peuvent entraîner des résultats imprévisibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>Voir aussi

[Échantillon MMXSwarm](../../overview/visual-cpp-samples.md)<br/>
[Échantillon DynamicConsumer](../../overview/visual-cpp-samples.md)<br/>
[Exemple UpdatePV](../../overview/visual-cpp-samples.md)<br/>
[Échantillon de marquee](../../overview/visual-cpp-samples.md)<br/>
[Classe CArray](../../mfc/reference/carray-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
