---
description: 'En savoir plus sur : CMap, classe'
title: CMap, classe
ms.date: 11/04/2016
f1_keywords:
- CMap
- AFXTEMPL/CMap
- AFXTEMPL/CMap::CPair
- AFXTEMPL/CMap::CMap
- AFXTEMPL/CMap::GetCount
- AFXTEMPL/CMap::GetHashTableSize
- AFXTEMPL/CMap::GetNextAssoc
- AFXTEMPL/CMap::GetSize
- AFXTEMPL/CMap::GetStartPosition
- AFXTEMPL/CMap::InitHashTable
- AFXTEMPL/CMap::IsEmpty
- AFXTEMPL/CMap::Lookup
- AFXTEMPL/CMap::PGetFirstAssoc
- AFXTEMPL/CMap::PGetNextAssoc
- AFXTEMPL/CMap::PLookup
- AFXTEMPL/CMap::RemoveAll
- AFXTEMPL/CMap::RemoveKey
- AFXTEMPL/CMap::SetAt
helpviewer_keywords:
- CMap [MFC], CPair
- CMap [MFC], CMap
- CMap [MFC], GetCount
- CMap [MFC], GetHashTableSize
- CMap [MFC], GetNextAssoc
- CMap [MFC], GetSize
- CMap [MFC], GetStartPosition
- CMap [MFC], InitHashTable
- CMap [MFC], IsEmpty
- CMap [MFC], Lookup
- CMap [MFC], PGetFirstAssoc
- CMap [MFC], PGetNextAssoc
- CMap [MFC], PLookup
- CMap [MFC], RemoveAll
- CMap [MFC], RemoveKey
- CMap [MFC], SetAt
ms.assetid: 640a45ab-0993-4def-97ec-42cc78eb10b9
ms.openlocfilehash: ff88d205608cc87f06d28e6d2d4b647c35909efa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207902"
---
# <a name="cmap-class"></a>CMap, classe

Classe de collection de dictionnaires qui mappe des clés uniques à des valeurs.

## <a name="syntax"></a>Syntaxe

```
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject
```

#### <a name="parameters"></a>Paramètres

*KEY*<br/>
Classe de l’objet utilisé comme clé de la classe Map.

*ARG_KEY*<br/>
Type de données utilisé pour les arguments de *clé* ; généralement une référence à la *clé*.

*VALUE*<br/>
Classe de l’objet stocké dans la classe Map.

*ARG_VALUE*<br/>
Type de données utilisé pour les arguments de *valeur* ; généralement une référence à *value*.

## <a name="members"></a>Membres

### <a name="public-structures"></a>Structures publiques

