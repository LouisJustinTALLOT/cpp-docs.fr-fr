---
title: CMapPtrToWord, classe
ms.date: 11/04/2016
f1_keywords:
- CMapPtrToWord
- AFXCOLL/CMapPtrToWord
- AFXCOLL/CMapPtrToWord::CMapPtrToWord
- AFXCOLL/CMapPtrToWord::GetCount
- AFXCOLL/CMapPtrToWord::GetHashTableSize
- AFXCOLL/CMapPtrToWord::GetNextAssoc
- AFXCOLL/CMapPtrToWord::GetSize
- AFXCOLL/CMapPtrToWord::GetStartPosition
- AFXCOLL/CMapPtrToWord::HashKey
- AFXCOLL/CMapPtrToWord::InitHashTable
- AFXCOLL/CMapPtrToWord::IsEmpty
- AFXCOLL/CMapPtrToWord::Lookup
- AFXCOLL/CMapPtrToWord::LookupKey
- AFXCOLL/CMapPtrToWord::RemoveAll
- AFXCOLL/CMapPtrToWord::RemoveKey
- AFXCOLL/CMapPtrToWord::SetAt
helpviewer_keywords:
- CMapPtrToWord [MFC], CMapPtrToWord
- CMapPtrToWord [MFC], GetCount
- CMapPtrToWord [MFC], GetHashTableSize
- CMapPtrToWord [MFC], GetNextAssoc
- CMapPtrToWord [MFC], GetSize
- CMapPtrToWord [MFC], GetStartPosition
- CMapPtrToWord [MFC], HashKey
- CMapPtrToWord [MFC], InitHashTable
- CMapPtrToWord [MFC], IsEmpty
- CMapPtrToWord [MFC], Lookup
- CMapPtrToWord [MFC], LookupKey
- CMapPtrToWord [MFC], RemoveAll
- CMapPtrToWord [MFC], RemoveKey
- CMapPtrToWord [MFC], SetAt
ms.assetid: 4631c6b6-d49f-49d9-adc0-1e0491e32d7b
ms.openlocfilehash: 254659a9f00ff7c0c27174cfbea4c131993150f3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223029"
---
# <a name="cmapptrtoword-class"></a>CMapPtrToWord, classe

Prend en charge les mappages de mots 16 bits indexés par des pointeurs void.

## <a name="syntax"></a>Syntaxe

```
class CMapPtrToWord : public CObject
```

## <a name="members"></a>Membres

Les fonctions membres de `CMapPtrToWord` sont similaires aux fonctions membres de la classe [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Ainsi, vous pouvez utiliser la documentation de référence de `CMapStringToOb` pour connaître les spécificités des fonctions membres. Partout où vous voyez un `CObject` pointeur sous la forme d’un paramètre de fonction ou d’une valeur de retour, remplacez Word. Partout où vous voyez un `CString` **`const`** pointeur ou vers **`char`** comme paramètre de fonction ou valeur de retour, substituez un pointeur à **`void`** .

`BOOL CMapPtrToWord::Lookup( const void* <key>, WORD& <rValue> ) const;`

par exemple, se traduit par

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMapPtrToWord::CMapPtrToWord](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMapPtrToWord :: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Retourne le nombre d’éléments de ce plan.|
|[CMapPtrToWord::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Détermine le nombre actuel d’éléments dans la table de hachage.|
|[CMapPtrToWord::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Obtient l’élément suivant pour l’itération.|
|[CMapPtrToWord :: est à obtenir](../../mfc/reference/cmapstringtoob-class.md#getsize)|Retourne le nombre d’éléments de ce plan.|
|[CMapPtrToWord::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Retourne la position du premier élément.|
|[CMapPtrToWord::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Calcule la valeur de hachage d’une clé spécifiée.|
|[CMapPtrToWord::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Initialise la table de hachage.|
|[CMapPtrToWord :: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Teste la condition de mappage vide (aucun élément).|
|[CMapPtrToWord :: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Recherche un pointeur void basé sur la clé de pointeur void. La valeur du pointeur, pas l’entité vers laquelle elle pointe, est utilisée pour la comparaison de clés.|
|[CMapPtrToWord :: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Retourne une référence à la clé associée à la valeur de clé spécifiée.|
|[CMapPtrToWord :: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Supprime tous les éléments de ce mappage.|
|[CMapPtrToWord::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Supprime un élément spécifié par une clé.|
|[CMapPtrToWord :: SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Insère un élément dans la classe Map ; remplace un élément existant si une clé correspondante est trouvée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CMapPtrToWord ::, opérateur \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Insère un élément dans la classe Map : substitution d’opérateur pour `SetAt` .|

## <a name="remarks"></a>Notes

`CMapWordToPtr`incorpore la macro IMPLEMENT_DYNAMIC pour prendre en charge l’accès aux types au moment de l’exécution et le vidage sur un `CDumpContext` objet. Si vous avez besoin d’un vidage d’éléments cartographiques individuels, vous devez définir la profondeur du contexte de vidage sur une valeur supérieure ou égale à 1.

Les mappages de pointeur vers Word ne peuvent pas être sérialisés.

Lorsqu’un `CMapPtrToWord` objet est supprimé ou que ses éléments sont supprimés, les pointeurs et les mots sont supprimés. Les entités référencées par les pointeurs clés ne sont pas supprimées.

Pour plus d’informations sur `CMapPtrToWord` , consultez l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToWord`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcoll. h

## <a name="see-also"></a>Voir aussi

[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
