---
description: 'En savoir plus sur : classe CMapStringToString'
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
ms.openlocfilehash: ba82647a6e81e82b4d977e4de3beee1bfd0b7c4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207811"
---
# <a name="cmapstringtostring-class"></a>CMapStringToString, classe

Prend en charge les mappages d'objets `CString` indexés par des objets `CString` .

## <a name="syntax"></a>Syntaxe

```
class CMapStringToString : public CObject
```

## <a name="members"></a>Membres

Les fonctions membres de `CMapStringToString` sont similaires aux fonctions membres de la classe [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Ainsi, vous pouvez utiliser la documentation de référence de `CMapStringToOb` pour connaître les spécificités des fonctions membres. Partout où vous voyez un `CObject` pointeur sous la forme d’une valeur de retour ou d’un paramètre de fonction de « sortie », remplacez un pointeur par **`char`** . Partout où vous voyez un `CObject` pointeur en tant que paramètre de fonction « d’entrée », remplacez un pointeur par **`char`** .

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

par exemple, se traduit par

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

### <a name="public-structures"></a>Structures publiques

|Nom|Description|
|----------|-----------------|
|[CMapStringToString::CPair](#cpair)|Structure imbriquée contenant une valeur de clé et la valeur de l’objet String associé.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMapStringToString::CMapStringToString](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMapStringToString :: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Retourne le nombre d’éléments de ce plan.|
|[CMapStringToString::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Détermine le nombre actuel d’éléments dans la table de hachage.|
|[CMapStringToString::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Obtient l’élément suivant pour l’itération.|
|[CMapStringToString :: est à obtenir](../../mfc/reference/cmapstringtoob-class.md#getsize)|Retourne le nombre d’éléments de ce plan.|
|[CMapStringToString::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Retourne la position du premier élément.|
|[CMapStringToString::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Calcule la valeur de hachage d’une clé spécifiée.|
|[CMapStringToString::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Initialise la table de hachage.|
|[CMapStringToString :: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Teste la condition de mappage vide (aucun élément).|
|[CMapStringToString :: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Recherche un pointeur void basé sur la clé de pointeur void. La valeur du pointeur, pas l’entité vers laquelle elle pointe, est utilisée pour la comparaison de clés.|
|[CMapStringToString :: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Retourne une référence à la clé associée à la valeur de clé spécifiée.|
|[CMapStringToString ::P GetFirstAssoc](#pgetfirstassoc)|Obtient un pointeur vers le premier `CString` dans le mappage.|
|[CMapStringToString ::P GetNextAssoc](#pgetnextassoc)|Obtient un pointeur vers le suivant `CString` pour l’itération.|
|[CMapStringToString ::P la recherche](#plookup)|Retourne un pointeur vers un `CString` dont la valeur correspond à la valeur spécifiée.|
|[CMapStringToString :: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Supprime tous les éléments de ce mappage.|
|[CMapStringToString::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Supprime un élément spécifié par une clé.|
|[CMapStringToString :: SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Insère un élément dans la classe Map ; remplace un élément existant si une clé correspondante est trouvée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CMapStringToString ::, opérateur \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Insère un élément dans la classe Map : substitution d’opérateur pour `SetAt` .|

## <a name="remarks"></a>Notes

`CMapStringToString` incorpore la macro `IMPLEMENT_SERIAL` pour prendre en charge la sérialisation et le vidage de ses éléments. Chaque élément est sérialisé à son tour si un mappage est stocké dans une archive, soit avec l’opérateur d’insertion () surchargé, soit **<<** avec la `Serialize` fonction membre.

Si vous avez besoin d’un vidage d' `CString` -  `CString` éléments individuels, vous devez définir la profondeur du contexte de vidage sur une valeur supérieure ou égale à 1.

Lorsqu’un `CMapStringToString` objet est supprimé ou que ses éléments sont supprimés, les `CString` objets sont supprimés, le cas échéant.

Pour plus d’informations sur `CMapStringToString` , consultez l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcoll. h

## <a name="cmapstringtostringcpair"></a><a name="cpair"></a> CMapStringToString::CPair

Contient une valeur de clé et la valeur de l’objet String associé.

### <a name="remarks"></a>Notes

Il s’agit d’une structure imbriquée dans la classe [CMapStringToString](../../mfc/reference/cmapstringtostring-class.md).

La structure est composée de deux champs :

- `key` Valeur réelle du type de clé.

- `value` Valeur de l’objet associé.

Il est utilisé pour stocker les valeurs de retour de [CMapStringToString ::P Lookup](#plookup), [CMapStringToString ::P getfirstassoc](#pgetfirstassoc)et [CMapStringToString ::P GetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Exemple

  Pour obtenir un exemple d’utilisation, consultez l’exemple pour [CMapStringToString ::P Lookup](#plookup).

## <a name="cmapstringtostringpgetfirstassoc"></a><a name="pgetfirstassoc"></a> CMapStringToString ::P GetFirstAssoc

Retourne la première entrée de l’objet Map.

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la première entrée dans le mappage ; consultez [CMapStringToString :: CPair](#cpair). Si le mappage est vide, la valeur est NULL.

### <a name="remarks"></a>Notes

Appelez cette fonction pour retourner un pointeur vers le premier élément de l’objet Map.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

## <a name="cmapstringtostringpgetnextassoc"></a><a name="pgetnextassoc"></a> CMapStringToString ::P GetNextAssoc

Récupère l’élément de mappage pointé par *pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>Paramètres

*pAssoc*<br/>
Pointe vers une entrée de mappage retournée par un appel [PGetNextAssoc](#pgetnextassoc) ou [PGetFirstAssoc](#pgetfirstassoc) précédent.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’entrée suivante dans le mappage ; consultez [CMapStringToString :: CPair](#cpair). Si l’élément est le dernier dans le mappage, la valeur est NULL.

### <a name="remarks"></a>Notes

Appelez cette méthode pour itérer au sein de tous les éléments de la classe Map. Récupère le premier élément avec un appel à `PGetFirstAssoc` , puis itère au sein de la carte avec des appels successifs à `PGetNextAssoc` .

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CMapStringToString ::P getfirstassoc](#pgetfirstassoc).

## <a name="cmapstringtostringplookup"></a><a name="plookup"></a> CMapStringToString ::P la recherche

Recherche la valeur mappée à une clé donnée.

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Pointeur vers la clé de l’élément à rechercher.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la clé spécifiée.

### <a name="remarks"></a>Notes

Appelez cette méthode pour rechercher un élément cartographique avec une clé qui correspond exactement à la clé donnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple de collecte MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
