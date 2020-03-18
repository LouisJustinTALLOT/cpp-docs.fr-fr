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
ms.openlocfilehash: b56e9052533269ba62d248312f07ac16db71bf4a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418537"
---
# <a name="cmapstringtoob-class"></a>CMapStringToOb, classe

Classe de collection de dictionnaires qui mappe des objets `CString` uniques à des pointeurs `CObject` .

## <a name="syntax"></a>Syntaxe

```
class CMapStringToOb : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CMapStringToOb::CMapStringToOb](#cmapstringtoob)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CMapStringToOb :: GetCount](#getcount)|Retourne le nombre d’éléments de ce plan.|
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|Détermine le nombre actuel d’éléments dans la table de hachage.|
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|Obtient l’élément suivant pour l’itération.|
|[CMapStringToOb :: est à obtenir](#getsize)|Retourne le nombre d’éléments de ce plan.|
|[CMapStringToOb::GetStartPosition](#getstartposition)|Retourne la position du premier élément.|
|[CMapStringToOb::HashKey](#hashkey)|Calcule la valeur de hachage d’une clé spécifiée.|
|[CMapStringToOb::InitHashTable](#inithashtable)|Initialise la table de hachage.|
|[CMapStringToOb :: IsEmpty](#isempty)|Teste la condition de mappage vide (aucun élément).|
|[CMapStringToOb :: Lookup](#lookup)|Recherche un pointeur void basé sur la clé de pointeur void. La valeur du pointeur, pas l’entité vers laquelle elle pointe, est utilisée pour la comparaison de clés.|
|[CMapStringToOb :: LookupKey](#lookupkey)|Retourne une référence à la clé associée à la valeur de clé spécifiée.|
|[CMapStringToOb :: RemoveAll](#removeall)|Supprime tous les éléments de ce mappage.|
|[CMapStringToOb::RemoveKey](#removekey)|Supprime un élément spécifié par une clé.|
|[CMapStringToOb :: SetAt](#setat)|Insère un élément dans la classe Map ; remplace un élément existant si une clé correspondante est trouvée.|

### <a name="public-operators"></a>Opérateurs publics

|Name|Description|
|----------|-----------------|
|[CMapStringToOb :: Operator \[ \]](#operator_at)|Insère un élément dans la classe Map : la substitution d’opérateur pour `SetAt`.|

## <a name="remarks"></a>Notes

Une fois que vous avez inséré un `CString`- `CObject*` paire (élément) dans la carte, vous pouvez récupérer ou supprimer efficacement la paire à l’aide d’une valeur de chaîne ou de `CString` comme clé. Vous pouvez également effectuer une itération sur tous les éléments de la carte.

Une variable de type POSITION est utilisée pour un autre accès aux entrées dans toutes les variations de la carte. Vous pouvez utiliser une POSITION pour « mémoriser » une entrée et pour effectuer une itération au sein de la carte. Vous pensez peut-être que cette itération est séquentielle par valeur de clé ; ce n’est pas le fait. La séquence des éléments récupérés est indéterminée.

`CMapStringToOb` incorpore la macro `IMPLEMENT_SERIAL` pour prendre en charge la sérialisation et le vidage de ses éléments. Chaque élément est sérialisé à son tour si un mappage est stocké dans une archive, soit avec l’opérateur d’insertion surchargé ( **<<** ), soit avec la fonction membre `Serialize`.

Si vous avez besoin d’un vidage des diagnostics des éléments individuels dans le mappage (la valeur `CString` et le contenu `CObject`), vous devez définir la profondeur du contexte de vidage sur une valeur supérieure ou égale à 1.

Quand un objet `CMapStringToOb` est supprimé ou que ses éléments sont supprimés, les objets `CString` et les pointeurs `CObject` sont supprimés. Les objets référencés par les pointeurs `CObject` ne sont pas détruits.

La dérivation de classe de mappage est similaire à la dérivation de liste. Consultez les [Collections](../../mfc/collections.md) d’articles pour obtenir une illustration de la dérivation d’une classe de liste à usage spécial.

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcoll. h

##  <a name="cmapstringtoob"></a>CMapStringToOb::CMapStringToOb

Construit une carte de `CString`à `CObject*` vide.

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Paramètres

*nBlockSize*<br/>
Spécifie la granularité d’allocation de mémoire pour l’extension de la carte.

### <a name="remarks"></a>Notes

À mesure que la carte se développe, la mémoire est allouée en unités d’entrées *nBlockSize* .

Le tableau suivant présente d’autres fonctions membres similaires à `CMapStringToOb:: CMapStringToOb`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr (INT_PTR** `nBlockSize` **= 10);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord (INT_PTR** `nBlockSize` **= 10);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr (INT_PTR** `nBlockSize` **= 10);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString (INT_PTR** `nBlockSize` **= 10);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb (INT_PTR** `nBlockSize` **= 10);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr (INT_PTR** `nBlockSize` **= 10);**|

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir une liste de la classe `CAge` utilisée dans tous les exemples de collection.

##  <a name="getcount"></a>CMapStringToOb :: GetCount

Détermine le nombre d’éléments dans la carte.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans ce mappage.

### <a name="remarks"></a>Notes

Le tableau suivant présente d’autres fonctions membres similaires à `CMapStringToOb::GetCount`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount () const ;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount () const ;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount () const ;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount () const ;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount () const ;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount () const ;**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir une liste de la classe `CAge` utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

##  <a name="gethashtablesize"></a>CMapStringToOb::GetHashTableSize

Détermine le nombre actuel d’éléments dans la table de hachage.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’éléments dans la table de hachage.

### <a name="remarks"></a>Notes

Le tableau suivant présente d’autres fonctions membres similaires à `CMapStringToOb::GetHashTableSize`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT GetHashTableSize () const ;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT GetHashTableSize () const ;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT GetHashTableSize () const ;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT GetHashTableSize () const ;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT GetHashTableSize () const ;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT GetHashTableSize () const ;**|

##  <a name="getnextassoc"></a>CMapStringToOb::GetNextAssoc

Récupère l’élément cartographique sur *rNextPosition*, puis met à jour *rNextPosition* pour faire référence à l’élément suivant dans la classe Map.

```
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Paramètres

