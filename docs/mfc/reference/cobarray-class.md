---
title: CObArray, classe
ms.date: 11/04/2016
f1_keywords:
- CObArray
- AFXCOLL/CObArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
ms.openlocfilehash: 7b923fd9231d3652d8d2f1750a8024d15287811e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360446"
---
# <a name="cobarray-class"></a>CObArray, classe

Prend en charge des tableaux de pointeurs `CObject` .

## <a name="syntax"></a>Syntaxe

```
class CObArray : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CObArray::CObArray](#cobarray)|Construit un tableau `CObject` vide pour les pointeurs.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CObArray::Ajouter](#add)|Ajoute un élément à la fin du tableau ; étend le tableau si nécessaire.|
|[CObArray::Append](#append)|Ajoute un autre tableau au tableau ; étend le tableau si nécessaire.|
|[CObArray::Copier](#copy)|Copie un autre tableau dans le tableau ; étend le tableau si nécessaire.|
|[CObArray::ElementAt](#elementat)|Retourne une référence temporaire au pointeur d'élément dans le tableau.|
|[CObArray::FreeExtra](#freeextra)|Libère toute la mémoire inutilisée au-dessus de la limite supérieure actuelle.|
|[CObArray::GetAt](#getat)|Retourne la valeur à un index donné.|
|[CObArray::GetCount](#getcount)|Obtient le nombre d'éléments dans ce tableau.|
|[CObArray::GetData](#getdata)|Autorise l'accès aux éléments du tableau. Sa valeur peut être NULL.|
|[CObArray::GetSize](#getsize)|Obtient le nombre d'éléments dans ce tableau.|
|[CObArray::GetUpperBound](#getupperbound)|Retourne le plus grand index valide.|
|[CObArray::InsertAt](#insertat)|Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.|
|[CObArray::IsEmpty](#isempty)|Détermine si le tableau est vide.|
|[CObArray::RemoveAll](#removeall)|Supprime tous les éléments de ce tableau.|
|[CObArray::RemoveAt](#removeat)|Supprime un élément à un index spécifique.|
|[CObArray::SetAt](#setat)|Définit la valeur d'un index donné. Le tableau n'est pas autorisé à s'étendre.|
|[CObArray::SetAtGrow](#setatgrow)|Définit la valeur d'un index donné. Le tableau est étendu si nécessaire.|
|[CObArray::SetSize](#setsize)|Définit le nombre d'éléments que ce tableau doit contenir.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CObArray::opérateur \[\]](#operator_at)|Définit ou obtient l'élément au niveau de l'index spécifié.|

## <a name="remarks"></a>Notes

Ces tableaux d’objets sont semblables aux tableaux C, mais ils peuvent dynamiquement rétrécir et se développer au besoin.

Les index de tableau commencent toujours à la position 0. Vous pouvez décider s’il faut fixer la limite supérieure ou permettre au tableau de se dilater lorsque vous ajoutez des éléments au-delà de la limite actuelle. La mémoire est attribuée de façon contigu à la limite supérieure, même si certains éléments sont nuls.

Sous Win32, la `CObArray` taille d’un objet est limitée uniquement à la mémoire disponible.

Comme avec un tableau C, `CObArray` le temps d’accès pour un élément indexé est constant et indépendant de la taille du tableau.

`CObArray`intègre la macro IMPLEMENT_SERIAL pour soutenir la sérialisation et le dumping de ses éléments. Si un `CObject` tableau de pointeurs est stocké à une archive, soit `Serialize` avec l’opérateur d’insertion surchargé ou avec la fonction membre, chaque `CObject` élément est, à son tour, sérialisé avec son index de tableau.

Si vous avez besoin `CObject` d’un dépotoir d’éléments `CDumpContext` individuels dans un tableau, vous devez définir la profondeur de l’objet à 1 ou plus.

Lorsqu’un `CObArray` objet est supprimé, ou lorsque ses `CObject` éléments sont supprimés, seuls les pointeurs sont supprimés, et non les objets qu’ils renvoient.

> [!NOTE]
> Avant d'utiliser un tableau, utilisez `SetSize` pour définir sa taille et lui allouer la mémoire nécessaire. Si vous n'utilisez pas `SetSize`, l'ajout d'éléments à votre tableau risque d'entraîner de fréquentes opérations de réallocation et de copie de ce dernier. Les opérations fréquentes de réallocation et de copie sont inefficaces et peuvent fragmenter la mémoire.

La dérivation de classe de tableau est semblable à la dérivation de liste. Pour plus de détails sur la dérivation d’une classe de liste à usage spécial, voir l’article [Collections](../../mfc/collections.md).

> [!NOTE]
> Vous devez utiliser la macro IMPLEMENT_SERIAL dans la mise en œuvre de votre classe dérivée si vous avez l’intention de sérialiser le tableau.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>Spécifications

**En-tête:** afxcoll.h

## <a name="cobarrayadd"></a><a name="add"></a>CObArray::Ajouter

Ajoute un nouvel élément à la fin d’un tableau, augmentant le tableau de 1.

```
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>Paramètres

