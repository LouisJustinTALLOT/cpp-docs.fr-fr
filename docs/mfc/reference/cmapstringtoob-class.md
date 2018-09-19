---
title: CMapStringToOb, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0d233bd9ad35eabe5782e58e186f0033b8cf816
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085769"
---
# <a name="cmapstringtoob-class"></a>CMapStringToOb (classe)
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
|[CMapStringToOb::GetCount](#getcount)|Retourne le nombre d’éléments dans ce mappage.|  
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|Détermine le nombre actuel d’éléments dans la table de hachage.|  
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|Obtient l’élément suivant pour une itération.|  
|[CMapStringToOb::GetSize](#getsize)|Retourne le nombre d’éléments dans ce mappage.|  
|[CMapStringToOb::GetStartPosition](#getstartposition)|Retourne la position du premier élément.|  
|[CMapStringToOb::HashKey](#hashkey)|Calcule la valeur de hachage d’une clé spécifiée.|  
|[CMapStringToOb::InitHashTable](#inithashtable)|Initialise la table de hachage.|  
|[CMapStringToOb::IsEmpty](#isempty)|Vérifie si la condition vide-map (pas d’éléments).|  
|[CMapStringToOb::Lookup](#lookup)|Recherche un pointeur void selon la clé du pointeur void. La valeur de pointeur, pas l’entité qu’il pointe vers, est utilisée pour la comparaison de clés.|  
|[CMapStringToOb::LookupKey](#lookupkey)|Retourne une référence à la clé associée à la valeur de clé spécifiée.|  
|[CMapStringToOb::RemoveAll](#removeall)|Supprime tous les éléments de ce mappage.|  
|[CMapStringToOb::RemoveKey](#removekey)|Supprime un élément spécifié par une clé.|  
|[CMapStringToOb::SetAt](#setat)|Insère un élément dans l’objet map. remplace un élément existant si une clé correspondante est trouvée.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMapStringToOb::operator [ ]](#operator_at)|Insère un élément dans la classe map, substitution d’opérateur pour `SetAt`.|  
  
## <a name="remarks"></a>Notes  
 Une fois que vous avez inséré un `CString` -  `CObject*` paire (élément) dans la classe map, vous pouvez efficacement récupérer ou supprimer la paire à l’aide d’une chaîne ou un `CString` valeur en tant que clé. Vous pouvez également itérer sur tous les éléments dans le mappage.  
  
 Une variable de type POSITION est utilisée pour l’accès d’entrée autre dans toutes les variations de la carte. Vous pouvez utiliser une POSITION à une entrée « mémoriser » et à effectuer une itération dans la carte. Vous pourriez penser que cette itération est séquentielle par valeur de clé ; Il n’est pas le cas. La séquence des éléments récupérés est indéterminée.  
  
 `CMapStringToOb` incorpore la macro `IMPLEMENT_SERIAL` pour prendre en charge la sérialisation et le vidage de ses éléments. Chaque élément est sérialisé à son tour, si un mappage est stocké dans une archive, soit avec l’insertion surchargée ( **<<**) opérateur ou avec le `Serialize` fonction membre.  
  
 Si vous avez besoin d’un vidage de diagnostic des éléments individuels dans le mappage (le `CString` valeur et le `CObject` contenu), vous devez définir la profondeur du contexte de vidage à 1 ou supérieur.  
  
 Quand un `CMapStringToOb` objet est supprimé, ou lorsque ses éléments sont supprimés, le `CString` objets et le `CObject` pointeurs sont supprimés. Les objets référencés par le `CObject` des pointeurs ne sont pas détruits.  
  
 Dérivation de classe Map est similaire à la dérivation de la liste. Consultez l’article [Collections](../../mfc/collections.md) pour obtenir une illustration de la dérivation d’une classe de liste de spécial.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToOb`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcoll.h  
  
##  <a name="cmapstringtoob"></a>  CMapStringToOb::CMapStringToOb  
 Construit un vide `CString`- au - `CObject*` carte.  
  
```  
CMapStringToOb(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Paramètres  
 *nBlockSize*  
 Spécifie la granularité d’allocation de mémoire pour l’extension de la carte.  
  
### <a name="remarks"></a>Notes  
 Comme la carte s’accroît, la mémoire est allouée en unités de *nBlockSize* entrées.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CMapStringToOb:: CMapStringToOb`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr( INT_PTR** `nBlockSize` **= 10 );**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord( INT_PTR** `nBlockSize` **= 10 );**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr( INT_PTR** `nBlockSize` **= 10 );**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString( INT_PTR** `nBlockSize` **= 10 );**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb( INT_PTR** `nBlockSize` **= 10 );**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr( INT_PTR** `nBlockSize` **= 10 );**|  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]  
  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
##  <a name="getcount"></a>  CMapStringToOb::GetCount  
 Détermine le nombre d’éléments dans le mappage.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans ce mappage.  
  
### <a name="remarks"></a>Notes  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CMapStringToOb::GetCount`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR const ; (GetCount)**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR const ; (GetCount)**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR const ; (GetCount)**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR const ; (GetCount)**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR const ; (GetCount)**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR const ; (GetCount)**|  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]  
  
##  <a name="gethashtablesize"></a>  CMapStringToOb::GetHashTableSize  
 Détermine le nombre actuel d’éléments dans la table de hachage.  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nombre d’éléments dans la table de hachage.  
  
### <a name="remarks"></a>Notes  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CMapStringToOb::GetHashTableSize`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT const ; (GetHashTableSize)**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT const ; (GetHashTableSize)**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT const ; (GetHashTableSize)**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT const ; (GetHashTableSize)**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT const ; (GetHashTableSize)**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT const ; (GetHashTableSize)**|  
  
##  <a name="getnextassoc"></a>  CMapStringToOb::GetNextAssoc  
 Récupère l’élément de carte à *rNextPosition*, puis met à jour *rNextPosition* pour faire référence à l’élément suivant dans la carte.  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,  
    CString& rKey,  
    CObject*& rValue) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *rNextPosition*  
 Spécifie une référence à une valeur POSITION retournée par une précédente `GetNextAssoc` ou `GetStartPosition` appeler.  
  
 *rKey*  
 Spécifie la clé retournée de l’élément récupéré (une chaîne).  
  
 *rValue*  
 Spécifie la valeur retournée de l’élément récupéré (un `CObject` pointeur). Consultez la section Notes pour plus d’informations sur ce paramètre.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est particulièrement utile pour itérer tous les éléments dans le mappage. Notez que la séquence de position n’est pas nécessairement identique à la séquence de la valeur de clé.  
  
 Si l’élément récupéré est le dernier dans le mappage, puis la nouvelle valeur de *rNextPosition* est définie sur NULL.  
  
 Pour le *rValue* paramètre, veillez à effectuer un cast de votre type d’objet à **CObject\*&**, qui est ce que le compilateur exige, comme indiqué dans l’exemple suivant :  
  
 [!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]  
  
 Cela n’est pas vrai pour `GetNextAssoc` pour les cartes basées sur des modèles.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CMapStringToOb::GetNextAssoc`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, void\* &**  *rKey* **, void\* &**  *rValue* **) const ;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, void\*&** *rKey* **, WORD&** *rValue* **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, CString &** *rKey* **, void\* &**  *rValue* **) const ;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, CString &** *rKey* **, CString &** *rValue* **) const ;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, WORD &** *rKey* **, CObject\* &**  *rValue* **) const ;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, WORD &** *rKey* **, void\* &**  *rValue* **) const ;**|  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]  
  
 Les résultats à partir de ce programme sont les suivantes :  
  
```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```
  
##  <a name="getsize"></a>  CMapStringToOb::GetSize  
 Retourne le nombre d’éléments de mappage.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans le mappage.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour récupérer le nombre d’éléments dans le mappage.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CMapStringToOb::GetSize`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetSize () const ;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetSize () const ;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetSize () const ;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetSize () const ;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetSize () const ;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetSize () const ;**|  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]  
  
##  <a name="getstartposition"></a>  CMapStringToOb::GetStartPosition  
 Démarre une itération de la carte en retournant une valeur POSITION qui peut être passée à un `GetNextAssoc` appeler.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur POSITION qui indique une position de départ pour une itération de la carte ; ou NULL si le mappage est vide.  
  
### <a name="remarks"></a>Notes  
 La séquence d’itération n’est pas prévisible ; Par conséquent, le « premier élément dans le mappage » n’a aucun signification particulière.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CMapStringToOb::GetStartPosition`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POSITION const ; (GetStartPosition)**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POSITION const ; (GetStartPosition)**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**POSITION const ; (GetStartPosition)**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**POSITION const ; (GetStartPosition)**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POSITION const ; (GetStartPosition)**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POSITION const ; (GetStartPosition)**|  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CMapStringToOb::GetNextAssoc](#getnextassoc).  
  
##  <a name="hashkey"></a>  CMapStringToOb::HashKey  
 Calcule la valeur de hachage d’une clé spécifiée.  
  
```  
UINT HashKey(LPCTSTR key) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *key*  
 Clé dont la valeur hachage doit être calculé.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur de hachage de la clé  
  
### <a name="remarks"></a>Notes  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CMapStringToOb::HashKey`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey (void** <strong>\*</strong> `key` **) const ;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey (void** <strong>\*</strong> `key` **) const ;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey (LPCTSTR** `key` **) const ;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey (LPCTSTR** `key` **) const ;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT HashKey (WORD** `key` **) const ;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT HashKey (WORD** `key` **) const ;**|  
  
##  <a name="inithashtable"></a>  CMapStringToOb::InitHashTable  
 Initialise la table de hachage.  
  
```  
void InitHashTable(
    UINT hashSize,  
    BOOL bAllocNow = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *hashSize*  
 Nombre d’entrées dans la table de hachage.  
  
 *bAllocNow*  
 Si la valeur est TRUE, alloue de la table de hachage lors de l’initialisation ; Sinon, le tableau est alloué lorsque nécessaire.  
  
### <a name="remarks"></a>Notes  
 Pour de meilleures performances, la taille de table de hachage doit être un nombre premier. Pour réduire les collisions, la taille doit être à peu près supérieur le plus grand jeu de données anticipé à 20 pour cent.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CMapStringToOb::InitHashTable`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE );**|  
  
##  <a name="isempty"></a>  CMapStringToOb::IsEmpty  
 Détermine si le mappage est vide.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si ce mappage ne contient aucun élément ; sinon 0.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [RemoveAll](#removeall).  
  
### <a name="remarks"></a>Notes  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux **CMapStringToOb :: IsEmpty**.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty () const ;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty () const ;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty () const ;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty () const ;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty () const ;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty () const ;**|  
  
##  <a name="lookup"></a>  CMapStringToOb::Lookup  
 Retourne un `CObject` pointeur selon un `CString` valeur.  
  
```  
BOOL Lookup(
    LPCTSTR key,  
    CObject*& rValue) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *key*  
 Spécifie la clé de chaîne qui identifie l’élément à rechercher.  
  
 *rValue*  
 Spécifie la valeur retournée à partir de l’élément recherché.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément a été trouvé ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 `Lookup` utilise un algorithme de hachage pour trouver rapidement l’élément de carte avec une clé qui correspond exactement ( `CString` valeur).  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CMapStringToOb::LookUp`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Recherche de BOOL (void** <strong>\*</strong> `key` **, void\* &**  `rValue` **) const ;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Recherche de BOOL (void** <strong>\*</strong> `key` **, WORD &** `rValue` **) const ;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Recherche de BOOL (LPCTSTR** `key` **, void\* &**  `rValue` **) const ;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Recherche de BOOL (LPCTSTR** `key` **, CString &** `rValue` **) const ;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Recherche de BOOL (mot** `key` **, CObject\* &**  `rValue` **) const ;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Recherche de BOOL (mot** `key` **, void\* &**  `rValue` **) const ;**|  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]  
  
##  <a name="lookupkey"></a>  CMapStringToOb::LookupKey  
 Retourne une référence à la clé associée à la valeur de clé spécifiée.  
  
```  
BOOL LookupKey(
    LPCTSTR key,  
    LPCTSTR& rKey) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *key*  
 Spécifie la clé de chaîne qui identifie l’élément à rechercher.  
  
 *rKey*  
 La référence à la clé associée.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la clé a été trouvée ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Il est risqué d’à l’aide d’une référence à une clé si utilisée une fois que l’élément associé a été supprimé de la carte ou une fois que la carte a été détruite.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CMapStringToOb:: LookupKey`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey (LPCTSTR** `key` **, LPCTSTR &** `rKey` **) const ;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey (LPCTSTR** `key` **, LPCTSTR &** `rKey` **) const ;**|  
  
##  <a name="operator_at"></a>  CMapStringToOb::operator [ ]  
 Une alternative pratique à la `SetAt` fonction membre.  
  
```  
CObject*& operator[ ](lpctstr key);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à un pointeur vers un `CObject` objet ; ou NULL si le mappage est vide ou *clé* est hors limites.  
  
### <a name="remarks"></a>Notes  
 Par conséquent, il peut être utilisé uniquement sur le côté gauche d’une instruction d’assignation (une l-value). S’il n’existe aucun élément de mappage avec la clé spécifiée, un nouvel élément est créé.  
  
 Aucun (r-value) « droite » n’est équivalent à cet opérateur, car il est possible qu’une clé peut être introuvable dans le mappage. Utilisez le `Lookup` fonction membre pour l’extraction d’un élément.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CMapStringToOb::operator []`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>void\*& opérateur\[] (void \*</strong>  `key`  **\);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**MOT &, opérateur\[] (void** <strong>\*</strong> `key`  **\);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& opérateur\[] (lpctstr** `key`  **\);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString & opérateur\[] (lpctstr** `key`  **\);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& opérateur\[] (word** `key`  **\);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& opérateur\[] (word** `key`  **\);**|  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]  
  
 Les résultats à partir de ce programme sont les suivantes :  
  
```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```
  
##  <a name="removeall"></a>  CMapStringToOb::RemoveAll  
 Supprime tous les éléments de cette carte et détruit le `CString` objets de clé.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Notes  
 Le `CObject` objets référencés par chaque clé ne sont pas détruits. Le `RemoveAll` (fonction) peut provoquer des fuites de mémoire si vous ne garantissent pas que référencé `CObject` les objets sont détruits.  
  
 La fonction fonctionne correctement si la carte est déjà vide.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CMapStringToOb::RemoveAll`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll( );**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll( );**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll( );**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll( );**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll( );**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll( );**|  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]  
  
##  <a name="removekey"></a>  CMapStringToOb::RemoveKey  
 Recherche l’entrée de mappage correspondant à la clé fournie ; Ensuite, si la clé est trouvée, supprime l’entrée.  
  
```  
BOOL RemoveKey(LPCTSTR key);
```  
  
### <a name="parameters"></a>Paramètres  
 *key*  
 Spécifie la chaîne utilisée pour la recherche de la carte.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’entrée a été trouvée et supprimée avec succès ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cela peut entraîner des fuites de mémoire si le `CObject` objet n’est pas supprimé ailleurs.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CMapStringToOb::RemoveKey`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey (void** <strong>\*</strong> `key` **) ;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey (void** <strong>\*</strong> `key` **) ;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **) ;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **) ;**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey (WORD** `key` **) ;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey (WORD** `key` **) ;**|  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]  
  
 Les résultats à partir de ce programme sont les suivantes :  
  
```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```
  
##  <a name="setat"></a>  CMapStringToOb::SetAt  
 Le principal moyen d’insérer un élément dans un mappage.  
  
```  
void SetAt(
    LPCTSTR key,  
    CObject* newValue);
```  
  
### <a name="parameters"></a>Paramètres  
 *key*  
 Spécifie la chaîne qui est la clé du nouvel élément.  
  
 *newValue*  
 Spécifie le `CObject` pointeur qui est la valeur du nouvel élément.  
  
### <a name="remarks"></a>Notes  
 Tout d’abord, la clé est recherchée. Si la clé est trouvée, la valeur correspondante est modifiée. Sinon, un nouvel élément de clé-valeur est créé.  
  
 Le tableau suivant présente les autres membres fonctions qui sont similaires aux `CMapStringToOb::SetAt`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt (void** <strong>\*</strong> `key` **, void** <strong>\*</strong> `newValue` **) ;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt (void** <strong>\*</strong> `key` **, WORD** `newValue` **) ;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt (LPCTSTR** `key` **, void** <strong>\*</strong> `newValue` **) ;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt( LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt (WORD** `key` **, CObject** <strong>\*</strong> `newValue` **) ;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt (WORD** `key` **, void** <strong>\*</strong> `newValue` **) ;**|  
  
### <a name="example"></a>Exemple  
 Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples de collection.  
  
 [!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]  
  
 Les résultats à partir de ce programme sont les suivantes :  
  
```Output
before Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $493C 11
[Bart] = a CAge at $4654 13
after Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $49C0 12
[Bart] = a CAge at $4654 13
```
  
## <a name="see-also"></a>Voir aussi  
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CMapPtrToPtr, classe](../../mfc/reference/cmapptrtoptr-class.md)   
 [CMapPtrToWord, classe](../../mfc/reference/cmapptrtoword-class.md)   
 [CMapStringToPtr, classe](../../mfc/reference/cmapstringtoptr-class.md)   
 [Cmapstringtostring, classe](../../mfc/reference/cmapstringtostring-class.md)   
 [Cmapwordtoob, classe](../../mfc/reference/cmapwordtoob-class.md)   
 [CMapWordToPtr, classe](../../mfc/reference/cmapwordtoptr-class.md)
