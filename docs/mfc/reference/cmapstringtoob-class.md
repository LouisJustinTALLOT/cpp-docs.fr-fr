---
title: CMapStringToOb, classe
ms.date: 11/04/2016
f1_keywords:
- CMapStringToOb
- AFXCOLL/CMapStringToOb
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
ms.openlocfilehash: 6520d1c38701647ae51450b9b9800a7cd2701b7a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754582"
---
# <a name="cmapstringtoob-class"></a>CMapStringToOb, classe

Classe de collection de dictionnaires qui mappe des objets `CString` uniques à des pointeurs `CObject` .

## <a name="syntax"></a>Syntaxe

```
class CMapStringToOb : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMapStringToOb::CMapStringToOb](#cmapstringtoob)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMapStringToOb::GetCount](#getcount)|Retourne le nombre d’éléments dans cette carte.|
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|Détermine le nombre actuel d’éléments dans le tableau de hachage.|
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|Obtient le prochain élément pour itérer.|
|[CMapStringToOb::GetSize](#getsize)|Retourne le nombre d’éléments dans cette carte.|
|[CMapStringToOb::GetStartPosition](#getstartposition)|Retourne la position du premier élément.|
|[CMapStringToOb::HashKey](#hashkey)|Calcule la valeur de hachage d’une clé spécifiée.|
|[CMapStringToOb::InitHashTable](#inithashtable)|Initialise la table de hachage.|
|[CMapStringToOb::IsEmpty](#isempty)|Tests pour l’état de la carte vide (pas d’éléments).|
|[CMapStringToOb::Lookup](#lookup)|Recherche vers le haut d’un pointeur vide basé sur la clé de pointeur de vide. La valeur de pointeur, et non l’entité à qui il pointe, est utilisée pour la comparaison de la clé.|
|[CMapStringToOb::LookupKey](#lookupkey)|Renvoie une référence à la clé associée à la valeur clé spécifiée.|
|[CMapStringToOb::RemoveAll](#removeall)|Supprime tous les éléments de cette carte.|
|[CMapStringToOb::RemoveKey](#removekey)|Supprime un élément spécifié par une clé.|
|[CMapStringToOb::SetAt](#setat)|Insère un élément dans la carte; remplace un élément existant si une clé correspondante est trouvée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CMapStringToOb::opérateur \[\]](#operator_at)|Insère un élément dans la `SetAt`carte — substitution de l’opérateur pour .|

## <a name="remarks"></a>Notes

Une fois que `CString` -  `CObject*` vous avez inséré une paire (élément) dans la carte, vous `CString` pouvez récupérer ou supprimer efficacement la paire à l’aide d’une chaîne ou d’une valeur comme clé. Vous pouvez également itérer sur tous les éléments de la carte.

Une variable de type POSITION est utilisée pour un accès alternatif à l’entrée dans toutes les variantes de cartes. Vous pouvez utiliser un POSITION pour « se souvenir » d’une entrée et pour itérer à travers la carte. Vous pourriez penser que cette itération est séquentielle par valeur clé; ce n’est pas le cas. La séquence des éléments récupérés est indéterminée.

`CMapStringToOb` incorpore la macro `IMPLEMENT_SERIAL` pour prendre en charge la sérialisation et le vidage de ses éléments. Chaque élément est sérialisé à son tour si une carte est **<<** stockée dans `Serialize` une archive, soit avec l’insertion surchargée () opérateur ou avec la fonction membre.

Si vous avez besoin d’un vidage `CString` diagnostique des `CObject` éléments individuels de la carte (la valeur et le contenu), vous devez définir la profondeur du contexte de décharge à 1 ou plus.

Lorsqu’un `CMapStringToOb` objet est supprimé ou lorsque ses `CString` éléments sont `CObject` supprimés, les objets et les pointeurs sont supprimés. Les objets référencés par les `CObject` pointeurs ne sont pas détruits.

La dérivation de classe de carte est semblable à la dérivation de liste. Voir l’article [Collections](../../mfc/collections.md) pour une illustration de la dérivation d’une classe de liste à usage spécial.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>Spécifications

**En-tête:** afxcoll.h

## <a name="cmapstringtoobcmapstringtoob"></a><a name="cmapstringtoob"></a>CMapStringToOb::CMapStringToOb

Construit une `CString` `CObject*` carte vide.

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Paramètres

*nBlockSize (en)*<br/>
Spécifie la granularité de la mémoire-allocation pour l’extension de la carte.

### <a name="remarks"></a>Notes

Au fur et à mesure que la carte se développe, la mémoire est attribuée dans les unités d’entrées *nBlockSize.*

Le tableau suivant montre d’autres `CMapStringToOb:: CMapStringToOb`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr (INT_PTR** `nBlockSize` **10);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord (INT_PTR** `nBlockSize` **10);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr (INT_PTR** `nBlockSize` **10);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString (INT_PTR** `nBlockSize` **10);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb (INT_PTR** `nBlockSize` **10);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr (INT_PTR** `nBlockSize` **10);**|

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

## <a name="cmapstringtoobgetcount"></a><a name="getcount"></a>CMapStringToOb::GetCount

Détermine le nombre d’éléments dans la carte.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans cette carte.

### <a name="remarks"></a>Notes

Le tableau suivant montre d’autres `CMapStringToOb::GetCount`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount) ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount) ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount) ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount) ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount) ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount) ) const;**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

## <a name="cmapstringtoobgethashtablesize"></a><a name="gethashtablesize"></a>CMapStringToOb::GetHashTableSize

Détermine le nombre actuel d’éléments dans le tableau de hachage.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’éléments dans le tableau de hachage.

### <a name="remarks"></a>Notes

Le tableau suivant montre d’autres `CMapStringToOb::GetHashTableSize`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT GetHashTableSize( ) const;**|

## <a name="cmapstringtoobgetnextassoc"></a><a name="getnextassoc"></a>CMapStringToOb::GetNextAssoc

Récupère l’élément de carte à *rNextPosition*, puis met à jour *rNextPosition* pour se référer à l’élément suivant dans la carte.

```cpp
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Paramètres