*rNextPosition*<br/>
Spécifie une référence à une valeur de POSITION retournée par un appel `GetNextAssoc` ou `GetStartPosition` précédent.

*rKey*<br/>
Spécifie la clé retournée de l’élément récupéré (une chaîne).

*rValue*<br/>
Spécifie la valeur retournée par l’élément récupéré (pointeur `CObject`). Pour plus d’informations sur ce paramètre, consultez la section Notes.

### <a name="remarks"></a>Notes

Cette fonction est particulièrement utile pour itérer au sein de tous les éléments de la classe Map. Notez que la séquence de position n’est pas nécessairement la même que la séquence de valeur de clé.

Si l’élément récupéré est le dernier dans le mappage, la nouvelle valeur de *rNextPosition* est définie sur null.

Pour le paramètre *rValue* , veillez à effectuer le cast de votre type d’objet en **CObject\*&** , ce que le compilateur requiert, comme illustré dans l’exemple suivant :

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

Ce n’est pas le cas de `GetNextAssoc` pour les mappages basés sur des modèles.

Le tableau suivant présente d’autres fonctions membres similaires à `CMapStringToOb::GetNextAssoc`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, void\*&** *RKEY* **, void\*&** *rValue* **) const ;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, void\*&** *RKEY* **, Word &** *rValue* **) const ;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, CString &** *RKEY* **, void\*&** *rValue* **) const ;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, cstring &** *RKEY* **, CString &** *rValue* **) const ;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, WORD &** *RKEY* **, CObject\*&** *rValue* **) const ;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, WORD &** *RKEY* **, void\*&** *rValue* **) const ;**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir une liste de la classe `CAge` utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

Les résultats de ce programme sont les suivants :

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

##  <a name="getsize"></a>CMapStringToOb :: est à obtenir

Retourne le nombre d’éléments cartographiques.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans la carte.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre d’éléments dans la classe Map.

Le tableau suivant présente d’autres fonctions membres similaires à `CMapStringToOb::GetSize`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTRs () const ;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTRs () const ;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTRs () const ;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTRs () const ;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTRs () const ;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTRs () const ;**|

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

##  <a name="getstartposition"></a>CMapStringToOb::GetStartPosition

Démarre une itération de mappage en retournant une valeur de POSITION qui peut être passée à un appel de `GetNextAssoc`.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de POSITION qui indique une position de départ pour itérer la carte ; ou NULL si le mappage est vide.

### <a name="remarks"></a>Notes

La séquence d’itération n’est pas prévisible ; par conséquent, le « premier élément du mappage » n’a pas d’importance particulière.

Le tableau suivant présente d’autres fonctions membres similaires à `CMapStringToOb::GetStartPosition`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POSITION GetStartPosition () const ;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POSITION GetStartPosition () const ;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**POSITION GetStartPosition () const ;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**POSITION GetStartPosition () const ;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POSITION GetStartPosition () const ;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POSITION GetStartPosition () const ;**|