*nouvel Element*<br/>
Le `CObject` pointeur à ajouter à ce tableau.

### <a name="return-value"></a>Valeur de retour

L’index de l’élément ajouté.

### <a name="remarks"></a>Notes

Si [SetSize](#setsize) a été utilisé avec une valeur *nGrowBy* supérieure à 1, alors la mémoire supplémentaire peut être allouée. Cependant, la limite supérieure n’augmentera que de 1.

Le tableau suivant montre d’autres `CObArray::Add`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR Ajouter( BYTE** `newElement` **);**<br /><br /> **lancer( CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR Ajouter( DWORD** `newElement` **);**<br /><br /> **lancer( CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR Ajouter( vide** <strong>\*</strong> `newElement` **);**<br /><br /> **lancer( CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR Add( LPCTSTR** `newElement` **); lancer (CMemoryException);\* **<br /><br /> **INT_PTR Add (const CString** `newElement` **&);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR Add( UINT** `newElement` **);**<br /><br /> **lancer( CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR Ajouter( WORD** `newElement` **);**<br /><br /> **lancer( CMemoryException\* );**|

### <a name="example"></a>Exemple

  Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

Les résultats de ce programme sont les suivants :

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

## <a name="cobarrayappend"></a><a name="append"></a>CObArray::Append

Appelez cette fonction de membre pour ajouter le contenu d’un autre tableau à la fin du tableau donné.

```
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
Source des éléments à annexer au tableau.

### <a name="return-value"></a>Valeur de retour

L’index du premier élément joint.

### <a name="remarks"></a>Notes

Les tableaux doivent être du même type.

Si nécessaire, `Append` peut allouer une mémoire supplémentaire pour accueillir les éléments annexés au tableau.

Le tableau suivant montre d’autres `CObArray::Append`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR Annexe (const CByteArray&** *src);* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR Append (const CDWordArray&** *src);* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR Annexe (const CPtrArray&** *src);* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR Annexe (const CStringArray&** *src);* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR Annexe (const CUIntArray&** *src);* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR Annexe (const CWordArray&** *src);* **);**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

## <a name="cobarraycopy"></a><a name="copy"></a>CObArray::Copier

Appelez cette fonction de membre pour remplacer les éléments du tableau donné avec les éléments d’un autre tableau du même type.

```
void Copy(const CObArray& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
Source des éléments à copier au tableau.

### <a name="remarks"></a>Notes

`Copy`ne libère pas la mémoire; toutefois, si `Copy` nécessaire, peut allouer une mémoire supplémentaire pour tenir compte des éléments copiés sur le tableau.

Le tableau suivant montre d’autres `CObArray::Copy`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**avenu Copie (const CByteArray&** *src);* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void Copy (const CDWordArray&** *src);* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**avenu copie (const CPtrArray&** *src);* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**avenu Copie (const CStringArray&** *src);* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**avenu Copie (const CUIntArray&** *src);* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void Copy( const CWordArray&** *src);* **);**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

## <a name="cobarraycobarray"></a><a name="cobarray"></a>CObArray::CObArray

Construit un `CObject` tableau de pointeur vide.

```
CObArray();
```

### <a name="remarks"></a>Notes

Le tableau pousse un élément à la fois.

Le tableau suivant montre d’autres `CObArray::CObArray`constructeurs qui sont similaires à .

|Classe|Constructeur|
|-----------|-----------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray() ();**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray();**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CStringArray();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntArray ();**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray() ();**|

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

## <a name="cobarrayelementat"></a><a name="elementat"></a>CObArray::ElementAt

Retourne une référence temporaire au pointeur d'élément dans le tableau.

```
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un indice d’intégration supérieur ou égal à 0 et inférieur `GetUpperBound`ou égal à la valeur retournée par .

### <a name="return-value"></a>Valeur de retour

Une référence `CObject` à un pointeur.

### <a name="remarks"></a>Notes

Il est utilisé pour implémenter l’opérateur d’affectation côté gauche pour les tableaux. Notez qu’il s’agit d’une fonction avancée qui ne doit être utilisée que pour implémenter des opérateurs de tableaux spéciaux.

Le tableau suivant montre d’autres `CObArray::ElementAt`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE& ElementAt** `nIndex` **(INT_PTR);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD& ElementAt** `nIndex` **(INT_PTR);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**vide\*& ElementAt (INT_PTR);** `nIndex` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString& ElementAt** `nIndex` **(INT_PTR);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT& ElementAt** `nIndex` **(INT_PTR);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD& ElementAt** `nIndex` **(INT_PTR);**|

### <a name="example"></a>Exemple

  Voir l’exemple pour [CObArray:GetSize](#getsize).

## <a name="cobarrayfreeextra"></a><a name="freeextra"></a>CObArray::FreeExtra

Libère toute mémoire supplémentaire qui a été allouée pendant que le tableau a été cultivé.

```
void FreeExtra();
```

### <a name="remarks"></a>Notes

Cette fonction n’a aucun effet sur la taille ou la limite supérieure du tableau.

Le tableau suivant montre d’autres `CObArray::FreeExtra`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void FreeExtra();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void FreeExtra();**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void FreeExtra();**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void FreeExtra();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void FreeExtra();**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void FreeExtra();**|

### <a name="example"></a>Exemple

  Voir l’exemple pour [CObArray::GetData](#getdata).

## <a name="cobarraygetat"></a><a name="getat"></a>CObArray::GetAt

Retourne l’élément de tableau à l’index spécifié.

```
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un indice d’intégration supérieur ou égal à 0 et inférieur `GetUpperBound`ou égal à la valeur retournée par .

### <a name="return-value"></a>Valeur de retour

L’élément `CObject` pointeur actuellement à cet indice.

### <a name="remarks"></a>Notes

> [!NOTE]
> L’adoption d’une valeur négative ou `GetUpperBound` d’une valeur supérieure à la valeur retournée entraînera un échec de l’affirmation.

Le tableau suivant montre d’autres `CObArray::GetAt`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE GetAt ( INT_PTR** `nIndex` **) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt ( INT_PTR** `nIndex` **) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**vide\* GetAt ( INT_PTR** `nIndex` **) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString GetAt ( INT_PTR** `nIndex` **) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT GetAt ( INT_PTR** `nIndex` **) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD GetAt ( INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

## <a name="cobarraygetcount"></a><a name="getcount"></a>CObArray::GetCount

Retourne le nombre d’éléments de tableau.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans le tableau.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre d’éléments dans le tableau. Étant donné que les indices sont basés à zéro, la taille est 1 supérieure à l’indice le plus important.

Le tableau suivant montre d’autres `CObArray::GetCount`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetCount) ) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetCount) ) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetCount) ) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetCount) ) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetCount) ) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetCount) ) const;**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

