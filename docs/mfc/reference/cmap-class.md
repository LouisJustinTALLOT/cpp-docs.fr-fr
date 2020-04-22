---
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
ms.openlocfilehash: fbb34d4db41ef11cd01a6a8a7f20cafa0e737268
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749077"
---
# <a name="cmap-class"></a>CMap, classe

Classe de collection de dictionnaires qui mappe des clés uniques à des valeurs.

## <a name="syntax"></a>Syntaxe

```
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject
```

#### <a name="parameters"></a>Paramètres

*Clé*<br/>
Classe de l’objet utilisé comme la clé de la carte.

*ARG_KEY*<br/>
Type de données utilisé pour les arguments *KEY;* généralement une référence à *KEY*.

*Valeur*<br/>
Classe de l’objet stocké dans la carte.

*ARG_VALUE*<br/>
Type de données utilisé pour les arguments *VALUE;* généralement une référence à *VALUE*.

## <a name="members"></a>Membres

### <a name="public-structures"></a>Structures publiques

|Nom|Description|
|----------|-----------------|
|[CMap::CPair](#cpair)|Une structure imbriquée contenant une valeur clé et la valeur de l’objet associé.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMap::CMap](#cmap)|Construit une collection qui cartographie les clés des valeurs.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMap::GetCount](#getcount)|Retourne le nombre d’éléments dans cette carte.|
|[CMap::GetHashTableSize](#gethashtablesize)|Retourne le nombre d’éléments dans le tableau de hachage.|
|[CMap::GetNextAssoc](#getnextassoc)|Obtient le prochain élément pour itérer.|
|[CMap::GetSize](#getsize)|Retourne le nombre d’éléments dans cette carte.|
|[CMap::GetStartPosition](#getstartposition)|Retourne la position du premier élément.|
|[CMap::InitHashTable](#inithashtable)|Initialise la table de hachage et précise sa taille.|
|[CMap::IsEmpty](#isempty)|Tests pour l’état de la carte vide (pas d’éléments).|
|[CMap::Lookup](#lookup)|Recherche la valeur cartographiée à une clé donnée.|
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|Retourne un pointeur au premier élément.|
|[CMap::PGetNextAssoc](#pgetnextassoc)|Obtient un pointeur à l’élément suivant pour itérer.|
|[CMap::PLookup](#plookup)|Retourne un pointeur à une clé dont la valeur correspond à la valeur spécifiée.|
|[CMap::RemoveAll](#removeall)|Supprime tous les éléments de cette carte.|
|[CMap::RemoveKey](#removekey)|Supprime un élément spécifié par une clé.|
|[CMap::SetAt](#setat)|Insère un élément dans la carte; remplace un élément existant si une clé correspondante est trouvée.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CMap::opérateur \[\]](#operator_at)|Insère un élément dans la `SetAt`carte — substitution de l’opérateur pour .|

## <a name="remarks"></a>Notes

Une fois que vous avez inséré une paire de valeur clé (élément) dans la carte, vous pouvez récupérer ou supprimer efficacement la paire en utilisant la clé pour y accéder. Vous pouvez également itérer sur tous les éléments de la carte.

Une variable de type POSITION est utilisée pour un accès alternatif aux entrées. Vous pouvez utiliser un POSITION pour « se souvenir » d’une entrée et pour itérer à travers la carte. Vous pourriez penser que cette itération est séquentielle par valeur clé; ce n’est pas le cas. La séquence des éléments récupérés est indéterminée.

Certaines fonctions membres de cette classe appellent fonctions d’aide globale `CMap` qui doivent être personnalisées pour la plupart des utilisations de la classe. Voir [Collection Class Helpers](../../mfc/reference/collection-class-helpers.md) dans la section Macros et Globals de la **référence MFC**.

`CMap`remplace [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) pour soutenir la sérialisation et le dumping de ses éléments. Si une carte est stockée `Serialize`dans une archive à l’aide de chaque élément de carte est sérialisé à son tour. La mise en `SerializeElements` œuvre par défaut de la fonction d’aide fait une écriture un peu sage. Pour plus d’informations sur la `CObject` sérialisation des éléments de collecte de pointeurs dérivés ou d’autres types définis par l’utilisateur, voir [Comment : Faire une collection type-safe](../../mfc/how-to-make-a-type-safe-collection.md).

Si vous avez besoin d’un vidage diagnostique des éléments individuels de la carte (les clés et les valeurs), vous devez définir la profondeur du contexte de décharge à 1 ou plus.

Lorsqu’un `CMap` objet est supprimé ou lorsque ses éléments sont supprimés, les clés et les valeurs sont supprimées.

La dérivation de classe de carte est semblable à la dérivation de liste. Voir l’article [Collections](../../mfc/collections.md) pour une illustration de la dérivation d’une classe de liste à usage spécial.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMap`

## <a name="requirements"></a>Spécifications

**En-tête :** afxtempl.h

## <a name="cmapcmap"></a><a name="cmap"></a>CMap::CMap

Construit une carte vide.

```
CMap(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Paramètres

*nBlockSize (en)*<br/>
Spécifie la granularité de la mémoire-allocation pour l’extension de la carte.

### <a name="remarks"></a>Notes

Au fur et à mesure que la carte se développe, la mémoire est attribuée dans les unités d’entrées *nBlockSize.*

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]

## <a name="cmapcpair"></a><a name="cpair"></a>CMap::CPair

Contient une valeur clé et la valeur de l’objet associé.

### <a name="remarks"></a>Notes

Il s’agit d’une structure imbriquée dans la classe [CMap](../../mfc/reference/cmap-class.md).

La structure est composée de deux champs :

- `key`La valeur réelle du type clé.

- `value`La valeur de l’objet associé.

Il est utilisé pour stocker les valeurs de retour de [CMap::PLookup](#plookup), [CMap::PGetFirstAssoc](#pgetfirstassoc), et [CMap::PGetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Exemple

Pour un exemple d’utilisation, voir l’exemple pour [CMap::PLookup](#plookup).

## <a name="cmapgetcount"></a><a name="getcount"></a>CMap::GetCount

Récupère le nombre d’éléments dans la carte.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments.

### <a name="example"></a>Exemple

Voir l’exemple pour [CMap:Lookup](#lookup).

## <a name="cmapgethashtablesize"></a><a name="gethashtablesize"></a>CMap::GetHashTableSize

Détermine le nombre d’éléments dans le tableau de hachage pour la carte.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans le tableau de hachage.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]

## <a name="cmapgetnextassoc"></a><a name="getnextassoc"></a>CMap::GetNextAssoc

Récupère l’élément `rNextPosition`de la `rNextPosition` carte à , puis mises à jour pour se référer à l’élément suivant dans la carte.

```cpp
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Paramètres

*rNextPosition (en)*<br/>
Spécifie une référence à une `GetNextAssoc` `GetStartPosition` valeur POSITION retournée par un précédent ou un appel.

*Clé*<br/>
Paramètre de modèle spécifiant le type de clé de la carte.

*rKey (en)*<br/>
Spécifie la clé retournée de l’élément récupéré.

*Valeur*<br/>
Paramètre de modèle spécifiant le type de valeur de la carte.

*rValue (en)*<br/>
Spécifie la valeur retournée de l’élément récupéré.

### <a name="remarks"></a>Notes

Cette fonction est plus utile pour itérer à travers tous les éléments de la carte. Notez que la séquence de position n’est pas nécessairement la même que la séquence de valeur clé.

Si l’élément récupéré est le dernier de la carte, alors la nouvelle valeur de *rNextPosition* est réglée à NULL.

### <a name="example"></a>Exemple

Voir l’exemple pour [CMap:SetAt](#setat).

## <a name="cmapgetsize"></a><a name="getsize"></a>CMap::GetSize

Retourne le nombre d’éléments cartographiques.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans la carte.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le nombre d’éléments dans la carte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapgetstartposition"></a><a name="getstartposition"></a>CMap::GetStartPosition

Démarre une itération de carte en retournant une `GetNextAssoc` valeur POSITION qui peut être passée à un appel.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Une valeur POSITION qui indique une position de départ pour itérer la carte; ou NULL si la carte est vide.

### <a name="remarks"></a>Notes

La séquence d’itération n’est pas prévisible; par conséquent, le «premier élément de la carte» n’a pas d’importance particulière.

### <a name="example"></a>Exemple

Voir l’exemple pour [CMap:SetAt](#setat).

## <a name="cmapinithashtable"></a><a name="inithashtable"></a>CMap::InitHashTable

Initialise la table de hachage.

```cpp
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);
```

### <a name="parameters"></a>Paramètres

*hashSize*<br/>
Nombre d’entrées dans le tableau de hachage.

*bAllocNow*<br/>
Si VRAI, alloue la table de hachage lors de l’initialisation; sinon la table est attribuée en cas de besoin.

### <a name="remarks"></a>Notes

Pour de meilleures performances, la taille de la table de hachage devrait être un nombre de choix. Pour minimiser les collisions, la taille devrait être d’environ 20 p. 100 plus grande que l’ensemble de données le plus important prévu.

### <a name="example"></a>Exemple

Voir l’exemple pour [CMap:Lookup](#lookup).

## <a name="cmapisempty"></a><a name="isempty"></a>CMap::IsEmpty

Détermine si la carte est vide.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si cette carte ne contient pas d’éléments; sinon 0.

### <a name="example"></a>Exemple

Voir l’exemple pour [CMap:RemoveAll](#removeall).

## <a name="cmaplookup"></a><a name="lookup"></a>CMap::Lookup

Recherche la valeur cartographiée à une clé donnée.

```
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Paramètres

*ARG_KEY*<br/>
Paramètre de modèle spécifiant le type de valeur *clé.*

*key*<br/>
Spécifie la clé qui identifie l’élément à lever.

*Valeur*<br/>
Spécifie le type de valeur à lever.

*rValue (en)*<br/>
Reçoit la valeur recherchée.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’élément a été trouvé; sinon 0.

### <a name="remarks"></a>Notes

`Lookup`utilise un algorithme de hachage pour trouver rapidement l’élément de carte avec une clé qui correspond exactement à la clé donnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]

## <a name="cmapoperator--"></a><a name="operator_at"></a>CMap::opérateur [ ]

Un substitut pratique `SetAt` à la fonction de membre.

```
VALUE& operator[](arg_key key);
```

### <a name="parameters"></a>Paramètres

*Valeur*<br/>
Paramètre de modèle spécifiant le type de valeur de la carte.

*ARG_KEY*<br/>
Paramètre de modèle spécifiant le type de valeur clé.

*key*<br/>
La clé utilisée pour récupérer la valeur de la carte.

### <a name="remarks"></a>Notes

Ainsi, il ne peut être utilisé que sur le côté gauche d’une déclaration d’affectation (une valeur l). S’il n’y a pas d’élément de carte avec la clé spécifiée, un nouvel élément est créé.

Il n’y a pas d’équivalent « côté droit » (r-valeur) à cet opérateur parce qu’il est possible qu’une clé ne soit pas trouvée dans la carte. Utilisez `Lookup` la fonction membre pour la récupération d’éléments.

### <a name="example"></a>Exemple

Voir l’exemple pour [CMap:Lookup](#lookup).

## <a name="cmappgetfirstassoc"></a><a name="pgetfirstassoc"></a>CMap::PGetFirstAssoc

Retourne la première entrée de l’objet de la carte.

```
const CPair* PGetFirstAssoc() const;
CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à la première entrée dans la carte; voir [CMap::CPair](#cpair). Si la carte ne contient aucune entrée, la valeur est NULL.

### <a name="remarks"></a>Notes

Appelez cette fonction pour retourner un pointeur le premier élément de l’objet de carte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#59](../../mfc/codesnippet/cpp/cmap-class_4.cpp)]

## <a name="cmappgetnextassoc"></a><a name="pgetnextassoc"></a>CMap::PGetNextAssoc

Récupère l’élément de carte pointé par *pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssocRet) const;

CPair *PGetNextAssoc(const CPair* pAssocRet);
```

### <a name="parameters"></a>Paramètres

*pAssocRet*<br/>
Points à une entrée de carte retournée par un précédent [PGetNextAssoc](#pgetnextassoc) ou [CMap::PGetFirstAssoc](#pgetfirstassoc) appel.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la prochaine entrée dans la carte; voir [CMap::CPair](#cpair). Si l’élément est le dernier de la carte, la valeur est NULL.

### <a name="remarks"></a>Notes

Appelez cette méthode pour itérer à travers tous les éléments de la carte. Récupérez le premier élément `PGetFirstAssoc` avec un appel à et puis `PGetNextAssoc`itérer à travers la carte avec des appels successifs à .

### <a name="example"></a>Exemple

Voir l’exemple pour [CMap::PGetFirstAssoc](#pgetfirstassoc).

## <a name="cmapplookup"></a><a name="plookup"></a>CMap::PLookup

Trouve la valeur cartographiée à une clé donnée.

```
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé pour l’élément à rechercher.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers une structure clé; voir [CMap::CPair](#cpair). Si aucune correspondance `CMap::PLookup` n’est trouvée, retourne NULL.

### <a name="remarks"></a>Notes

Appelez cette méthode pour rechercher un élément de carte avec une clé qui correspond exactement à la clé donnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]

## <a name="cmapremoveall"></a><a name="removeall"></a>CMap::RemoveAll

Supprime toutes les valeurs de cette carte en `DestructElements`appelant la fonction globale d’aide .

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Notes

La fonction fonctionne correctement si la carte est déjà vide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#61](../../mfc/codesnippet/cpp/cmap-class_6.cpp)]

## <a name="cmapremovekey"></a><a name="removekey"></a>CMap::RemoveKey

Recherche l’entrée de la carte correspondant à la clé fournie; puis, si la clé est trouvée, supprime l’entrée.

```
BOOL RemoveKey(ARG_KEY key);
```

### <a name="parameters"></a>Paramètres

*ARG_KEY*<br/>
Paramètre de modèle spécifiant le type de clé.

*key*<br/>
Clé pour que l’élément soit enlevé.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’entrée a été trouvée et enlevée avec succès; sinon 0.

### <a name="remarks"></a>Notes

La `DestructElements` fonction d’aide est utilisée pour enlever l’entrée.

### <a name="example"></a>Exemple

Voir l’exemple pour [CMap:SetAt](#setat).

## <a name="cmapsetat"></a><a name="setat"></a>CMap::SetAt

Le principal moyen d’insérer un élément dans une carte.

```cpp
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```

### <a name="parameters"></a>Paramètres

*ARG_KEY*<br/>
Paramètre de modèle spécifiant le type de paramètre *clé.*

*key*<br/>
Spécifie la clé du nouvel élément.

*ARG_VALUE*<br/>
Paramètre de modèle spécifiant le type du *nouveau paramètreValue.*

*newValue*<br/>
Spécifie la valeur du nouvel élément.

### <a name="remarks"></a>Notes

Tout d’abord, la clé est regardée vers le haut. Si la clé est trouvée, alors la valeur correspondante est modifiée; sinon une nouvelle paire de valeur clé est créée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC Échantillon COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
