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
ms.openlocfilehash: b083bf0e82f9d9b928e613f07a71d36147240cd2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212369"
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
|[CObArray :: CObArray](#cobarray)|Construit un tableau vide pour les `CObject` pointeurs.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CObArray :: Add](#add)|Ajoute un élément à la fin du tableau ; étend le tableau si nécessaire.|
|[CObArray :: Append](#append)|Ajoute un autre tableau au tableau ; étend le tableau si nécessaire.|
|[CObArray :: Copy](#copy)|Copie un autre tableau dans le tableau ; étend le tableau si nécessaire.|
|[CObArray :: ElementAt](#elementat)|Retourne une référence temporaire au pointeur d'élément dans le tableau.|
|[CObArray :: FreeExtra](#freeextra)|Libère toute la mémoire inutilisée au-dessus de la limite supérieure actuelle.|
|[CObArray :: GetAt](#getat)|Retourne la valeur à un index donné.|
|[CObArray :: GetCount](#getcount)|Obtient le nombre d'éléments dans ce tableau.|
|[CObArray :: GetData](#getdata)|Autorise l'accès aux éléments du tableau. Sa valeur peut être NULL.|
|[CObArray :: est à obtenir](#getsize)|Obtient le nombre d'éléments dans ce tableau.|
|[CObArray :: GetUpperBound](#getupperbound)|Retourne le plus grand index valide.|
|[CObArray :: InsertAt](#insertat)|Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.|
|[CObArray :: IsEmpty](#isempty)|Détermine si le tableau est vide.|
|[CObArray :: RemoveAll](#removeall)|Supprime tous les éléments de ce tableau.|
|[CObArray :: RemoveAt](#removeat)|Supprime un élément à un index spécifique.|
|[CObArray :: SetAt](#setat)|Définit la valeur d'un index donné. Le tableau n'est pas autorisé à s'étendre.|
|[CObArray :: SetAtGrow](#setatgrow)|Définit la valeur d'un index donné. Le tableau est étendu si nécessaire.|
|[CObArray :: configure](#setsize)|Définit le nombre d'éléments que ce tableau doit contenir.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CObArray ::, opérateur \[\]](#operator_at)|Définit ou obtient l'élément au niveau de l'index spécifié.|

## <a name="remarks"></a>Notes

Ces tableaux d’objets sont similaires aux tableaux C, mais ils peuvent se réduire et croître de manière dynamique selon les besoins.

Les index de tableau commencent toujours à la position 0. Vous pouvez décider s’il faut corriger la limite supérieure ou autoriser le tableau à se développer lorsque vous ajoutez des éléments au-delà de la limite actuelle. La mémoire est allouée de façon contiguë à la limite supérieure, même si certains éléments ont la valeur null.

Sous Win32, la taille d’un `CObArray` objet est limitée uniquement à la mémoire disponible.

Comme avec un tableau C, le temps d’accès d’un `CObArray` élément indexé est constant et indépendant de la taille du tableau.

`CObArray`incorpore la macro IMPLEMENT_SERIAL pour prendre en charge la sérialisation et le vidage de ses éléments. Si un tableau de `CObject` pointeurs est stocké dans une archive, avec l’opérateur d’insertion surchargé ou avec la `Serialize` fonction membre, chaque `CObject` élément est, à son tour, sérialisé avec son index de tableau.

Si vous avez besoin d’un vidage d' `CObject` éléments individuels dans un tableau, vous devez définir la profondeur de l' `CDumpContext` objet à une valeur supérieure ou égale à 1.

Lorsqu’un `CObArray` objet est supprimé ou que ses éléments sont supprimés, seuls les `CObject` pointeurs sont supprimés, pas les objets qu’ils référencent.

> [!NOTE]
> Avant d'utiliser un tableau, utilisez `SetSize` pour définir sa taille et lui allouer la mémoire nécessaire. Si vous n'utilisez pas `SetSize`, l'ajout d'éléments à votre tableau risque d'entraîner de fréquentes opérations de réallocation et de copie de ce dernier. Les opérations fréquentes de réallocation et de copie sont inefficaces et peuvent fragmenter la mémoire.

La dérivation de classe de tableau est semblable à la dérivation de liste. Pour plus d’informations sur la dérivation d’une classe de liste à usage spécial, consultez l’article [Collections](../../mfc/collections.md).

> [!NOTE]
> Vous devez utiliser la macro IMPLEMENT_SERIAL dans l’implémentation de votre classe dérivée si vous envisagez de sérialiser le tableau.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcoll. h

## <a name="cobarrayadd"></a><a name="add"></a>CObArray :: Add

Ajoute un nouvel élément à la fin d’un tableau, en augmentant le tableau de 1.

```
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>Paramètres

*newElement*<br/>
`CObject`Pointeur à ajouter à ce tableau.

### <a name="return-value"></a>Valeur de retour

Index de l’élément ajouté.

### <a name="remarks"></a>Notes

Si la valeur de la fonction de [configuration](#setsize) est utilisée avec une valeur *nGrowBy* supérieure à 1, une mémoire supplémentaire peut être allouée. Toutefois, la limite supérieure n’augmente que de 1.

Le tableau suivant présente d’autres fonctions membres similaires à `CObArray::Add` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR Add (Byte** `newElement` **);**<br /><br /> **Throw (CMemoryException \* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR Add (DWORD** `newElement` **);**<br /><br /> **Throw (CMemoryException \* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR ajouter (void** <strong>\*</strong> `newElement` **);**<br /><br /> **Throw (CMemoryException \* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR Add (LPCTSTR** `newElement` **); Throw (CMemoryException \* );**<br /><br /> **INT_PTR Add (const CString&** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR Add (uint** `newElement` **);**<br /><br /> **Throw (CMemoryException \* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR ajouter (Word** `newElement` **);**<br /><br /> **Throw (CMemoryException \* );**|

### <a name="example"></a>Exemple

  Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

Les résultats de ce programme sont les suivants :

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

## <a name="cobarrayappend"></a><a name="append"></a>CObArray :: Append

Appelez cette fonction membre pour ajouter le contenu d’un autre tableau à la fin du tableau donné.

```
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
Source des éléments à ajouter au tableau.

### <a name="return-value"></a>Valeur de retour

Index du premier élément ajouté.

### <a name="remarks"></a>Notes

Les tableaux doivent être du même type.

Si nécessaire, `Append` peut allouer de la mémoire supplémentaire pour prendre en charge les éléments ajoutés au tableau.

Le tableau suivant présente d’autres fonctions membres similaires à `CObArray::Append` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Ajout de INT_PTR (const CByteArray&** *src* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Ajout de INT_PTR (const CDWordArray&** *src* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Ajout de INT_PTR (const CPtrArray&** *src* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Ajout de INT_PTR (const CStringArray&** *src* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Ajout de INT_PTR (const CUIntArray&** *src* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Ajout de INT_PTR (const CWordArray&** *src* **);**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

## <a name="cobarraycopy"></a><a name="copy"></a>CObArray :: Copy

Appelez cette fonction membre pour remplacer les éléments du tableau donné par les éléments d’un autre tableau du même type.

```cpp
void Copy(const CObArray& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
Source des éléments à copier dans le tableau.

### <a name="remarks"></a>Notes

`Copy`ne libère pas la mémoire ; Toutefois, si nécessaire, `Copy` peut allouer de la mémoire supplémentaire pour prendre en charge les éléments copiés dans le tableau.

Le tableau suivant présente d’autres fonctions membres similaires à `CObArray::Copy` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void Copy (const CByteArray&** *src* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void Copy (const CDWordArray&** *src* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void Copy (const CPtrArray&** *src* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void Copy (const CStringArray&** *src* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void Copy (const CUIntArray&** *src* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void Copy (const CWordArray&** *src* **);**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

## <a name="cobarraycobarray"></a><a name="cobarray"></a>CObArray :: CObArray

Construit un tableau de `CObject` pointeurs vide.

```
CObArray();
```

### <a name="remarks"></a>Notes

Le tableau augmente un élément à la fois.

Le tableau suivant présente d’autres constructeurs similaires à `CObArray::CObArray` .

|Classe|Constructeur|
|-----------|-----------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray ();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CStringArray( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntArray( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray( );**|

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

## <a name="cobarrayelementat"></a><a name="elementat"></a>CObArray :: ElementAt

Retourne une référence temporaire au pointeur d'élément dans le tableau.

```
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index entier qui est supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par `GetUpperBound` .

### <a name="return-value"></a>Valeur de retour

Référence à un `CObject` pointeur.

### <a name="remarks"></a>Notes

Il est utilisé pour implémenter l’opérateur d’assignation côté gauche pour les tableaux. Notez qu’il s’agit d’une fonction avancée qui ne doit être utilisée que pour implémenter des opérateurs de tableau spéciaux.

Le tableau suivant présente d’autres fonctions membres similaires à `CObArray::ElementAt` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE& ElementAt (INT_PTR** `nIndex` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD& ElementAt (INT_PTR** `nIndex` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void \*& ElementAt (INT_PTR** `nIndex` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString& ElementAt (INT_PTR** `nIndex` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT& ElementAt (INT_PTR** `nIndex` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD& ElementAt (INT_PTR** `nIndex` **);**|

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CObArray :: de](#getsize).

## <a name="cobarrayfreeextra"></a><a name="freeextra"></a>CObArray :: FreeExtra

Libère toute mémoire supplémentaire allouée lors de la croissance du tableau.

```cpp
void FreeExtra();
```

### <a name="remarks"></a>Notes

Cette fonction n’a aucun effet sur la taille ou la limite supérieure du tableau.

Le tableau suivant présente d’autres fonctions membres similaires à `CObArray::FreeExtra` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void FreeExtra ();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void FreeExtra ();**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void FreeExtra ();**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void FreeExtra ();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void FreeExtra ();**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void FreeExtra ();**|

### <a name="example"></a>Exemple

  Consultez l’exemple de [CObArray :: GetData](#getdata).

## <a name="cobarraygetat"></a><a name="getat"></a>CObArray :: GetAt

Retourne l’élément de tableau à l’index spécifié.

```
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index entier qui est supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par `GetUpperBound` .

### <a name="return-value"></a>Valeur de retour

`CObject`Élément pointeur actuellement à cet index.

### <a name="remarks"></a>Notes

> [!NOTE]
> Le passage d’une valeur négative ou d’une valeur supérieure à la valeur retournée par `GetUpperBound` entraîne une assertion ayant échoué.

Le tableau suivant présente d’autres fonctions membres similaires à `CObArray::GetAt` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Octet GetAt (INT_PTR** `nIndex` **) const ;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt (INT_PTR** `nIndex` **) const ;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void \* GetAt (INT_PTR** `nIndex` **) const ;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString GetAt (INT_PTR** `nIndex` **) const ;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Uint GetAt (INT_PTR** `nIndex` **) const ;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Mot GetAt (INT_PTR** `nIndex` **) const ;**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

## <a name="cobarraygetcount"></a><a name="getcount"></a>CObArray :: GetCount

Retourne le nombre d’éléments du tableau.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans le tableau.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre d’éléments dans le tableau. Étant donné que les index sont de base zéro, la taille est égale à 1 par rapport à l’index le plus grand.

Le tableau suivant présente d’autres fonctions membres similaires à `CObArray::GetCount` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetCount () const ;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetCount () const ;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetCount () const ;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetCount () const ;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetCount () const ;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetCount () const ;**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

## <a name="cobarraygetdata"></a><a name="getdata"></a>CObArray :: GetData

Utilisez cette fonction membre pour obtenir un accès direct aux éléments du tableau.

```
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le tableau de `CObject` pointeurs.

### <a name="remarks"></a>Notes

Si aucun élément n’est disponible, `GetData` retourne une valeur null.

Bien que l’accès direct aux éléments d’un tableau puisse vous aider à travailler plus rapidement, soyez prudent lors de l’appel de `GetData` ; toutes les erreurs que vous apportez affectent directement les éléments de votre tableau.

Le tableau suivant présente d’autres fonctions membres similaires à `CObArray::GetData` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**const octet \* GetData () const ; BYTE \* GetData ();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**const DWORD \* GetData () const ; DWORD \* GetData ();**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**const void \* \* GetData () const ; void \* \* GetData ();**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**const CString \* GetData () const ; CString \* GetData ();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**const UINT \* GetData () const ; UINT \* GetData ();**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**const mot \* GetData () const ; MOT \* GetData ();**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

## <a name="cobarraygetsize"></a><a name="getsize"></a>CObArray :: est à obtenir

Retourne la taille du tableau.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Notes

Étant donné que les index sont de base zéro, la taille est égale à 1 par rapport à l’index le plus grand.

Le tableau suivant présente d’autres fonctions membres similaires à `CObArray::GetSize` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTRs () const ;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTRs () const ;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTRs () const ;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTRs () const ;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTRs () const ;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTRs () const ;**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

## <a name="cobarraygetupperbound"></a><a name="getupperbound"></a>CObArray :: GetUpperBound

Retourne la limite supérieure actuelle de ce tableau.

```
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>Valeur de retour

Index de la limite supérieure (de base zéro).

### <a name="remarks"></a>Notes

Étant donné que les index de tableau sont de base zéro, cette fonction retourne une valeur 1 inférieure à `GetSize` .

La condition `GetUpperBound( )` =-1 indique que le tableau ne contient pas d’éléments.

Le tableau suivant présente d’autres fonctions membres similaires à `CObArray::GetUpperBound` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetUpperBound () const ;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetUpperBound () const ;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetUpperBound () const ;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetUpperBound () const ;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetUpperBound () const ;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetUpperBound () const ;**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

## <a name="cobarrayinsertat"></a><a name="insertat"></a>CObArray :: InsertAt

Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.

```cpp
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
Index entier qui peut être supérieur à la valeur retournée par `GetUpperBound` .

*newElement*<br/>
`CObject`Pointeur à placer dans ce tableau. Un *newelement* de valeur null est autorisé.

*nCount*<br/>
Nombre de fois où cet élément doit être inséré (1 par défaut).

*nStartIndex*<br/>
Index entier qui peut être supérieur à la valeur retournée par `GetUpperBound` .

*pNewArray*<br/>
Autre tableau qui contient les éléments à ajouter à ce tableau.

### <a name="remarks"></a>Notes

La première version de `InsertAt` insère un élément (ou plusieurs copies d’un élément) à un index spécifié dans un tableau. Dans le processus, il est déplacé vers le haut (en incrémentant l’index) de l’élément existant à cet index, et il décale tous les éléments situés au-dessus de celui-ci.

La deuxième version insère tous les éléments d’une autre `CObArray` collection, en commençant à la position *nStartIndex* .

`SetAt`En revanche, la fonction remplace un élément de tableau spécifié et ne décale aucun élément.

Le tableau suivant présente d’autres fonctions membres similaires à `CObArray::InsertAt` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, Byte** `newElement` **, int** `nCount` **= 1);**<br /><br /> **Throw (CMemoryException \* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CByteArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **Throw (CMemoryException \* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, DWORD** `newElement` **, int** `nCount` **= 1);**<br /><br /> **Throw (CMemoryException \* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CDWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **Throw (CMemoryException \* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **, int** `nCount` **= 1);**<br /><br /> **Throw (CMemoryException \* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CPtrArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **Throw (CMemoryException \* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **, int** `nCount` **= 1);**<br /><br /> **Throw (CMemoryException \* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CStringArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **Throw (CMemoryException \* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, uint** `newElement` **, int** `nCount` **= 1);**<br /><br /> **Throw (CMemoryException \* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CUIntArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **Throw (CMemoryException \* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, Word** `newElement` **, int** `nCount` **= 1);**<br /><br /> **Throw (CMemoryException \* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **Throw (CMemoryException \* );**|

### <a name="example"></a>Exemple

  Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

Les résultats de ce programme sont les suivants :

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

## <a name="cobarrayisempty"></a><a name="isempty"></a>CObArray :: IsEmpty

Détermine si le tableau est vide.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le tableau est vide ; Sinon, 0.

## <a name="cobarrayoperator--"></a><a name="operator_at"></a>CObArray :: Operator []

Ces opérateurs d’indice sont un substitut pratique pour `SetAt` les `GetAt` fonctions et.

```
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>Notes

Le premier opérateur, appelé pour les tableaux qui ne sont pas **`const`** , peut être utilisé soit sur le droit (r-value), soit sur la gauche (l-value) d’une instruction d’assignation. La seconde, appelée pour les **`const`** tableaux, peut être utilisée uniquement à droite.

La version de débogage de la bibliothèque déclare si l’indice (à gauche ou à droite d’une instruction d’assignation) est hors limites.

Le tableau suivant présente d’autres opérateurs similaires à `CObArray::operator []` .

|Classe|Opérateur|
|-----------|--------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE& Operator [] (INT_PTR** `nindex` ** \) ;**<br /><br /> **Byte, opérateur [] (INT_PTR** `nindex` ** \) const ;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD& Operator [] (INT_PTR** `nindex` ** \) ;**<br /><br /> **DWORD, opérateur [] (INT_PTR** `nindex` ** \) const ;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void \*& Operator [] (INT_PTR** `nindex` ** \) ;**<br /><br /> **void, \* opérateur [] (INT_PTR** `nindex` ** \) const ;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString& Operator [] (INT_PTR** `nindex` ** \) ;**<br /><br /> **CString, opérateur [] (INT_PTR** `nindex` ** \) const ;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT& Operator [] (INT_PTR** `nindex` ** \) ;**<br /><br /> **Uint, opérateur [] (INT_PTR** `nindex` ** \) const ;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD& Operator [] (INT_PTR** `nindex` ** \) ;**<br /><br /> **Opérateur Word [] (INT_PTR** `nindex` ** \) const ;**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

## <a name="cobarrayremoveall"></a><a name="removeall"></a>CObArray :: RemoveAll

Supprime tous les pointeurs de ce tableau, mais ne supprime pas réellement les `CObject` objets.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Notes

Si le tableau est déjà vide, la fonction fonctionne toujours.

La `RemoveAll` fonction libère toute la mémoire utilisée pour le stockage du pointeur.

Le tableau suivant présente d’autres fonctions membres similaires à `CObArray::RemoveAll` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAll ();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAll ();**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAll ();**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAll ();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAll ();**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAll ();**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

## <a name="cobarrayremoveat"></a><a name="removeat"></a>CObArray :: RemoveAt

Supprime un ou plusieurs éléments commençant à un index spécifié dans un tableau.

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index entier qui est supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par `GetUpperBound` .

*nCount*<br/>
Nombre d'éléments à supprimer.

### <a name="remarks"></a>Notes

Dans le processus, il décale tous les éléments au-dessus du ou des éléments supprimés. Elle décrémente la limite supérieure du tableau, mais ne libère pas la mémoire.

Si vous essayez de supprimer plus d’éléments que ceux contenus dans le tableau au-dessus du point de suppression, la version Debug de la bibliothèque Assert.

La `RemoveAt` fonction supprime le `CObject` pointeur du tableau, mais elle ne supprime pas l’objet lui-même.

Le tableau suivant présente d’autres fonctions membres similaires à `CObArray::RemoveAt` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** *nCount* **= 1);**|

### <a name="example"></a>Exemple

  Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

Les résultats de ce programme sont les suivants :

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

## <a name="cobarraysetat"></a><a name="setat"></a>CObArray :: SetAt

Définit l’élément de tableau à l’index spécifié.

```cpp
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index entier qui est supérieur ou égal à 0 et inférieur ou égal à la valeur retournée par `GetUpperBound` .

*newElement*<br/>
Pointeur d’objet à insérer dans ce tableau. Une valeur NULL est autorisée.

### <a name="remarks"></a>Notes

`SetAt`n’entraîne pas la croissance du tableau. Utilisez `SetAtGrow` si vous souhaitez que le tableau augmente automatiquement.

Vous devez vous assurer que votre valeur d’index représente une position valide dans le tableau. S’il est hors limites, la version de débogage de la bibliothèque Assert.

Le tableau suivant présente d’autres fonctions membres similaires à `CObArray::SetAt` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAt (INT_PTR** `nIndex` **, Byte** `newElement` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, DWORD** `newElement` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, uint** `newElement` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAt (INT_PTR** `nIndex` **, Word** `newElement` **);**|

### <a name="example"></a>Exemple

  Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

Les résultats de ce programme sont les suivants :

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

## <a name="cobarraysetatgrow"></a><a name="setatgrow"></a>CObArray :: SetAtGrow

Définit l’élément de tableau à l’index spécifié.

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index entier supérieur ou égal à 0.

*newElement*<br/>
Pointeur d’objet à ajouter à ce tableau. Une valeur NULL est autorisée.

### <a name="remarks"></a>Notes

Le tableau s’agrandit automatiquement si nécessaire (autrement dit, la limite supérieure est ajustée pour s’adapter au nouvel élément).

Le tableau suivant présente d’autres fonctions membres similaires à `CObArray::SetAtGrow` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, Byte** `newElement` **);**<br /><br /> **Throw (CMemoryException \* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, DWORD** `newElement` **);**<br /><br /> **Throw (CMemoryException \* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **);**<br /><br /> **Throw (CMemoryException \* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**<br /><br /> **Throw (CMemoryException \* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, uint** `newElement` **);**<br /><br /> **Throw (CMemoryException \* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow (INT_PTR** `nIndex` **, Word** `newElement` **);**<br /><br /> **Throw (CMemoryException \* );**|

### <a name="example"></a>Exemple

  Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

Les résultats de ce programme sont les suivants :

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

## <a name="cobarraysetsize"></a><a name="setsize"></a>CObArray :: configure

Établit la taille d’un tableau vide ou existant ; alloue de la mémoire si nécessaire.

```cpp
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Paramètres

*nNewSize*<br/>
Nouvelle taille de tableau (nombre d’éléments). Doit être supérieure ou égale à 0.

*nGrowBy*<br/>
Nombre minimal d’emplacements d’éléments à allouer si une augmentation de la taille est nécessaire.

### <a name="remarks"></a>Notes

Si la nouvelle taille est inférieure à l’ancienne taille, le tableau est tronqué et toute la mémoire inutilisée est libérée. Pour plus d’efficacité, appelez `SetSize` pour définir la taille du tableau avant de l’utiliser. Cela évite de devoir réallouer et copier le tableau chaque fois qu’un élément est ajouté.

Le paramètre *nGrowBy* affecte l’allocation de mémoire interne pendant la croissance du tableau. Son utilisation n’affecte jamais la taille du tableau comme indiqué par `GetSize` et `GetUpperBound` .

Si la taille du tableau a augmenté, tous les pointeurs **CObject** nouvellement alloués <strong>\*</strong> ont la valeur null.

Le tableau suivant présente d’autres fonctions membres similaires à `CObArray::SetSize` .

|Classe|Fonction membre|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void Assets (INT_PTR** `nNewSize` **, int** `nGrowBy` **=-1);**<br /><br /> **Throw (CMemoryException \* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void Assets (INT_PTR** `nNewSize` **, int** `nGrowBy` **=-1);**<br /><br /> **Throw (CMemoryException \* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void Assets (INT_PTR** `nNewSize` **, int** `nGrowBy` **=-1);**<br /><br /> **Throw (CMemoryException \* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void Assets (INT_PTR** `nNewSize` **, int** `nGrowBy` **=-1);**<br /><br /> **Throw (CMemoryException \* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void Assets (INT_PTR** `nNewSize` **, int** `nGrowBy` **=-1);**<br /><br /> **Throw (CMemoryException \* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void Assets (INT_PTR** `nNewSize` **, int** `nGrowBy` **=-1);**<br /><br /> **Throw (CMemoryException \* );**|

### <a name="example"></a>Exemple

  Consultez l’exemple de [CObArray :: GetData](#getdata).

## <a name="see-also"></a>Voir aussi

[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CStringArray, classe](../../mfc/reference/cstringarray-class.md)<br/>
[CPtrArray, classe](../../mfc/reference/cptrarray-class.md)<br/>
[Classe CByteArray](../../mfc/reference/cbytearray-class.md)<br/>
[CWordArray, classe](../../mfc/reference/cwordarray-class.md)<br/>
[CDWordArray, classe](../../mfc/reference/cdwordarray-class.md)