### <a name="example"></a>Exemple

Consultez l’exemple de [CMapStringToOb :: GetNextAssoc](#getnextassoc).

##  <a name="hashkey"></a>CMapStringToOb::HashKey

Calcule la valeur de hachage d’une clé spécifiée.

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé dont la valeur de hachage doit être calculée.

### <a name="return-value"></a>Valeur de retour

Valeur de hachage de la clé

### <a name="remarks"></a>Notes

Le tableau suivant présente d’autres fonctions membres similaires à `CMapStringToOb::HashKey`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Uint HashKey (void** <strong>\*</strong> `key` **) const ;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Uint HashKey (void** <strong>\*</strong> `key` **) const ;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Uint HashKey (LPCTSTR** `key` **) const ;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Uint HashKey (LPCTSTR** `key` **) const ;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Uint HashKey (mot** `key` **) const ;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Uint HashKey (mot** `key` **) const ;**|

##  <a name="inithashtable"></a>CMapStringToOb::InitHashTable

Initialise la table de hachage.

```
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>Paramètres

*hashSize*<br/>
Nombre d’entrées dans la table de hachage.

*bAllocNow*<br/>
Si la valeur est TRUE, alloue la table de hachage lors de l’initialisation ; dans le cas contraire, la table est allouée.

### <a name="remarks"></a>Notes

Pour des performances optimales, la taille de la table de hachage doit être un nombre premier. Pour réduire les collisions, la taille doit être d’environ 20 pour cent plus grande que le plus grand jeu de données prévu.

Le tableau suivant présente d’autres fonctions membres similaires à `CMapStringToOb::InitHashTable`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|

##  <a name="isempty"></a>CMapStringToOb :: IsEmpty

Détermine si le mappage est vide.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si ce mappage ne contient aucun élément ; Sinon, 0.

### <a name="example"></a>Exemple

Consultez l’exemple pour [RemoveAll](#removeall).

### <a name="remarks"></a>Notes

Le tableau suivant présente d’autres fonctions membres similaires à **CMapStringToOb :: IsEmpty**.

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty () const ;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty () const ;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty () const ;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty () const ;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty () const ;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty () const ;**|

##  <a name="lookup"></a>CMapStringToOb :: Lookup

Retourne un pointeur de `CObject` basé sur une valeur de `CString`.

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la clé de chaîne qui identifie l’élément à rechercher.

*rValue*<br/>
Spécifie la valeur retournée à partir de l’élément recherché.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’élément a été trouvé ; Sinon, 0.

### <a name="remarks"></a>Notes

`Lookup` utilise un algorithme de hachage pour trouver rapidement l’élément cartographique avec une clé qui correspond exactement (valeur `CString`).

Le tableau suivant présente d’autres fonctions membres similaires à `CMapStringToOb::LookUp`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Bool Lookup (void** <strong>\*</strong> `key` **, void\*&** `rValue` **) const ;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Bool Lookup (void** <strong>\*</strong> `key` **, mot &** `rValue` **) const ;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Bool Lookup (LPCTSTR** `key` **, void\*&** `rValue` **) const ;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Bool Lookup (LPCTSTR** `key` **, CString &** `rValue` **) const ;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Bool Lookup (mot** `key` **, CObject\*&** `rValue` **) const ;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Bool Lookup (mot** `key` **, void\*&** `rValue` **) const ;**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir une liste de la classe `CAge` utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

##  <a name="lookupkey"></a>CMapStringToOb :: LookupKey

Retourne une référence à la clé associée à la valeur de clé spécifiée.

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la clé de chaîne qui identifie l’élément à rechercher.

*rKey*<br/>
Référence à la clé associée.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la clé a été trouvée ; Sinon, 0.

### <a name="remarks"></a>Notes

L’utilisation d’une référence à une clé n’est pas sécurisée si elle est utilisée après que l’élément associé a été supprimé de la carte ou une fois que le mappage a été détruit.

Le tableau suivant présente d’autres fonctions membres similaires à `CMapStringToOb:: LookupKey`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Bool LookupKey (lpctstr** `key` **, LPCTSTR &** `rKey` **) const ;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Bool LookupKey (lpctstr** `key` **, LPCTSTR &** `rKey` **) const ;**|

##  <a name="operator_at"></a>CMapStringToOb :: Operator []

Substitution pratique de la fonction membre `SetAt`.

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>Valeur de retour

Référence à un pointeur vers un objet `CObject` ; ou NULL si le mappage est vide ou si la *clé* est hors limites.

### <a name="remarks"></a>Notes

Il peut donc être utilisé uniquement sur le côté gauche d’une instruction d’assignation (une l-value). S’il n’y a pas d’élément cartographique avec la clé spécifiée, un nouvel élément est créé.

Il n’y a aucun « côté droit » (r-value) équivalent à cet opérateur, car il est possible qu’une clé ne soit pas trouvée dans le mappage. Utilisez la fonction membre `Lookup` pour la récupération d’élément.

Le tableau suivant présente d’autres fonctions membres similaires à `CMapStringToOb::operator []`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>void\*& opérateur\[] (void \*</strong> `key` **\);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD & operator\[] (void** <strong>\*</strong> `key` **\);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& opérateur\[] (lpctstr** `key` **\);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString & opérateur\[] (lpctstr** `key` **\);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& opérateur\[] (word** `key` **\);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& opérateur\[] (word** `key` **\);**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir une liste de la classe `CAge` utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

Les résultats de ce programme sont les suivants :

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

##  <a name="removeall"></a>CMapStringToOb :: RemoveAll

Supprime tous les éléments de ce mappage et détruit les objets clés de `CString`.

```
void RemoveAll();
```

### <a name="remarks"></a>Notes

Les objets `CObject` référencés par chaque clé ne sont pas détruits. La fonction `RemoveAll` peut provoquer des fuites de mémoire si vous ne vous assurez pas que les objets référencés `CObject` sont détruits.

La fonction fonctionne correctement si le mappage est déjà vide.

Le tableau suivant présente d’autres fonctions membres similaires à `CMapStringToOb::RemoveAll`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll ();**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll ();**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll ();**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll ();**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll ();**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll ();**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir une liste de la classe `CAge` utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

##  <a name="removekey"></a>CMapStringToOb::RemoveKey

Recherche l’entrée de mappage correspondant à la clé fournie. puis, si la clé est trouvée, supprime l’entrée.

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la chaîne utilisée pour la recherche de mappage.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’entrée a été trouvée et supprimée avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Cela peut provoquer des fuites de mémoire si l’objet `CObject` n’est pas supprimé ailleurs.

Le tableau suivant présente d’autres fonctions membres similaires à `CMapStringToOb::RemoveKey`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Bool RemoveKey (void** <strong>\*</strong> `key` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Bool RemoveKey (void** <strong>\*</strong> `key` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Bool RemoveKey (LPCTSTR** `key` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Bool RemoveKey (LPCTSTR** `key` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Bool RemoveKey (mot** `key` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Bool RemoveKey (mot** `key` **);**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir une liste de la classe `CAge` utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

Les résultats de ce programme sont les suivants :

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

##  <a name="setat"></a>CMapStringToOb :: SetAt

Le principal moyen d’insérer un élément dans une classe Map.

```
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la chaîne qui est la clé du nouvel élément.

*newValue*<br/>
Spécifie le pointeur `CObject` qui est la valeur du nouvel élément.

### <a name="remarks"></a>Notes

Tout d’abord, la clé est recherchée. Si la clé est trouvée, la valeur correspondante est modifiée ; dans le cas contraire, un nouvel élément key-value est créé.

Le tableau suivant présente d’autres fonctions membres similaires à `CMapStringToOb::SetAt`.

|Classe|Fonction membre|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt (void** <strong>\*</strong> `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt (void** <strong>\*</strong> `key` **, Word** `newValue` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt (LPCTSTR** `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt (lpctstr** `key` **, LPCTSTR** `newValue` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt (WORD** `key` **, CObject** <strong>\*</strong> `newValue` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt (mot** `key` **, void** <strong>\*</strong> `newValue` **);**|

### <a name="example"></a>Exemple

Consultez [CObList :: CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir une liste de la classe `CAge` utilisée dans tous les exemples de collection.

[!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]

Les résultats de ce programme sont les suivants :

```Output
before Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $493C 11
[Bart] = a CAge at $4654 13
after Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $49C0 12
[Bart] = a CAge at $4654 13
```

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr, classe](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord, classe](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapStringToPtr, classe](../../mfc/reference/cmapstringtoptr-class.md)<br/>
[CMapStringToString, classe](../../mfc/reference/cmapstringtostring-class.md)<br/>
[CMapWordToOb, classe](../../mfc/reference/cmapwordtoob-class.md)<br/>
[CMapWordToPtr, classe](../../mfc/reference/cmapwordtoptr-class.md)
