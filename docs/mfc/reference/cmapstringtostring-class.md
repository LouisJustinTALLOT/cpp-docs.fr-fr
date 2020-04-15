---
title: CMapStringToString, classe
ms.date: 11/04/2016
f1_keywords:
- CMapStringToString
- AFXCOLL/CMapStringToString
- AFXCOLL/CMapStringToString::CPair
- AFXCOLL/CMapStringToString::CMapStringToString
- AFXCOLL/CMapStringToString::GetCount
- AFXCOLL/CMapStringToString::GetHashTableSize
- AFXCOLL/CMapStringToString::GetNextAssoc
- AFXCOLL/CMapStringToString::GetSize
- AFXCOLL/CMapStringToString::GetStartPosition
- AFXCOLL/CMapStringToString::HashKey
- AFXCOLL/CMapStringToString::InitHashTable
- AFXCOLL/CMapStringToString::IsEmpty
- AFXCOLL/CMapStringToString::Lookup
- AFXCOLL/CMapStringToString::LookupKey
- AFXCOLL/CMapStringToString::PGetFirstAssoc
- AFXCOLL/CMapStringToString::PGetNextAssoc
- AFXCOLL/CMapStringToString::PLookup
- AFXCOLL/CMapStringToString::RemoveAll
- AFXCOLL/CMapStringToString::RemoveKey
- AFXCOLL/CMapStringToString::SetAt
helpviewer_keywords:
- CMapStringToString [MFC], CPair
- CMapStringToString [MFC], CMapStringToString
- CMapStringToString [MFC], GetCount
- CMapStringToString [MFC], GetHashTableSize
- CMapStringToString [MFC], GetNextAssoc
- CMapStringToString [MFC], GetSize
- CMapStringToString [MFC], GetStartPosition
- CMapStringToString [MFC], HashKey
- CMapStringToString [MFC], InitHashTable
- CMapStringToString [MFC], IsEmpty
- CMapStringToString [MFC], Lookup
- CMapStringToString [MFC], LookupKey
- CMapStringToString [MFC], PGetFirstAssoc
- CMapStringToString [MFC], PGetNextAssoc
- CMapStringToString [MFC], PLookup
- CMapStringToString [MFC], RemoveAll
- CMapStringToString [MFC], RemoveKey
- CMapStringToString [MFC], SetAt
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
ms.openlocfilehash: 544154569c50369b805ba296aa975849f245d4ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370116"
---
# <a name="cmapstringtostring-class"></a>CMapStringToString, classe

Prend en charge les mappages d'objets `CString` indexés par des objets `CString` .

## <a name="syntax"></a>Syntaxe

```
class CMapStringToString : public CObject
```

## <a name="members"></a>Membres

