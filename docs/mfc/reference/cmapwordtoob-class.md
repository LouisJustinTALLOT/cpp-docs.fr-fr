---
description: 'En savoir plus sur : classe CMapWordToOb'
title: CMapWordToOb, classe
ms.date: 11/04/2016
f1_keywords:
- CMapWordToOb
- AFXCOLL/CMapWordToOb
- AFXCOLL/CMapWordToOb::CMapWordToOb
- AFXCOLL/CMapWordToOb::GetCount
- AFXCOLL/CMapWordToOb::GetHashTableSize
- AFXCOLL/CMapWordToOb::GetNextAssoc
- AFXCOLL/CMapWordToOb::GetSize
- AFXCOLL/CMapWordToOb::GetStartPosition
- AFXCOLL/CMapWordToOb::HashKey
- AFXCOLL/CMapWordToOb::InitHashTable
- AFXCOLL/CMapWordToOb::IsEmpty
- AFXCOLL/CMapWordToOb::Lookup
- AFXCOLL/CMapWordToOb::LookupKey
- AFXCOLL/CMapWordToOb::RemoveAll
- AFXCOLL/CMapWordToOb::RemoveKey
- AFXCOLL/CMapWordToOb::SetAt
helpviewer_keywords:
- CMapWordToOb [MFC], CMapWordToOb
- CMapWordToOb [MFC], GetCount
- CMapWordToOb [MFC], GetHashTableSize
- CMapWordToOb [MFC], GetNextAssoc
- CMapWordToOb [MFC], GetSize
- CMapWordToOb [MFC], GetStartPosition
- CMapWordToOb [MFC], HashKey
- CMapWordToOb [MFC], InitHashTable
- CMapWordToOb [MFC], IsEmpty
- CMapWordToOb [MFC], Lookup
- CMapWordToOb [MFC], LookupKey
- CMapWordToOb [MFC], RemoveAll
- CMapWordToOb [MFC], RemoveKey
- CMapWordToOb [MFC], SetAt
ms.assetid: 9c9bcd76-456f-4cf9-b03c-dd28b49d5e4f
ms.openlocfilehash: da21902c3789f1547055baffae5650fcb6b8c789
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336711"
---
# <a name="cmapwordtoob-class"></a>CMapWordToOb, classe

Prend en charge les mappages de pointeurs `CObject` indexés par des mots 16 bits.

## <a name="syntax"></a>Syntaxe

```
class CMapWordToOb : public CObject
```

## <a name="members"></a>Membres

Les fonctions membres de `CMapWordToOb` sont similaires aux fonctions membres de la classe [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Ainsi, vous pouvez utiliser la documentation de référence de `CMapStringToOb` pour connaître les spécificités des fonctions membres. Partout où vous voyez un `CString` **`const`** pointeur ou vers **`char`** comme paramètre de fonction ou valeur de retour, remplacez Word.

`BOOL CMapWordToOb::Lookup( WORD <key>, CObject*& <rValue> ) const;`

par exemple, se traduit par

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMapWordToOb::CMapWordToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMapWordToOb :: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Retourne le nombre d’éléments de ce plan.|
|[CMapWordToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Détermine le nombre actuel d’éléments dans la table de hachage.|
|[CMapWordToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Obtient l’élément suivant pour l’itération.|
|[CMapWordToOb :: est à obtenir](../../mfc/reference/cmapstringtoob-class.md#getsize)|Retourne le nombre d’éléments de ce plan.|
|[CMapWordToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Retourne la position du premier élément.|
|[CMapWordToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Calcule la valeur de hachage d’une clé spécifiée.|
|[CMapWordToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Initialise la table de hachage.|
|[CMapWordToOb :: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Teste la condition de mappage vide (aucun élément).|
|[CMapWordToOb :: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Recherche un pointeur void basé sur la clé de pointeur void. La valeur du pointeur, pas l’entité vers laquelle elle pointe, est utilisée pour la comparaison de clés.|
|[CMapWordToOb :: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Retourne une référence à la clé associée à la valeur de clé spécifiée.|
|[CMapWordToOb :: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Supprime tous les éléments de ce mappage.|
|[CMapWordToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Supprime un élément spécifié par une clé.|
|[CMapWordToOb :: SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Insère un élément dans la classe Map ; remplace un élément existant si une clé correspondante est trouvée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CMapWordToOb ::, opérateur \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Insère un élément dans la classe Map : substitution d’opérateur pour `SetAt` .|

## <a name="remarks"></a>Notes

`CMapWordToOb` incorpore la macro IMPLEMENT_SERIAL pour prendre en charge la sérialisation et le vidage de ses éléments. Chaque élément est sérialisé à son tour si un mappage est stocké dans une archive, soit avec l’opérateur d’insertion () surchargé, soit **<<** avec la `Serialize` fonction membre.

Si vous avez besoin d’un vidage d’éléments de mots individuels `CObject` , vous devez définir la profondeur du contexte de vidage sur une valeur supérieure ou égale à 1.

Lorsqu’un `CMapWordToOb` objet est supprimé ou que ses éléments sont supprimés, les `CObject` pointeurs sont supprimés. Les objets référencés par les `CObject` pointeurs ne sont pas détruits.

Pour plus d’informations sur `CMapWordToOb` , consultez l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMapWordToOb`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcoll. h

## <a name="see-also"></a>Voir aussi

[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