## <a name="cobarraygetdata"></a><a name="getdata"></a>CObArray::GetData

Utilisez cette fonction de membre pour accéder directement aux éléments du tableau.

```
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à `CObject` la gamme de pointeurs.

### <a name="remarks"></a>Notes

Si aucun élément `GetData` n’est disponible, renvoie une valeur nulle.

Bien que l’accès direct aux éléments d’un tableau `GetData`peut vous aider à travailler plus rapidement, faites preuve de prudence lorsque vous appelez; toutes les erreurs que vous faites affectent directement les éléments de votre tableau.

Le tableau suivant montre d’autres `CObArray::GetData`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**const BYTE\* GetData( ) const; BYTE\* GetData() () (en)**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**const DWORD\* GetData( ) const;DWORD\* GetData() );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**const\* \* vide GetData( )\* \* const;void GetData( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**const CString\* GetData( ) const; CString\* GetData() );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**const UINT\* GetData( ) const; UINT\* GetData() () (en)**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**const\* WORD GetData( ) const; WORD\* GetData() );**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

## <a name="cobarraygetsize"></a><a name="getsize"></a>CObArray::GetSize

Retourne la taille du tableau.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Notes

Étant donné que les indices sont basés à zéro, la taille est 1 supérieure à l’indice le plus important.

Le tableau suivant montre d’autres `CObArray::GetSize`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetSize( ) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetSize( ) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetSize( ) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetSize( ) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetSize( ) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

## <a name="cobarraygetupperbound"></a><a name="getupperbound"></a>CObArray::GetUpperBound

Retourne la limite supérieure actuelle de ce tableau.

```
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>Valeur de retour