*rNextPosition (en)*<br/>
Spécifie une référence à une `GetNextAssoc` `GetStartPosition` valeur POSITION retournée par un précédent ou un appel.

*rKey (en)*<br/>
Spécifie la clé retournée de l’élément récupéré (une ficelle).

*rValue (en)*<br/>
Spécifie la valeur retournée de `CObject` l’élément récupéré (un pointeur). Voir Remarques pour en savoir plus sur ce paramètre.

### <a name="remarks"></a>Notes

Cette fonction est plus utile pour itérer à travers tous les éléments de la carte. Notez que la séquence de position n’est pas nécessairement la même que la séquence de valeur clé.

Si l’élément récupéré est le dernier de la carte, alors la nouvelle valeur de *rNextPosition* est réglée à NULL.

Pour le *paramètre rValue,* assurez-vous de jeter votre type d’objet à **CObject\***, qui est ce que le compilateur exige, comme le montre l’exemple suivant:

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

Ce n’est `GetNextAssoc` pas vrai pour les cartes basées sur des modèles.

Le tableau suivant montre d’autres `CMapStringToOb::GetNextAssoc`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**vide GetNextAssoc ( POSITION&** *rNextPosition* **, void\* ** *rKey* **, void\* ** *rValue* **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**vide GetNextAssoc ( POSITION&** *rNextPosition* **, void\* ** *rKey* **, WORD&** *rValue* **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**vide GetNextAssoc ( POSITION&** *rNextPosition* **, CString&** *rKey* **, void\* ** *rValue* **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**vide GetNextAssoc ( POSITION&** *rNextPosition* **, CString&** *rKey* **, CString&** *rValue* **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**vide GetNextAssoc ( POSITION&** *rNextPosition* **, WORD&** *rKey* **, CObject\* ** *rValue* **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**vide GetNextAssoc ( POSITION&** *rNextPosition* **, WORD&** *rKey* **, void\* ** *rValue* **) const;**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

Les résultats de ce programme sont les suivants :

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

## <a name="cmapstringtoobgetsize"></a><a name="getsize"></a>CMapStringToOb::GetSize

Retourne le nombre d’éléments cartographiques.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans la carte.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre d’éléments dans la carte.

Le tableau suivant montre d’autres `CMapStringToOb::GetSize`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

## <a name="cmapstringtoobgetstartposition"></a><a name="getstartposition"></a>CMapStringToOb::GetStartPosition

Démarre une itération de carte en retournant une `GetNextAssoc` valeur POSITION qui peut être passée à un appel.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui indique une position de départ pour itérer la carte; ou NULL si la carte est vide.

### <a name="remarks"></a>Notes

La séquence d’itération n’est pas prévisible; par conséquent, le «premier élément de la carte» n’a pas d’importance particulière.

Le tableau suivant montre d’autres `CMapStringToOb::GetStartPosition`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POSITION GetStartPosition( ) const;**|

### <a name="example"></a>Exemple

Voir l’exemple pour [CMapStringToOb::GetNextAssoc](#getnextassoc).

## <a name="cmapstringtoobhashkey"></a><a name="hashkey"></a>CMapStringToOb::HashKey

Calcule la valeur de hachage d’une clé spécifiée.

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
La clé dont la valeur de hachage doit être calculée.

### <a name="return-value"></a>Valeur de retour

La valeur de hachage de la Key

### <a name="remarks"></a>Notes

Le tableau suivant montre d’autres `CMapStringToOb::HashKey`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey ( vide** <strong>\*</strong> `key` **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey ( vide** <strong>\*</strong> `key` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey ( LPCTSTR** `key` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey ( LPCTSTR** `key` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT HashKey ( WORD** `key` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT HashKey ( WORD** `key` **) const;**|

## <a name="cmapstringtoobinithashtable"></a><a name="inithashtable"></a>CMapStringToOb::InitHashTable

Initialise la table de hachage.

```cpp
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>Paramètres

*hashSize*<br/>
Nombre d’entrées dans le tableau de hachage.

*bAllocNow*<br/>
Si VRAI, alloue la table de hachage lors de l’initialisation; sinon la table est attribuée en cas de besoin.

### <a name="remarks"></a>Notes

Pour de meilleures performances, la taille de la table de hachage devrait être un nombre de choix. Pour minimiser les collisions, la taille devrait être d’environ 20 p. 100 plus grande que l’ensemble de données le plus important prévu.

Le tableau suivant montre d’autres `CMapStringToOb::InitHashTable`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**vide InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **- TRUE );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**vide InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **- TRUE );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**vide InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **- TRUE );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**vide InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **- TRUE );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**vide InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **- TRUE );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**vide InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **- TRUE );**|

## <a name="cmapstringtoobisempty"></a><a name="isempty"></a>CMapStringToOb::IsEmpty

Détermine si la carte est vide.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si cette carte ne contient pas d’éléments; sinon 0.

### <a name="example"></a>Exemple

Voir l’exemple pour [RemoveAll](#removeall).

### <a name="remarks"></a>Notes

Le tableau suivant montre d’autres fonctions de membre qui sont similaires à **CMapStringToOb:: IsEmpty**.

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty( ) const;**|

## <a name="cmapstringtooblookup"></a><a name="lookup"></a>CMapStringToOb::Lookup

Retourne `CObject` un pointeur `CString` en fonction d’une valeur.

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la clé de chaîne qui identifie l’élément à lever.

*rValue (en)*<br/>
Spécifie la valeur retournée de l’élément recherché.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’élément a été trouvé; sinon 0.

### <a name="remarks"></a>Notes

`Lookup`utilise un algorithme de hachage pour trouver rapidement l’élément de carte avec une clé qui correspond exactement (valeur). `CString`

Le tableau suivant montre d’autres `CMapStringToOb::LookUp`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL Lookup ( vide** <strong>\*</strong> `key` **, vide\* ** `rValue` ) **const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL Lookup ( vide** <strong>\*</strong> `key` **, WORD&** `rValue` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL Lookup ( LPCTSTR** `key` **, vide\* ** `rValue` ) **const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL Lookup ( LPCTSTR** `key` **, CString&** `rValue` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL Lookup ( WORD** `key` **, CObject\* ** `rValue` ) **const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL Lookup( WORD** `key` **, vide\* ** `rValue` ) **const;**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

## <a name="cmapstringtooblookupkey"></a><a name="lookupkey"></a>CMapStringToOb::LookupKey

Renvoie une référence à la clé associée à la valeur clé spécifiée.

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la clé de chaîne qui identifie l’élément à lever.

*rKey (en)*<br/>
La référence à la clé associée.

### <a name="return-value"></a>Valeur de retour

Nonzero si la clé a été trouvée; sinon 0.

### <a name="remarks"></a>Notes

L’utilisation d’une référence à une clé n’est pas sécuritaire si elle est utilisée après que l’élément associé a été retiré de la carte ou après la destruction de la carte.

Le tableau suivant montre d’autres `CMapStringToOb:: LookupKey`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey ( LPCTSTR** `key` **, LPCTSTR&** `rKey` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey ( LPCTSTR** `key` **, LPCTSTR&** `rKey` **) const;**|

## <a name="cmapstringtooboperator--"></a><a name="operator_at"></a>CMapStringToOb::opérateur [ ]

Un substitut pratique `SetAt` à la fonction de membre.

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>Valeur de retour

Une référence à un `CObject` pointeur à un objet; ou NULL si la carte est vide ou si la *clé* est hors de portée.

### <a name="remarks"></a>Notes

Ainsi, il ne peut être utilisé que sur le côté gauche d’une déclaration d’affectation (une valeur l). S’il n’y a pas d’élément de carte avec la clé spécifiée, un nouvel élément est créé.

Il n’y a pas d’équivalent « côté droit » (r-valeur) à cet opérateur parce qu’il est possible qu’une clé ne soit pas trouvée dans la carte. Utilisez `Lookup` la fonction membre pour la récupération d’éléments.

Le tableau suivant montre d’autres `CMapStringToOb::operator []`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>vide\*& opérateur\[] (vide \* </strong> `key` ** \);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD& opérateur\[](void;** ** \)** <strong>\*</strong> `key`|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**vide\*& opérateur\[](lpctstr;** `key` ** \)**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString\[& opérateur ](lpctstr;** ** \)** `key`|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& opérateur]\[(mot** `key` ** \);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**vide\*& opérateur\[] (mot** `key` ** \);**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

Les résultats de ce programme sont les suivants :

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

## <a name="cmapstringtoobremoveall"></a><a name="removeall"></a>CMapStringToOb::RemoveAll

Supprime tous les éléments de cette `CString` carte et détruit les objets clés.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Notes

Les `CObject` objets référencés par chaque clé ne sont pas détruits. La `RemoveAll` fonction peut provoquer des fuites de mémoire `CObject` si vous ne vous assurez pas que les objets référencés sont détruits.

La fonction fonctionne correctement si la carte est déjà vide.

Le tableau suivant montre d’autres `CMapStringToOb::RemoveAll`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**vide RemoveAll( );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**vide RemoveAll( );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**vide RemoveAll( );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**vide RemoveAll( );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**vide RemoveAll( );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**vide RemoveAll( );**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

## <a name="cmapstringtoobremovekey"></a><a name="removekey"></a>CMapStringToOb::RemoveKey

Recherche l’entrée de la carte correspondant à la clé fournie; puis, si la clé est trouvée, supprime l’entrée.

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la chaîne utilisée pour le plan de la carte.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’entrée a été trouvée et enlevée avec succès; sinon 0.

### <a name="remarks"></a>Notes

Cela peut causer des `CObject` fuites de mémoire si l’objet n’est pas supprimé ailleurs.

Le tableau suivant montre d’autres `CMapStringToOb::RemoveKey`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey** <strong>\*</strong> `key` **(vide);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey** <strong>\*</strong> `key` **(vide);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey (LPCTSTR);** `key` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey (LPCTSTR);** `key` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey(E) (EN** `key` **anglais) :;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey(E) (EN** `key` **anglais) :;**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

Les résultats de ce programme sont les suivants :

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

## <a name="cmapstringtoobsetat"></a><a name="setat"></a>CMapStringToOb::SetAt

Le principal moyen d’insérer un élément dans une carte.

```cpp
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la chaîne qui est la clé du nouvel élément.

*newValue*<br/>
Spécifie le `CObject` pointeur qui est la valeur du nouvel élément.

### <a name="remarks"></a>Notes

Tout d’abord, la clé est regardée vers le haut. Si la clé est trouvée, alors la valeur correspondante est modifiée; sinon un nouvel élément de valeur clé est créé.

Le tableau suivant montre d’autres `CMapStringToOb::SetAt`fonctions de membre qui sont similaires à .

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt ( vide** <strong>\*</strong> `key` **, vide** <strong>\*</strong> `newValue` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt (vide** <strong>\*</strong> `key` **, WORD** `newValue` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt ( LPCTSTR** `key` **, vide** <strong>\*</strong> `newValue` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt ( LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt ( WORD** `key` **, CObject** <strong>\*</strong> `newValue` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt ( WORD** `key` **, vide** <strong>\*</strong> `newValue` **);**|

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de la classe utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]

Les résultats de ce programme sont les suivants :

```Output
before Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $493C 11
[Bart] = a CAge at $4654 13
after Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $49C0 12
[Bart] = a CAge at $4654 13
```

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr, classe](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord, classe](../../mfc/reference/cmapptrtoword-class.md)<br/>
[Classe CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)<br/>
[CMapStringToString, classe](../../mfc/reference/cmapstringtostring-class.md)<br/>
[Classe CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)<br/>
[Classe CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)
