---
title: CMapWordToPtr, classe
ms.date: 11/04/2016
f1_keywords:
- CMapWordToPtr
- AFXCOLL/CMapWordToPtr
- AFXCOLL/CMapWordToPtr::CMapWordToPtr
- AFXCOLL/CMapWordToPtr::GetCount
- AFXCOLL/CMapWordToPtr::GetHashTableSize
- AFXCOLL/CMapWordToPtr::GetNextAssoc
- AFXCOLL/CMapWordToPtr::GetSize
- AFXCOLL/CMapWordToPtr::GetStartPosition
- AFXCOLL/CMapWordToPtr::HashKey
- AFXCOLL/CMapWordToPtr::InitHashTable
- AFXCOLL/CMapWordToPtr::IsEmpty
- AFXCOLL/CMapWordToPtr::Lookup
- AFXCOLL/CMapWordToPtr::LookupKey
- AFXCOLL/CMapWordToPtr::RemoveAll
- AFXCOLL/CMapWordToPtr::RemoveKey
- AFXCOLL/CMapWordToPtr::SetAt
helpviewer_keywords:
- CMapWordToPtr [MFC], CMapWordToPtr
- CMapWordToPtr [MFC], GetCount
- CMapWordToPtr [MFC], GetHashTableSize
- CMapWordToPtr [MFC], GetNextAssoc
- CMapWordToPtr [MFC], GetSize
- CMapWordToPtr [MFC], GetStartPosition
- CMapWordToPtr [MFC], HashKey
- CMapWordToPtr [MFC], InitHashTable
- CMapWordToPtr [MFC], IsEmpty
- CMapWordToPtr [MFC], Lookup
- CMapWordToPtr [MFC], LookupKey
- CMapWordToPtr [MFC], RemoveAll
- CMapWordToPtr [MFC], RemoveKey
- CMapWordToPtr [MFC], SetAt
ms.assetid: b204d87f-6427-43e1-93e3-a4b1bb41099f
ms.openlocfilehash: 71d79f9f57be2cdfe16c526bd50173a8ec3c5829
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442562"
---
# <a name="cmapwordtoptr-class"></a>CMapWordToPtr, classe

Prend en charge les mappages de pointeurs void indexés par des mots 16 bits.

## <a name="syntax"></a>Syntaxe

```
class CMapWordToPtr : public CObject
```

## <a name="members"></a>Membres

Les fonctions membres de `CMapWordToPtr` sont similaires aux fonctions membres de la classe [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Ainsi, vous pouvez utiliser la documentation de référence de `CMapStringToOb` pour connaître les spécificités des fonctions membres. Chaque fois que vous voyez un pointeur de `CObject` en tant que paramètre de fonction ou valeur de retour, substituez un pointeur à **void**. Chaque fois que vous voyez un `CString` ou un pointeur **const** vers un **caractère** comme paramètre de fonction ou valeur de retour, remplacez Word.

`BOOL CMapWordToPtr::Lookup( WORD <key>, void*& <rValue> ) const;`

par exemple, se traduit par

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CMapWordToPtr::CMapWordToPtr](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CMapWordToPtr :: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Retourne le nombre d’éléments de ce plan.|
|[CMapWordToPtr::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Détermine le nombre actuel d’éléments dans la table de hachage.|
|[CMapWordToPtr::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Obtient l’élément suivant pour l’itération.|
|[CMapWordToPtr :: est à obtenir](../../mfc/reference/cmapstringtoob-class.md#getsize)|Retourne le nombre d’éléments de ce plan.|
|[CMapWordToPtr::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Retourne la position du premier élément.|
|[CMapWordToPtr::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Calcule la valeur de hachage d’une clé spécifiée.|
|[CMapWordToPtr::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Initialise la table de hachage.|
|[CMapWordToPtr :: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Teste la condition de mappage vide (aucun élément).|
|[CMapWordToPtr :: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Recherche un pointeur void basé sur la clé de pointeur void. La valeur du pointeur, pas l’entité vers laquelle elle pointe, est utilisée pour la comparaison de clés.|
|[CMapWordToPtr :: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Retourne une référence à la clé associée à la valeur de clé spécifiée.|
|[CMapWordToPtr :: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Supprime tous les éléments de ce mappage.|
|[CMapWordToPtr::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Supprime un élément spécifié par une clé.|
|[CMapWordToPtr :: SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Insère un élément dans la classe Map ; remplace un élément existant si une clé correspondante est trouvée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[CMapWordToPtr :: Operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Insère un élément dans la classe Map : la substitution d’opérateur pour `SetAt`.|

## <a name="remarks"></a>Notes

`CMapWordToPtr` incorpore la macro IMPLEMENT_DYNAMIC pour prendre en charge l’accès aux types au moment de l’exécution et le vidage sur un objet `CDumpContext`. Si vous avez besoin d’un vidage d’éléments cartographiques individuels, vous devez définir la profondeur du contexte de vidage sur une valeur supérieure ou égale à 1.

Les mappages de mots à pointeurs ne peuvent pas être sérialisés.

Quand un objet `CMapWordToPtr` est supprimé ou que ses éléments sont supprimés, les mots et les pointeurs sont supprimés. Les entités référencées par les pointeurs ne sont pas supprimées.

Pour plus d’informations sur les `CMapWordToPtr`, consultez l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMapWordToPtr`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcoll. h

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