L’indice de la limite supérieure (zéro à base).

### <a name="remarks"></a>Notes

Étant donné que les indices de tableau sont basés à `GetSize`zéro, cette fonction retourne une valeur 1 de moins que .

La `GetUpperBound( )` condition de -1 indique que le tableau ne contient aucun élément.

Le tableau suivant montre d’autres `CObArray::GetUpperBound`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetUpperBound( ) const;**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

## <a name="cobarrayinsertat"></a><a name="insertat"></a>CObArray::InsertAt

Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.

```
void InsertAt(
    INT_PTR nIndex,
    CObject* newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CObArray* pNewArray);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un indice d’intégration qui peut `GetUpperBound`être supérieur à la valeur retournée par .

*nouvel Element*<br/>
Le `CObject` pointeur à placer dans ce tableau. Un *nouvel Element* de la valeur NULL est autorisé.

*nCompte*<br/>
Le nombre de fois cet élément doit être inséré (par défaut à 1).

*nStartIndex*<br/>
Un indice d’intégration qui peut `GetUpperBound`être supérieur à la valeur retournée par .

*pNewArray (en)*<br/>
Un autre tableau qui contient des éléments à ajouter à ce tableau.

### <a name="remarks"></a>Notes

La première `InsertAt` version des inserts d’un élément (ou de multiples copies d’un élément) à un index spécifié dans un tableau. Dans le processus, il déplace vers le haut (en incrémentant l’indice) l’élément existant à cet indice, et il déplace vers le haut tous les éléments au-dessus.

La deuxième version insère `CObArray` tous les éléments d’une autre collection, à partir de la position *nStartIndex.*

La `SetAt` fonction, en revanche, remplace un élément de tableau spécifié et ne déplace aucun élément.

Le tableau suivant montre d’autres `CObArray::InsertAt`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**insertAt ( INT_PTR** `nIndex` **, BYTE** `newElement` **, int** `nCount` **1 );**<br /><br /> **lancer( CMemoryException\* );**<br /><br /> **void InsertAt ( INT_PTR** `nStartIndex` **, CByteArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **lancer( CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**insertAt ( INT_PTR** `nIndex` **, DWORD** `newElement` **, int** `nCount` **1 );**<br /><br /> **lancer( CMemoryException\* );**<br /><br /> **void InsertAt ( INT_PTR** `nStartIndex` **, CDWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **lancer( CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**insertAt (INT_PTR** `nIndex` **, vide** <strong>\*</strong> `newElement` **, int** `nCount` **1 );**<br /><br /> **lancer( CMemoryException\* );**<br /><br /> **insertAt ( INT_PTR** `nStartIndex` **, CPtrArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **lancer( CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**insertAt ( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **, int** `nCount` **1 );**<br /><br /> **lancer( CMemoryException\* );**<br /><br /> **void InsertAt ( INT_PTR** `nStartIndex` **, CStringArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **lancer( CMemoryException\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**insertAt ( INT_PTR** `nIndex` **, UINT** `newElement` **, int** `nCount` **1 );**<br /><br /> **lancer( CMemoryException\* );**<br /><br /> **insertAt ( INT_PTR** `nStartIndex` **, CUIntArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **lancer( CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**insertAt ( INT_PTR** `nIndex` **, WORD** `newElement` **, int** `nCount` **1 );**<br /><br /> **lancer( CMemoryException\* );**<br /><br /> **void InsertAt ( INT_PTR** `nStartIndex` **, CWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **lancer( CMemoryException\* );**|

### <a name="example"></a>Exemple

  Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

Les résultats de ce programme sont les suivants :

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

## <a name="cobarrayisempty"></a><a name="isempty"></a>CObArray::IsEmpty

Détermine si le tableau est vide.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le tableau est vide; sinon 0.

## <a name="cobarrayoperator--"></a><a name="operator_at"></a>CObArray::opérateur [ ]

Ces opérateurs de sous-scriptums `GetAt` remplacent les fonctions et les `SetAt` fonctions.

```
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>Notes

Le premier opérateur, appelé pour des tableaux qui ne sont pas **const**, peut être utilisé soit sur la droite (r-valeur) ou la gauche (l-valeur) d’une déclaration d’affectation. Le second, appelé pour les tableaux **de cônes,** ne peut être utilisé que sur la droite.