Les fonctions `CMapStringToString` de membre sont similaires aux fonctions de membre de la classe [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Ainsi, vous pouvez utiliser la documentation de référence de `CMapStringToOb` pour connaître les spécificités des fonctions membres. Où que `CObject` vous voyiez un pointeur comme un paramètre de fonction de valeur de retour ou de « sortie », remplacez un pointeur à **l’omble**chevalier. Partout où `CObject` vous voyez un pointeur comme un paramètre de fonction "entrée", remplacez un pointeur à **l’omble**.

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

par exemple, se traduit par

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

### <a name="public-structures"></a>Structures publiques

|Nom|Description|
|----------|-----------------|
|[CMapStringToString::CPair](#cpair)|Une structure imbriquée contenant une valeur clé et la valeur de l’objet à chaîne associé.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMapStringToString::CMapStringToString](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMapStringToString::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Retourne le nombre d’éléments dans cette carte.|
|[CMapStringToString::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Détermine le nombre actuel d’éléments dans le tableau de hachage.|
|[CMapStringToString::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Obtient le prochain élément pour itérer.|
|[CMapStringToString::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Retourne le nombre d’éléments dans cette carte.|
|[CMapStringToString::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Retourne la position du premier élément.|
|[CMapStringToString::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Calcule la valeur de hachage d’une clé spécifiée.|
|[CMapStringToString::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Initialise la table de hachage.|
|[CMapStringToString::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Tests pour l’état de la carte vide (pas d’éléments).|
|[CMapStringToString::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Recherche vers le haut d’un pointeur vide basé sur la clé de pointeur de vide. La valeur de pointeur, et non l’entité à qui il pointe, est utilisée pour la comparaison de la clé.|
|[CMapStringToString::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Renvoie une référence à la clé associée à la valeur clé spécifiée.|
|[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)|Obtient un pointeur `CString` à la première dans la carte.|
|[CMapStringToString::PGetNextAssoc](#pgetnextassoc)|Obtient un pointeur `CString` à l’autre pour itérer.|
|[CMapStringToString::PLookup](#plookup)|Retourne un pointeur à un `CString` dont la valeur correspond à la valeur spécifiée.|
|[CMapStringToString::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Supprime tous les éléments de cette carte.|
|[CMapStringToString::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Supprime un élément spécifié par une clé.|
|[CMapStringToString::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Insère un élément dans la carte; remplace un élément existant si une clé correspondante est trouvée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CMapStringToString::opérateur \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Insère un élément dans la `SetAt`carte — substitution de l’opérateur pour .|

## <a name="remarks"></a>Notes

`CMapStringToString` incorpore la macro `IMPLEMENT_SERIAL` pour prendre en charge la sérialisation et le vidage de ses éléments. Chaque élément est sérialisé à son tour si une carte est **<<** stockée dans `Serialize` une archive, soit avec l’insertion surchargée () opérateur ou avec la fonction membre.

Si vous avez besoin `CString` -  `CString` d’un dépotoir d’éléments individuels, vous devez définir la profondeur du contexte de décharge à 1 ou plus.

Lorsqu’un `CMapStringToString` objet est supprimé ou lorsque ses `CString` éléments sont supprimés, les objets sont supprimés au besoin.

Pour plus `CMapStringToString`d’informations sur , voir l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>Spécifications

**En-tête:** afxcoll.h

## <a name="cmapstringtostringcpair"></a><a name="cpair"></a>CMapStringToString::CPair

Contient une valeur clé et la valeur de l’objet à chaîne associé.

### <a name="remarks"></a>Notes

Il s’agit d’une structure imbriquée au sein de la classe [CMapStringToString](../../mfc/reference/cmapstringtostring-class.md).

La structure est composée de deux champs :

- `key`La valeur réelle du type clé.

- `value`La valeur de l’objet associé.

Il est utilisé pour stocker les valeurs de retour de [CMapStringToString::PLookup](#plookup), [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc), et [CMapStringToString::PGetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Exemple

  Pour un exemple d’utilisation, voir l’exemple pour [CMapStringToString::PLookup](#plookup).

## <a name="cmapstringtostringpgetfirstassoc"></a><a name="pgetfirstassoc"></a>CMapStringToString::PGetFirstAssoc

Retourne la première entrée de l’objet de la carte.

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à la première entrée dans la carte; voir [CMapStringToString::CPair](#cpair). Si la carte est vide, la valeur est NULL.

### <a name="remarks"></a>Notes

Appelez cette fonction pour retourner un pointeur le premier élément de l’objet de carte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

## <a name="cmapstringtostringpgetnextassoc"></a><a name="pgetnextassoc"></a>CMapStringToString::PGetNextAssoc

Récupère l’élément de carte pointé par *pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>Paramètres

*pAssoc*<br/>
Points à une entrée de carte retournée par un précédent [appel PGetNextAssoc](#pgetnextassoc) ou [PGetFirstAssoc.](#pgetfirstassoc)

### <a name="return-value"></a>Valeur de retour

Un pointeur à la prochaine entrée dans la carte; voir [CMapStringToString::CPair](#cpair). Si l’élément est le dernier de la carte, la valeur est NULL.

### <a name="remarks"></a>Notes

Appelez cette méthode pour itérer à travers tous les éléments de la carte. Récupérez le premier élément `PGetFirstAssoc` avec un appel à et puis `PGetNextAssoc`itérer à travers la carte avec des appels successifs à .

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc).

## <a name="cmapstringtostringplookup"></a><a name="plookup"></a>CMapStringToString::PLookup

Recherche la valeur cartographiée à une clé donnée.

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Un pointeur à la clé pour l’élément à rechercher.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la clé spécifiée.

### <a name="remarks"></a>Notes

Appelez cette méthode pour rechercher un élément de carte avec une clé qui correspond exactement à la clé donnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC Échantillon COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