|Nom|Description|
|----------|-----------------|
|[CMap :: CPair](#cpair)|Structure imbriquée contenant une valeur de clé et la valeur de l’objet associé.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMap :: CMap](#cmap)|Construit une collection qui mappe des clés aux valeurs.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMap :: GetCount](#getcount)|Retourne le nombre d’éléments de ce plan.|
|[CMap :: GetHashTableSize](#gethashtablesize)|Retourne le nombre d’éléments dans la table de hachage.|
|[CMap :: GetNextAssoc](#getnextassoc)|Obtient l’élément suivant pour l’itération.|
|[CMap :: Deis](#getsize)|Retourne le nombre d’éléments de ce plan.|
|[CMap :: GetStartPosition](#getstartposition)|Retourne la position du premier élément.|
|[CMap :: InitHashTable](#inithashtable)|Initialise la table de hachage et spécifie sa taille.|
|[CMap :: IsEmpty](#isempty)|Teste la condition de mappage vide (aucun élément).|
|[CMap :: Lookup](#lookup)|Recherche la valeur mappée à une clé donnée.|
|[CMap ::P GetFirstAssoc](#pgetfirstassoc)|Retourne un pointeur vers le premier élément.|
|[CMap ::P GetNextAssoc](#pgetnextassoc)|Obtient un pointeur vers l’élément suivant pour l’itération.|
|[CMap ::P Lookup](#plookup)|Retourne un pointeur vers une clé dont la valeur correspond à la valeur spécifiée.|
|[CMap :: RemoveAll](#removeall)|Supprime tous les éléments de ce mappage.|
|[CMap :: RemoveKey](#removekey)|Supprime un élément spécifié par une clé.|
|[CMap :: SetAt](#setat)|Insère un élément dans la classe Map ; remplace un élément existant si une clé correspondante est trouvée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CMap :: Operator \[\]](#operator_at)|Insère un élément dans la classe Map : substitution d’opérateur pour `SetAt` .|

## <a name="remarks"></a>Notes

Une fois que vous avez inséré une paire clé-valeur (élément) dans le mappage, vous pouvez récupérer ou supprimer efficacement la paire à l’aide de la clé pour y accéder. Vous pouvez également effectuer une itération sur tous les éléments de la carte.

Une variable de type POSITION est utilisée pour un autre accès aux entrées. Vous pouvez utiliser une POSITION pour « mémoriser » une entrée et pour effectuer une itération au sein de la carte. Vous pensez peut-être que cette itération est séquentielle par valeur de clé ; ce n’est pas le fait. La séquence des éléments récupérés est indéterminée.

Certaines fonctions membres de cette classe appellent des fonctions d’assistance globales qui doivent être personnalisées pour la plupart des utilisations de la `CMap` classe. Pour plus d’informations, consultez la section [relative aux classes de collection](../../mfc/reference/collection-class-helpers.md) dans la section macros et Globals de la **référence MFC**.

`CMap` Substitue [CObject :: Serialize](../../mfc/reference/cobject-class.md#serialize) pour prendre en charge la sérialisation et le vidage de ses éléments. Si un mappage est stocké dans une archive à l’aide de `Serialize` , chaque élément cartographique est sérialisé à son tour. L’implémentation par défaut de la `SerializeElements` fonction d’assistance effectue une écriture au niveau du bit. Pour plus d’informations sur la sérialisation d’éléments de collection de pointeurs dérivés de `CObject` ou d’autres types définis par l’utilisateur, consultez [How to : Make a Type-Safe collection](../../mfc/how-to-make-a-type-safe-collection.md).

Si vous avez besoin d’un vidage des diagnostics des éléments individuels dans le mappage (clés et valeurs), vous devez définir la profondeur du contexte de vidage sur une valeur supérieure ou égale à 1.

Lorsqu’un `CMap` objet est supprimé ou que ses éléments sont supprimés, les clés et les valeurs sont supprimées.

La dérivation de classe de mappage est similaire à la dérivation de liste. Consultez les [Collections](../../mfc/collections.md) d’articles pour obtenir une illustration de la dérivation d’une classe de liste à usage spécial.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMap`

## <a name="requirements"></a>Spécifications

**En-tête :** afxtempl.h

## <a name="cmapcmap"></a><a name="cmap"></a> CMap :: CMap

Construit un mappage vide.

```
CMap(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Paramètres

*nBlockSize*<br/>
Spécifie la granularité d’allocation de mémoire pour l’extension de la carte.

### <a name="remarks"></a>Notes

À mesure que la carte se développe, la mémoire est allouée en unités d’entrées *nBlockSize* .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]

## <a name="cmapcpair"></a><a name="cpair"></a> CMap :: CPair

Contient une valeur de clé et la valeur de l’objet associé.

### <a name="remarks"></a>Notes

Il s’agit d’une structure imbriquée dans la classe [CMAP](../../mfc/reference/cmap-class.md).

La structure est composée de deux champs :

- `key` Valeur réelle du type de clé.

- `value` Valeur de l’objet associé.

Il est utilisé pour stocker les valeurs de retour de [CMAP ::P Lookup](#plookup), [CMAP ::P getfirstassoc](#pgetfirstassoc)et [CMAP ::P GetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation, consultez l’exemple de [CMAP ::P Lookup](#plookup).

## <a name="cmapgetcount"></a><a name="getcount"></a> CMap :: GetCount

Récupère le nombre d’éléments dans la classe Map.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d'éléments.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMAP :: Lookup](#lookup).

## <a name="cmapgethashtablesize"></a><a name="gethashtablesize"></a> CMap :: GetHashTableSize

Détermine le nombre d’éléments dans la table de hachage pour la carte.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments dans la table de hachage.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]

## <a name="cmapgetnextassoc"></a><a name="getnextassoc"></a> CMap :: GetNextAssoc

Récupère l’élément cartographique à `rNextPosition` , puis met à jour `rNextPosition` pour faire référence à l’élément suivant dans la classe Map.

```cpp
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Paramètres

*rNextPosition*<br/>
Spécifie une référence à une valeur de POSITION retournée par un `GetNextAssoc` appel précédent ou `GetStartPosition` .

*KEY*<br/>
Paramètre de modèle qui spécifie le type de la clé de la carte.

*rKey*<br/>
Spécifie la clé retournée de l’élément récupéré.

*VALUE*<br/>
Paramètre de modèle qui spécifie le type de la valeur de la carte.

*rValue*<br/>
Spécifie la valeur retournée par l’élément récupéré.

### <a name="remarks"></a>Notes

Cette fonction est particulièrement utile pour itérer au sein de tous les éléments de la classe Map. Notez que la séquence de position n’est pas nécessairement la même que la séquence de valeur de clé.

Si l’élément récupéré est le dernier dans le mappage, la nouvelle valeur de *rNextPosition* est définie sur null.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMAP :: setat](#setat).

## <a name="cmapgetsize"></a><a name="getsize"></a> CMap :: Deis

Retourne le nombre d’éléments cartographiques.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments dans la carte.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre d’éléments dans la classe Map.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapgetstartposition"></a><a name="getstartposition"></a> CMap :: GetStartPosition

Démarre une itération de mappage en retournant une valeur de POSITION qui peut être passée à un `GetNextAssoc` appel.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur de POSITION qui indique une position de départ pour itérer la carte ; ou NULL si le mappage est vide.

### <a name="remarks"></a>Notes

La séquence d’itération n’est pas prévisible ; par conséquent, le « premier élément du mappage » n’a pas d’importance particulière.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMAP :: setat](#setat).

## <a name="cmapinithashtable"></a><a name="inithashtable"></a> CMap :: InitHashTable

Initialise la table de hachage.

```cpp
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);
```

### <a name="parameters"></a>Paramètres

*hashSize*<br/>
Nombre d’entrées dans la table de hachage.

*bAllocNow*<br/>
Si la valeur est TRUE, alloue la table de hachage lors de l’initialisation ; dans le cas contraire, la table est allouée.

### <a name="remarks"></a>Notes

Pour des performances optimales, la taille de la table de hachage doit être un nombre premier. Pour réduire les collisions, la taille doit être d’environ 20 pour cent plus grande que le plus grand jeu de données prévu.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMAP :: Lookup](#lookup).

## <a name="cmapisempty"></a><a name="isempty"></a> CMap :: IsEmpty

Détermine si le mappage est vide.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si ce mappage ne contient aucun élément ; Sinon, 0.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMAP :: RemoveAll](#removeall).

## <a name="cmaplookup"></a><a name="lookup"></a> CMap :: Lookup

Recherche la valeur mappée à une clé donnée.

```
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Paramètres

*ARG_KEY*<br/>
Paramètre de modèle spécifiant le type de la valeur de *clé* .

*key*<br/>
Spécifie la clé qui identifie l’élément à rechercher.

*VALUE*<br/>
Spécifie le type de la valeur à rechercher.

*rValue*<br/>
Reçoit la valeur recherchée.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’élément a été trouvé ; Sinon, 0.

### <a name="remarks"></a>Notes

`Lookup` utilise un algorithme de hachage pour trouver rapidement l’élément cartographique avec une clé qui correspond exactement à la clé donnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapoperator--"></a><a name="operator_at"></a> CMap :: Operator []

Substitution pratique de la `SetAt` fonction membre.

```
VALUE& operator[](arg_key key);
```

### <a name="parameters"></a>Paramètres

*VALUE*<br/>
Paramètre de modèle qui spécifie le type de la valeur de mappage.

*ARG_KEY*<br/>
Paramètre de modèle spécifiant le type de la valeur de clé.

*key*<br/>
Clé utilisée pour récupérer la valeur de la carte.

### <a name="remarks"></a>Notes

Il peut donc être utilisé uniquement sur le côté gauche d’une instruction d’assignation (une l-value). S’il n’y a pas d’élément cartographique avec la clé spécifiée, un nouvel élément est créé.

Il n’y a aucun « côté droit » (r-value) équivalent à cet opérateur, car il est possible qu’une clé ne soit pas trouvée dans le mappage. Utilisez la `Lookup` fonction membre pour la récupération d’élément.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMAP :: Lookup](#lookup).

## <a name="cmappgetfirstassoc"></a><a name="pgetfirstassoc"></a> CMap ::P GetFirstAssoc

Retourne la première entrée de l’objet Map.

```
const CPair* PGetFirstAssoc() const;
CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la première entrée dans le mappage ; consultez [CMAP :: CPair](#cpair). Si le mappage ne contient aucune entrée, la valeur est NULL.

### <a name="remarks"></a>Notes

Appelez cette fonction pour retourner un pointeur vers le premier élément de l’objet Map.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]

## <a name="cmappgetnextassoc"></a><a name="pgetnextassoc"></a> CMap ::P GetNextAssoc

Récupère l’élément de mappage pointé par *pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;

CPair *PGetNextAssoc(const CPair* pAssocRet);
```

### <a name="parameters"></a>Paramètres

*pAssocRet*<br/>
Pointe vers une entrée de mappage retournée par un appel [PGetNextAssoc](#pgetnextassoc) ou [CMAP ::P getfirstassoc](#pgetfirstassoc) précédent.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’entrée suivante dans le mappage ; consultez [CMAP :: CPair](#cpair). Si l’élément est le dernier dans le mappage, la valeur est NULL.

### <a name="remarks"></a>Notes

Appelez cette méthode pour itérer au sein de tous les éléments de la classe Map. Récupère le premier élément avec un appel à `PGetFirstAssoc` , puis itère au sein de la carte avec des appels successifs à `PGetNextAssoc` .

### <a name="example"></a>Exemple

Consultez l’exemple de [CMAP ::P getfirstassoc](#pgetfirstassoc).

## <a name="cmapplookup"></a><a name="plookup"></a> CMap ::P Lookup

Recherche la valeur mappée à une clé donnée.

```
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé pour l’élément à rechercher.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers une structure de clé ; consultez [CMAP :: CPair](#cpair). Si aucune correspondance n’est trouvée, `CMap::PLookup` retourne la valeur null.

### <a name="remarks"></a>Notes

Appelez cette méthode pour rechercher un élément cartographique avec une clé qui correspond exactement à la clé donnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]

## <a name="cmapremoveall"></a><a name="removeall"></a> CMap :: RemoveAll

Supprime toutes les valeurs de ce mappage en appelant la fonction d’assistance globale `DestructElements` .

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Notes

La fonction fonctionne correctement si le mappage est déjà vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]

## <a name="cmapremovekey"></a><a name="removekey"></a> CMap :: RemoveKey

Recherche l’entrée de mappage correspondant à la clé fournie. puis, si la clé est trouvée, supprime l’entrée.

```
BOOL RemoveKey(ARG_KEY key);
```

### <a name="parameters"></a>Paramètres

*ARG_KEY*<br/>
Paramètre de modèle spécifiant le type de la clé.

*key*<br/>
Clé pour l’élément à supprimer.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’entrée a été trouvée et supprimée avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

La `DestructElements` fonction d’assistance est utilisée pour supprimer l’entrée.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMAP :: setat](#setat).

## <a name="cmapsetat"></a><a name="setat"></a> CMap :: SetAt

Le principal moyen d’insérer un élément dans une classe Map.

```cpp
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```

### <a name="parameters"></a>Paramètres

*ARG_KEY*<br/>
Paramètre de modèle spécifiant le type du paramètre de *clé* .

*key*<br/>
Spécifie la clé du nouvel élément.

*ARG_VALUE*<br/>
Paramètre de modèle spécifiant le type du paramètre *NewValue* .

*newValue*<br/>
Spécifie la valeur du nouvel élément.

### <a name="remarks"></a>Notes

Tout d’abord, la clé est recherchée. Si la clé est trouvée, la valeur correspondante est modifiée ; Sinon, une nouvelle paire clé-valeur est créée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple de collecte MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