La version Debug de la bibliothèque affirme si le sous-scriptum (soit sur le côté gauche ou à droite d’une déclaration d’affectation) est hors limites.

Le tableau suivant montre d’autres opérateurs qui sont similaires à `CObArray::operator []`.

|Classe|Opérateur|
|-----------|--------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE& opérateur [](int_ptr** `nindex` ** \);**<br /><br /> **BYTE opérateur [](int_ptr** `nindex` ** \) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD& opérateur [](int_ptr** `nindex` ** \);**<br /><br /> **L’opérateur DWORD [](int_ptr** `nindex` ** \) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**vide\*& opérateur [](int_ptr** `nindex` ** \);**<br /><br /> **opérateur\* vide [](int_ptr** `nindex` ** \) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString& opérateur [](int_ptr** `nindex` ** \);**<br /><br /> **Opérateur CString [](int_ptr** `nindex` ** \) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT& opérateur [](int_ptr** `nindex` ** \);**<br /><br /> **Opérateur UINT [](int_ptr** `nindex` ** \) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD& opérateur [](int_ptr** `nindex` ** \);**<br /><br /> **L’opérateur WORD [](int_ptr** `nindex` ** \) const;**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

## <a name="cobarrayremoveall"></a><a name="removeall"></a>CObArray::RemoveAll

Supprime tous les pointeurs de ce tableau, `CObject` mais ne supprime pas réellement les objets.

```
void RemoveAll();
```

### <a name="remarks"></a>Notes

Si le tableau est déjà vide, la fonction fonctionne toujours.

La `RemoveAll` fonction libère toute mémoire utilisée pour le stockage de pointeur.

