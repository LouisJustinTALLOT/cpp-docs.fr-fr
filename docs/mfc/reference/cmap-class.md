---
title: CMap (classe)
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
ms.openlocfilehash: 58f9efb19988be8487ec87ce0c63d90ee1a97911
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769834"
---
# <a name="cmap-class"></a>CMap (classe)

Classe de collection de dictionnaires qui mappe des clés uniques à des valeurs.

## <a name="syntax"></a>Syntaxe

```
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject
```

#### <a name="parameters"></a>Paramètres

*KEY*<br/>
Classe de l’objet utilisé comme clé pour la carte.

*ARG_KEY*<br/>
Type de données utilisé pour *clé* arguments ; généralement une référence à *clé*.

*VALEUR*<br/>
Classe de l’objet stocké dans la classe map.

*ARG_VALUE*<br/>
Type de données utilisé pour *valeur* arguments ; généralement une référence à *valeur*.

## <a name="members"></a>Membres

### <a name="public-structures"></a>Structures publiques

|Nom|Description|
|----------|-----------------|
|[CMap::CPair](#cpair)|Une structure imbriquée contenant une valeur de clé et la valeur de l’objet associé.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMap::CMap](#cmap)|Construit une collection qui mappe les valeurs des clés.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMap::GetCount](#getcount)|Retourne le nombre d’éléments dans ce mappage.|
|[CMap::GetHashTableSize](#gethashtablesize)|Retourne le nombre d’éléments dans la table de hachage.|
|[CMap::GetNextAssoc](#getnextassoc)|Obtient l’élément suivant pour une itération.|
|[CMap::GetSize](#getsize)|Retourne le nombre d’éléments dans ce mappage.|
|[CMap::GetStartPosition](#getstartposition)|Retourne la position du premier élément.|
|[CMap::InitHashTable](#inithashtable)|Initialise la table de hachage et spécifie sa taille.|
|[CMap::IsEmpty](#isempty)|Vérifie si la condition vide-map (pas d’éléments).|
|[CMap::Lookup](#lookup)|Recherche la valeur mappée à une clé donnée.|
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|Retourne un pointeur vers le premier élément.|
|[CMap::PGetNextAssoc](#pgetnextassoc)|Obtient un pointeur vers l’élément suivant pour une itération.|
|[CMap::PLookup](#plookup)|Retourne un pointeur vers une clé dont la valeur correspond à la valeur spécifiée.|
|[CMap::RemoveAll](#removeall)|Supprime tous les éléments de ce mappage.|
|[CMap::RemoveKey](#removekey)|Supprime un élément spécifié par une clé.|
|[CMap::SetAt](#setat)|Insère un élément dans l’objet map. remplace un élément existant si une clé correspondante est trouvée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CMap::operator \[ \]](#operator_at)|Insère un élément dans la classe map, substitution d’opérateur pour `SetAt`.|

## <a name="remarks"></a>Notes

Une fois que vous avez inséré une paire clé-valeur (élément) dans la classe map, vous pouvez efficacement récupérer ou supprimer la paire à l’aide de la clé pour y accéder. Vous pouvez également itérer sur tous les éléments dans le mappage.

Une variable de type de que position est utilisée pour un autre accès aux entrées. Vous pouvez utiliser une POSITION à une entrée « mémoriser » et à effectuer une itération dans la carte. Vous pourriez penser que cette itération est séquentielle par valeur de clé ; Il n’est pas le cas. La séquence des éléments récupérés est indéterminée.

Certaines fonctions de membre de cet appel de la classe d’assistance globales des fonctions qui doivent être personnalisées pour la plupart des utilisations de la `CMap` classe. Consultez [Assistants de classe de Collection](../../mfc/reference/collection-class-helpers.md) dans la section de Macros et objet Globals de la **référence MFC**.

`CMap` substitue [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) pour prendre en charge la sérialisation et le vidage de ses éléments. Si un mappage est stocké dans une archive à l’aide `Serialize`, chaque élément cartographique est sérialisé à son tour. L’implémentation par défaut de la `SerializeElements` fonction d’assistance effectue une écriture au niveau du bit. Pour plus d’informations sur la sérialisation des éléments de collecte de pointeur dérivé `CObject` ou autres types définis par l’utilisateur, consultez [Comment : Définir une Collection de Type sécurisé](../../mfc/how-to-make-a-type-safe-collection.md).

Si vous avez besoin d’un vidage de diagnostic des éléments individuels dans le mappage (les clés et valeurs), vous devez définir la profondeur du contexte de vidage à 1 ou supérieur.

Quand un `CMap` objet est supprimé, ou lorsque ses éléments sont supprimés, les clés et valeurs sont supprimés.

Dérivation de classe Map est similaire à la dérivation de la liste. Consultez l’article [Collections](../../mfc/collections.md) pour obtenir une illustration de la dérivation d’une classe de liste de spécial.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMap`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxtempl.h

##  <a name="cmap"></a>  CMap::CMap

Construit un mappage vide.

```
CMap(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Paramètres

*nBlockSize*<br/>
Spécifie la granularité d’allocation de mémoire pour l’extension de la carte.

### <a name="remarks"></a>Notes

Comme la carte s’accroît, la mémoire est allouée en unités de *nBlockSize* entrées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]

##  <a name="cpair"></a>  CMap::CPair

Contient une valeur de clé et la valeur de l’objet associé.

### <a name="remarks"></a>Notes

Il s’agit d’une structure imbriquée au sein de la classe [CMap](../../mfc/reference/cmap-class.md).

La structure se compose de deux champs :

- `key` La valeur réelle du type de clé.

- `value` La valeur de l’objet associé.

Il est utilisé pour stocker les valeurs de retour à partir de [CMap::PLookup](#plookup), [CMap::PGetFirstAssoc](#pgetfirstassoc), et [CMap::PGetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation, consultez l’exemple de [CMap::PLookup](#plookup).

##  <a name="getcount"></a>  CMap::GetCount

Récupère le nombre d’éléments dans le mappage.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMap::Lookup](#lookup).

##  <a name="gethashtablesize"></a>  CMap::GetHashTableSize

Détermine le nombre d’éléments dans la table de hachage pour la carte.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans la table de hachage.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]

##  <a name="getnextassoc"></a>  CMap::GetNextAssoc

Récupère l’élément de carte à `rNextPosition`, puis met à jour `rNextPosition` pour faire référence à l’élément suivant dans la carte.

```
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Paramètres

*rNextPosition*<br/>
Spécifie une référence à une valeur POSITION retournée par une précédente `GetNextAssoc` ou `GetStartPosition` appeler.

*KEY*<br/>
Paramètre de modèle qui spécifie le type de clé de la carte.

*rKey*<br/>
Spécifie la clé retournée de l’élément récupéré.

*VALEUR*<br/>
Paramètre de modèle qui spécifie le type de valeur de la carte.

*rValue*<br/>
Spécifie la valeur retournée de l’élément récupéré.

### <a name="remarks"></a>Notes

Cette fonction est particulièrement utile pour itérer tous les éléments dans le mappage. Notez que la séquence de position n’est pas nécessairement identique à la séquence de la valeur de clé.

Si l’élément récupéré est le dernier dans le mappage, puis la nouvelle valeur de *rNextPosition* est définie sur NULL.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMap::SetAt](#setat).

##  <a name="getsize"></a>  CMap::GetSize

Retourne le nombre d’éléments de mappage.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans le mappage.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre d’éléments dans le mappage.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

##  <a name="getstartposition"></a>  CMap::GetStartPosition

Démarre une itération de la carte en retournant une valeur POSITION qui peut être passée à un `GetNextAssoc` appeler.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui indique une position de départ pour une itération de la carte ; ou NULL si le mappage est vide.

### <a name="remarks"></a>Notes

La séquence d’itération n’est pas prévisible ; Par conséquent, le « premier élément dans le mappage » n’a aucun signification particulière.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMap::SetAt](#setat).

##  <a name="inithashtable"></a>  CMap::InitHashTable

Initialise la table de hachage.

```
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);
```

### <a name="parameters"></a>Paramètres

*hashSize*<br/>
Nombre d’entrées dans la table de hachage.

*bAllocNow*<br/>
Si la valeur est TRUE, alloue de la table de hachage lors de l’initialisation ; Sinon, le tableau est alloué lorsque nécessaire.

### <a name="remarks"></a>Notes

Pour de meilleures performances, la taille de table de hachage doit être un nombre premier. Pour réduire les collisions, la taille doit être à peu près supérieur le plus grand jeu de données anticipé à 20 pour cent.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMap::Lookup](#lookup).

##  <a name="isempty"></a>  CMap::IsEmpty

Détermine si le mappage est vide.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si ce mappage ne contient aucun élément ; sinon 0.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMap::RemoveAll](#removeall).

##  <a name="lookup"></a>  CMap::Lookup

Recherche la valeur mappée à une clé donnée.

```
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Paramètres

*ARG_KEY*<br/>
Paramètre de modèle spécifiant le type de la *clé* valeur.

*key*<br/>
Spécifie la clé qui identifie l’élément à rechercher.

*VALEUR*<br/>
Spécifie le type de la valeur à rechercher.

*rValue*<br/>
Reçoit la valeur recherché.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’élément a été trouvé ; sinon 0.

### <a name="remarks"></a>Notes

`Lookup` utilise un algorithme de hachage pour trouver rapidement l’élément de carte avec une clé qui correspond exactement à la clé donnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

##  <a name="operator_at"></a>  CMap::operator [ ]

Une alternative pratique à la `SetAt` fonction membre.

```
VALUE& operator[](arg_key key);
```

### <a name="parameters"></a>Paramètres

*VALEUR*<br/>
Paramètre de modèle qui spécifie le type de la valeur de la carte.

*ARG_KEY*<br/>
Paramètre de modèle spécifiant le type de la valeur de clé.

*key*<br/>
La clé utilisée pour récupérer la valeur de la carte.

### <a name="remarks"></a>Notes

Par conséquent, il peut être utilisé uniquement sur le côté gauche d’une instruction d’assignation (une l-value). S’il n’existe aucun élément de mappage avec la clé spécifiée, un nouvel élément est créé.

Aucun (r-value) « droite » n’est équivalent à cet opérateur, car il est possible qu’une clé peut être introuvable dans le mappage. Utilisez le `Lookup` fonction membre pour l’extraction d’un élément.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMap::Lookup](#lookup).

##  <a name="pgetfirstassoc"></a>  CMap::PGetFirstAssoc

Retourne la première entrée de l’objet map.

```
const CPair* PGetFirstAssoc() const;
CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la première entrée dans le mappage ; consultez [CMap::CPair](#cpair). Si la carte ne contient aucune entrée, la valeur est NULL.

### <a name="remarks"></a>Notes

Appelez cette fonction pour retourner un pointeur du premier élément dans l’objet map.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]

##  <a name="pgetnextassoc"></a>  CMap::PGetNextAssoc

Récupère l’élément de mappage vers lequel pointé *pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;

CPair *PGetNextAssoc(const CPair* pAssocRet);
```

### <a name="parameters"></a>Paramètres

*pAssocRet*<br/>
Pointe vers une entrée de mappage retournée par une précédente [PGetNextAssoc](#pgetnextassoc) ou [CMap::PGetFirstAssoc](#pgetfirstassoc) appeler.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’entrée suivante dans le mappage ; consultez [CMap::CPair](#cpair). Si l’élément est le dernier dans le mappage, la valeur est NULL.

### <a name="remarks"></a>Notes

Appelez cette méthode pour effectuer une itération dans tous les éléments dans le mappage. Récupérer le premier élément avec un appel à `PGetFirstAssoc` , puis itérer la carte avec des appels successifs à `PGetNextAssoc`.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMap::PGetFirstAssoc](#pgetfirstassoc).

##  <a name="plookup"></a>  CMap::PLookup

Recherche la valeur mappée à une clé donnée.

```
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé de l’élément à rechercher.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers une structure de clés ; consultez [CMap::CPair](#cpair). Si aucune correspondance n’est trouvée, `CMap::PLookup` renvoie la valeur NULL.

### <a name="remarks"></a>Notes

Appelez cette méthode pour rechercher un élément de carte avec une clé qui correspond exactement à la clé donnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]

##  <a name="removeall"></a>  CMap::RemoveAll

Supprime toutes les valeurs à partir de ce mappage en appelant la fonction d’assistance globales `DestructElements`.

```
void RemoveAll();
```

### <a name="remarks"></a>Notes

La fonction fonctionne correctement si la carte est déjà vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]

##  <a name="removekey"></a>  CMap::RemoveKey

Recherche l’entrée de mappage correspondant à la clé fournie ; Ensuite, si la clé est trouvée, supprime l’entrée.

```
BOOL RemoveKey(ARG_KEY key);
```

### <a name="parameters"></a>Paramètres

*ARG_KEY*<br/>
Paramètre de modèle qui spécifie le type de la clé.

*key*<br/>
Clé de l’élément à supprimer.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’entrée a été trouvée et supprimée avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Le `DestructElements` fonction d’assistance est utilisée pour supprimer l’entrée.

### <a name="example"></a>Exemple

Consultez l’exemple de [CMap::SetAt](#setat).

##  <a name="setat"></a>  CMap::SetAt

Le principal moyen d’insérer un élément dans un mappage.

```
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```

### <a name="parameters"></a>Paramètres

*ARG_KEY*<br/>
Paramètre de modèle spécifiant le type de la *clé* paramètre.

*key*<br/>
Spécifie la clé du nouvel élément.

*ARG_VALUE*<br/>
Paramètre de modèle spécifiant le type de la *newValue* paramètre.

*newValue*<br/>
Spécifie la valeur du nouvel élément.

### <a name="remarks"></a>Notes

Tout d’abord, la clé est recherchée. Si la clé est trouvée, la valeur correspondante est modifiée. Sinon, une nouvelle paire clé-valeur est créée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC COLLECT](../../overview/visual-cpp-samples.md)<br/>
[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