Le tableau suivant montre d’autres `CObArray::RemoveAll`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**vide RemoveAll( );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**vide RemoveAll( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**vide RemoveAll( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**vide RemoveAll( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**vide RemoveAll( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**vide RemoveAll( );**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

## <a name="cobarrayremoveat"></a><a name="removeat"></a>CObArray::RemoveAt

Supprime un ou plusieurs éléments à partir d’un index spécifié dans un tableau.

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un indice d’intégration supérieur ou égal à 0 et inférieur `GetUpperBound`ou égal à la valeur retournée par .

*nCompte*<br/>
Nombre d'éléments à supprimer.

### <a name="remarks"></a>Notes

Dans le processus, il déplace vers le bas tous les éléments au-dessus de l’élément supprimé.s). Il décrément la limite supérieure du tableau mais ne libère pas la mémoire.

Si vous essayez d’enlever plus d’éléments que ceux contenus dans le tableau au-dessus du point de suppression, la version Debug de la bibliothèque affirme.

La `RemoveAt` fonction supprime `CObject` le pointeur du tableau, mais elle ne supprime pas l’objet lui-même.

Le tableau suivant montre d’autres `CObArray::RemoveAt`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAt ( INT_PTR** `nIndex` **, INT_PTR** `nCount` **1 );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAt ( INT_PTR** `nIndex` **, INT_PTR** `nCount` **1 );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAt ( INT_PTR** `nIndex` **, INT_PTR** `nCount` **1 );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAt ( INT_PTR** `nIndex` **, INT_PTR** `nCount` **1 );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAt ( INT_PTR** `nIndex` **, INT_PTR** `nCount` **1 );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**suppression de videAt ( INT_PTR** `nIndex` **, INT_PTR** *nCount* **1 );**|

### <a name="example"></a>Exemple

  Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

Les résultats de ce programme sont les suivants :

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

## <a name="cobarraysetat"></a><a name="setat"></a>CObArray::SetAt

Définit l’élément de tableau à l’index spécifié.

```
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un indice d’intégration supérieur ou égal à 0 et inférieur `GetUpperBound`ou égal à la valeur retournée par .

*nouvel Element*<br/>
Le pointeur d’objet à insérer dans ce tableau. Une valeur NULL est autorisée.

### <a name="remarks"></a>Notes

`SetAt`ne fera pas croître le tableau. Utilisez `SetAtGrow` si vous voulez que le tableau se développe automatiquement.

Vous devez vous assurer que votre valeur indicative représente une position valide dans le tableau. S’il est hors limites, alors la version Debug de la bibliothèque affirme.

Le tableau suivant montre d’autres `CObArray::SetAt`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAt ( INT_PTR** `nIndex` **, BYTE** `newElement` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAt ( INT_PTR** `nIndex` **, DWORD** `newElement` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAt ( INT_PTR** `nIndex` **, vide** <strong>\*</strong> `newElement` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAt ( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAt ( INT_PTR** `nIndex` **, UINT** `newElement` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAt ( INT_PTR** `nIndex` **, WORD** `newElement` **);**|

### <a name="example"></a>Exemple

  Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

Les résultats de ce programme sont les suivants :

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

## <a name="cobarraysetatgrow"></a><a name="setatgrow"></a>CObArray::SetAtGrow

Définit l’élément de tableau à l’index spécifié.

```
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Un indice d’intégration supérieur ou égal à 0.

*nouvel Element*<br/>
Le pointeur d’objet à ajouter à ce tableau. Une valeur NULL est autorisée.

### <a name="remarks"></a>Notes

Le tableau se développe automatiquement si nécessaire (c’est-à-dire que la limite supérieure est ajustée pour accueillir le nouvel élément).

Le tableau suivant montre d’autres `CObArray::SetAtGrow`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow ( INT_PTR** `nIndex` **, BYTE** `newElement` **);**<br /><br /> **lancer( CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAtGrow ( INT_PTR** `nIndex` **, DWORD** `newElement` **);**<br /><br /> **lancer( CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAtGrow ( INT_PTR** `nIndex` **, vide** <strong>\*</strong> `newElement` **);**<br /><br /> **lancer( CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**<br /><br /> **lancer( CMemoryException\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, UINT** `newElement` **);**<br /><br /> **lancer( CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow ( INT_PTR** `nIndex` **, WORD** `newElement` **);**<br /><br /> **lancer( CMemoryException\* );**|

### <a name="example"></a>Exemple

  Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

Les résultats de ce programme sont les suivants :

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

## <a name="cobarraysetsize"></a><a name="setsize"></a>CObArray::SetSize

Établit la taille d’un tableau vide ou existant; alloue la mémoire si nécessaire.

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Paramètres

*nNewSize (en)*<br/>
La nouvelle taille du tableau (nombre d’éléments). Doit être supérieur ou égal à 0.

*nGrowBy (en)*<br/>
Le nombre minimum de fentes d’élément à allouer si une augmentation de taille est nécessaire.

### <a name="remarks"></a>Notes

Si la nouvelle taille est plus petite que l’ancienne taille, alors le tableau est tronqué et toute mémoire inutilisée est libérée. Pour plus `SetSize` d’efficacité, appelez pour définir la taille du tableau avant de l’utiliser. Cela empêche la nécessité de réaffecter et de copier le tableau chaque fois qu’un élément est ajouté.

Le *paramètre nGrowBy* affecte l’allocation de mémoire interne pendant que le tableau est en croissance. Son utilisation n’affecte jamais `GetSize` la `GetUpperBound`taille du tableau tel que rapporté par et .

Si la taille du tableau a augmenté, tous les pointeurs **CObject** <strong>\*</strong> nouvellement attribués sont réglés à NULL.

Le tableau suivant montre d’autres `CObArray::SetSize`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetSize ( INT_PTR** `nNewSize` **, int** `nGrowBy` **-1 );**<br /><br /> **lancer( CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetSize ( INT_PTR** `nNewSize` **, int** `nGrowBy` **-1 );**<br /><br /> **lancer( CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetSize ( INT_PTR** `nNewSize` **, int** `nGrowBy` **-1 );**<br /><br /> **lancer( CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetSize ( INT_PTR** `nNewSize` **, int** `nGrowBy` **-1 );**<br /><br /> **lancer( CMemoryException\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetSize ( INT_PTR** `nNewSize` **, int** `nGrowBy` **-1 );**<br /><br /> **lancer( CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetSize ( INT_PTR** `nNewSize` **, int** `nGrowBy` **-1 );**<br /><br /> **lancer( CMemoryException\* );**|

### <a name="example"></a>Exemple

  Voir l’exemple pour [CObArray::GetData](#getdata).

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CStringArray, classe](../../mfc/reference/cstringarray-class.md)<br/>
[CPtrArray, classe](../../mfc/reference/cptrarray-class.md)<br/>
[CByteArray, classe](../../mfc/reference/cbytearray-class.md)<br/>
[Classe CWordArray](../../mfc/reference/cwordarray-class.md)<br/>
[CDWordArray, classe](../../mfc/reference/cdwordarray-class.md)
