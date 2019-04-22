---
title: CAtlMap, classe
ms.date: 11/04/2016
f1_keywords:
- CAtlMap
- ATLCOLL/ATL::CAtlMap
- ATLCOLL/ATL::CAtlMap::KINARGTYPE
- ATLCOLL/ATL::CAtlMap::KOUTARGTYPE
- ATLCOLL/ATL::CAtlMap::VINARGTYPE
- ATLCOLL/ATL::CAtlMap::VOUTARGTYPE
- ATLCOLL/ATL::CPair::m_key
- ATLCOLL/ATL::CPair::m_value
- ATLCOLL/ATL::CAtlMap::CAtlMap
- ATLCOLL/ATL::CAtlMap::AssertValid
- ATLCOLL/ATL::CAtlMap::DisableAutoRehash
- ATLCOLL/ATL::CAtlMap::EnableAutoRehash
- ATLCOLL/ATL::CAtlMap::GetAt
- ATLCOLL/ATL::CAtlMap::GetCount
- ATLCOLL/ATL::CAtlMap::GetHashTableSize
- ATLCOLL/ATL::CAtlMap::GetKeyAt
- ATLCOLL/ATL::CAtlMap::GetNext
- ATLCOLL/ATL::CAtlMap::GetNextAssoc
- ATLCOLL/ATL::CAtlMap::GetNextKey
- ATLCOLL/ATL::CAtlMap::GetNextValue
- ATLCOLL/ATL::CAtlMap::GetStartPosition
- ATLCOLL/ATL::CAtlMap::GetValueAt
- ATLCOLL/ATL::CAtlMap::InitHashTable
- ATLCOLL/ATL::CAtlMap::IsEmpty
- ATLCOLL/ATL::CAtlMap::Lookup
- ATLCOLL/ATL::CAtlMap::Rehash
- ATLCOLL/ATL::CAtlMap::RemoveAll
- ATLCOLL/ATL::CAtlMap::RemoveAtPos
- ATLCOLL/ATL::CAtlMap::RemoveKey
- ATLCOLL/ATL::CAtlMap::SetAt
- ATLCOLL/ATL::CAtlMap::SetOptimalLoad
- ATLCOLL/ATL::CAtlMap::SetValueAt
helpviewer_keywords:
- CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
ms.openlocfilehash: 1821532a4d5a3078202f180273b02945b8d8e4ba
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58774553"
---
# <a name="catlmap-class"></a>CAtlMap, classe

Cette classe fournit des méthodes pour créer et gérer un objet de mappage.

## <a name="syntax"></a>Syntaxe

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CAtlMap
```

#### <a name="parameters"></a>Paramètres

*K*<br/>
Le type d’élément clé.

*V*<br/>
Le type d’élément de valeur.

*KTraits*<br/>
Le code utilisé pour copier ou déplacer les éléments clés. Consultez [celementtraits, classe](../../atl/reference/celementtraits-class.md) pour plus d’informations.

*VTraits*<br/>
Le code utilisé pour copier ou déplacer des éléments de valeur.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CAtlMap::KINARGTYPE](#kinargtype)|Type utilisé lorsqu’une touche est passée comme argument d’entrée|
|[CAtlMap::KOUTARGTYPE](#koutargtype)|Type utilisé pour une clé est retournée comme un argument de sortie.|
|[CAtlMap::VINARGTYPE](#vinargtype)|Type utilisé lorsqu’une valeur est passée comme argument d’entrée.|
|[CAtlMap::VOUTARGTYPE](#voutargtype)|Type utilisé lorsqu’une valeur est passée comme un argument de sortie.|

### <a name="public-classes"></a>Classes publiques

|Nom|Description|
|----------|-----------------|
|[Classe de CAtlMap::CPair](#cpair_class)|Une classe qui contient les éléments clé / valeur.|

### <a name="cpair-data-members"></a>Membres de données de CPair

|Nom|Description|
|----------|-----------------|
|[CPair::m_key](#m_key)|Le stockage de l’élément clé de membre de données.|
|[CPair::m_value](#m_value)|Le membre de données stocker l’élément de valeur.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlMap::CAtlMap](#catlmap)|Constructeur.|
|[CAtlMap::~CAtlMap](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlMap::AssertValid](#assertvalid)|Appelez cette méthode pour provoquer une assertion si le `CAtlMap` n’est pas valide.|
|[CAtlMap::DisableAutoRehash](#disableautorehash)|Appelez cette méthode pour désactiver aborderont automatique de la `CAtlMap` objet.|
|[CAtlMap::EnableAutoRehash](#enableautorehash)|Appelez cette méthode pour activer aborderont automatique de la `CAtlMap` objet.|
|[CAtlMap::GetAt](#getat)|Appelez cette méthode pour retourner l’élément à une position spécifiée dans le mappage.|
|[CAtlMap::GetCount](#getcount)|Appelez cette méthode pour récupérer le nombre d’éléments dans le mappage.|
|[CAtlMap::GetHashTableSize](#gethashtablesize)|Appelez cette méthode pour déterminer le nombre de compartiments dans la table de hachage de la carte.|
|[CAtlMap::GetKeyAt](#getkeyat)|Appelez cette méthode pour récupérer la clé stockée à la position donnée dans le `CAtlMap` objet.|
|[CAtlMap::GetNext](#getnext)|Appelez cette méthode pour obtenir un pointeur vers l’élément suivant paire stockée dans le `CAtlMap` objet.|
|[CAtlMap::GetNextAssoc](#getnextassoc)|Obtient l’élément suivant pour une itération.|
|[CAtlMap::GetNextKey](#getnextkey)|Appelez cette méthode pour récupérer la clé suivante dans le `CAtlMap` objet.|
|[CAtlMap::GetNextValue](#getnextvalue)|Appelez cette méthode pour obtenir la valeur suivante à partir de la `CAtlMap` objet.|
|[CAtlMap::GetStartPosition](#getstartposition)|Appelez cette méthode pour démarrer une itération de la carte.|
|[CAtlMap::GetValueAt](#getvalueat)|Appelez cette méthode pour récupérer la valeur stockée à une position donnée dans le `CAtlMap` objet.|
|[CAtlMap::InitHashTable](#inithashtable)|Appelez cette méthode pour initialiser la table de hachage.|
|[CAtlMap::IsEmpty](#isempty)|Appelez cette méthode pour tester un objet de mappage vide.|
|[CAtlMap::Lookup](#lookup)|Appelez cette méthode pour rechercher des clés ou des valeurs dans le `CAtlMap` objet.|
|[CAtlMap::Rehash](#rehash)|Appelez cette méthode pour rehash le `CAtlMap` objet.|
|[CAtlMap::RemoveAll](#removeall)|Appelez cette méthode pour supprimer tous les éléments à partir de la `CAtlMap` objet.|
|[CAtlMap::RemoveAtPos](#removeatpos)|Appelez cette méthode pour supprimer l’élément à la position donnée dans le `CAtlMap` objet.|
|[CAtlMap::RemoveKey](#removekey)|Appelez cette méthode pour supprimer un élément à partir de la `CAtlMap` objet, en fonction de la clé.|
|[CAtlMap::SetAt](#setat)|Appelez cette méthode pour insérer une paire de l’élément dans la classe map.|
|[CAtlMap::SetOptimalLoad](#setoptimalload)|Appelez cette méthode pour définir la charge optimale de la `CAtlMap` objet.|
|[CAtlMap::SetValueAt](#setvalueat)|Appelez cette méthode pour modifier la valeur stockée à une position donnée dans le `CAtlMap` objet.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|Remplace ou ajoute un nouvel élément à la `CAtlMap`.|

## <a name="remarks"></a>Notes

`CAtlMap` prend en charge un tableau de mappage d’un type donné, la gestion d’un tableau non ordonné d’éléments clés et leurs valeurs associées. Éléments (composé d’une clé et une valeur) sont stockés à l’aide d’un algorithme de hachage, ce qui permet une grande quantité de données à stocker et récupérer efficacement.

Le *KTraits* et *VTraits* paramètres sont des classes de traits qui contiennent tout code supplémentaire nécessaire pour copier ou déplacer des éléments.

Une alternative à `CAtlMap` est proposé par le [CRBMap](../../atl/reference/crbmap-class.md) classe. `CRBMap` également stocke les paires clé/valeur, mais présente des caractéristiques de performances différentes. Le temps nécessaire pour insérer un élément, rechercher une clé, ou supprimer une clé à partir d’un `CRBMap` objet est d’ordre *log(n)*, où *n* est le nombre d’éléments. Pour `CAtlMap`, toutes ces opérations prennent généralement un temps constant, même si le pire des cas peuvent être de commande *n*. Par conséquent, dans un cas classique, `CAtlMap` est plus rapide.

L’autre différence entre `CRBMap` et `CAtlMap` devient évidente lorsque l’itération sur les éléments stockées. Dans un `CRBMap`, les éléments sont consultées dans un ordre trié. Dans un `CAtlMap`, les éléments ne sont pas ordonnés, et aucun ordre ne peut être déduit.

Lorsqu’un petit nombre d’éléments doit être stockées, envisagez d’utiliser le [CSimpleMap](../../atl/reference/csimplemap-class.md) classe à la place.

Pour plus d’informations, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcoll.h

##  <a name="assertvalid"></a>  CAtlMap::AssertValid

Appelez cette méthode pour provoquer une assertion si le `CAtlMap` objet n’est pas valide.

```
void AssertValid() const;
```

### <a name="remarks"></a>Notes

Dans les versions debug, cette méthode provoque une assertion si le `CAtlMap` objet n’est pas valide.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlMap::CAtlMap](#catlmap).

##  <a name="catlmap"></a>  CAtlMap::CAtlMap

Constructeur.

```
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```

### <a name="parameters"></a>Paramètres

*nBins*<br/>
Le nombre d’emplacements en fournissant des pointeurs aux éléments stockées. Consultez la section Notes plus loin dans cette rubrique pour obtenir une explication des emplacements.

*fOptimalLoad*<br/>
Le taux de charge optimale.

*fLoThreshold*<br/>
Le seuil inférieur pour le taux de charge.

*fHiThreshold*<br/>
Le seuil supérieur pour le taux de charge.

*nBlockSize*<br/>
La taille du bloc.

### <a name="remarks"></a>Notes

`CAtlMap` fait référence à tous ses éléments stockées en commençant par créer un index à l’aide d’un algorithme de hachage sur la clé. Cet index fait référence à un « bin » qui contient un pointeur vers les éléments stockées. Si l’emplacement est déjà en cours d’utilisation, une liste liée est créée pour accéder aux éléments suivants. Parcourir une liste est inférieure à celle de l’accès direct à l’élément approprié, et par conséquent, la structure du plan doit équilibrer les besoins de stockage par rapport aux performances. Les paramètres par défaut ont été choisies pour donner de bons résultats dans la plupart des cas.

Le taux de charge est le rapport entre le nombre d’emplacements pour le nombre d’éléments stockés dans l’objet map. Lorsque la structure du plan est recalculée, le *fOptimalLoad* paramètre valeur sera utilisée pour calculer le nombre d’emplacements requis. Cette valeur peut être modifiée à l’aide de la [CAtlMap::SetOptimalLoad](#setoptimalload) (méthode).

Le *fLoThreshold* paramètre est la valeur plus faible que le taux de charge peut atteindre avant `CAtlMap` recalcule la taille optimale de la carte.

Le *fHiThreshold* paramètre est la valeur supérieure que le taux de charge peut atteindre avant le `CAtlMap` objet recalcule la taille optimale de la carte.

Ce processus de recalcul (appelé également) est activé par défaut. Si vous souhaitez désactiver ce processus, par exemple lors de la saisie d’un grand nombre de données en même temps, appelez le [CAtlMap::DisableAutoRehash](#disableautorehash) (méthode). Réactiver avec le [CAtlMap::EnableAutoRehash](#enableautorehash) (méthode).

Le *nBlockSize* paramètre est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est requis. Tailles de bloc supérieures réduisent les appels aux routines d’allocation de mémoire, mais utilisent davantage de ressources.

Avant que toutes les données peuvent être stockées, il est nécessaire d’initialiser la table de hachage avec un appel à [CAtlMap::InitHashTable](#inithashtable).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]

##  <a name="dtor"></a>  CAtlMap::~CAtlMap

Destructeur.

```
~CAtlMap() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

##  <a name="cpair_class"></a>  CAtlMap::CPair Class

Une classe qui contient les éléments clé / valeur.

```
class CPair : public __POSITION
```

### <a name="remarks"></a>Notes

Cette classe est utilisée par les méthodes [CAtlMap::GetNext](#getnext) et [CAtlMap::Lookup](#lookup) pour accéder aux éléments de clé et la valeur stockées dans la structure de mappage.

##  <a name="disableautorehash"></a>  CAtlMap::DisableAutoRehash

Appelez cette méthode pour désactiver aborderont automatique de la `CAtlMap` objet.

```
void DisableAutoRehash() throw();
```

### <a name="remarks"></a>Notes

Lorsque aborderont automatique est activé (ce qui est par défaut), le nombre de compartiments dans la table de hachage est recalculé automatiquement si la valeur de la charge (le rapport entre le nombre d’emplacements pour le nombre d’éléments stockés dans le tableau) dépasse les valeurs maximales ou minimales spécifié au moment de que la création de la carte.

`DisableAutoRehash` est particulièrement utile lorsqu’un grand nombre d’éléments sera ajouté à la fois à la carte. Au lieu de déclencher le processus rehashing chaque fois que les limites sont dépassées, il est plus efficace d’appeler `DisableAutoRehash`, ajoutez les éléments et enfin appeler [CAtlMap::EnableAutoRehash](#enableautorehash).

##  <a name="enableautorehash"></a>  CAtlMap::EnableAutoRehash

Appelez cette méthode pour activer aborderont automatique de la `CAtlMap` objet.

```
void EnableAutoRehash() throw();
```

### <a name="remarks"></a>Notes

Lorsque aborderont automatique est activé (ce qui est par défaut), le nombre de compartiments dans la table de hachage est recalculé automatiquement si la valeur de la charge (le rapport entre le nombre d’emplacements pour le nombre d’éléments stockés dans le tableau) dépasse les valeurs maximales ou minimales spécifié au moment de que la création de la carte.

`EnableAutoRefresh` est souvent utilisé après un appel à [CAtlMap::DisableAutoRehash](#disableautorehash).

##  <a name="getat"></a>  CAtlMap::GetAt

Appelez cette méthode pour retourner l’élément à une position spécifiée dans le mappage.

```
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

*key*<br/>
Paramètre de modèle qui spécifie le type de clé de la carte.

*value*<br/>
Paramètre de modèle qui spécifie le type de valeur de la carte.

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la paire d’éléments clé/valeur stockées dans le mappage actuel.

### <a name="remarks"></a>Notes

Dans les versions debug, une erreur d’assertion se produit si *pos* est égal à NULL.

##  <a name="getcount"></a>  CAtlMap::GetCount

Appelez cette méthode pour récupérer le nombre d’éléments dans le mappage.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre d’éléments dans l’objet map. Un seul élément est une paire clé/valeur.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlMap::CAtlMap](#catlmap).

##  <a name="gethashtablesize"></a>  CAtlMap::GetHashTableSize

Appelez cette méthode pour déterminer le nombre de compartiments dans la table de hachage de la carte.

```
UINT GetHashTableSize() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de compartiments dans la table de hachage. Consultez [CAtlMap::CAtlMap](#catlmap) pour obtenir une explication.

##  <a name="getkeyat"></a>  CAtlMap::GetKeyAt

Appelez cette méthode pour récupérer la clé stockée à la position donnée dans le `CAtlMap` objet.

```
const K& GetKeyAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valeur de retour

Retourne une référence à la clé stockée à la position donnée dans le `CAtlMap` objet.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlMap::CAtlMap](#catlmap).

##  <a name="getnext"></a>  CAtlMap::GetNext

Appelez cette méthode pour obtenir un pointeur vers l’élément suivant paire stockée dans le `CAtlMap` objet.

```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la paire d’éléments clé/valeur stockées dans la table suivante. Le *pos* position est mis à jour après chaque appel. Si l’élément récupéré est le dernier dans le mappage, *pos* est définie sur NULL.

##  <a name="getnextassoc"></a>  CAtlMap::GetNextAssoc

Obtient l’élément suivant pour une itération.

```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

*key*<br/>
Paramètre de modèle qui spécifie le type de clé de la carte.

*value*<br/>
Paramètre de modèle qui spécifie le type de valeur de la carte.

### <a name="remarks"></a>Notes

Le *pos* position est mis à jour après chaque appel. Si l’élément récupéré est le dernier dans le mappage, *pos* est définie sur NULL.

##  <a name="getnextkey"></a>  CAtlMap::GetNextKey

Appelez cette méthode pour récupérer la clé suivante dans le `CAtlMap` objet.

```
const K& GetNextKey(POSITION& pos) const throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valeur de retour

Retourne une référence à la clé suivante dans le mappage.

### <a name="remarks"></a>Notes

Met à jour le compteur de position actuelle, *pos*. S’il n’y a aucune entrée dans le mappage, le compteur de position est défini sur NULL.

##  <a name="getnextvalue"></a>  CAtlMap::GetNextValue

Appelez cette méthode pour obtenir la valeur suivante à partir de la `CAtlMap` objet.

```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valeur de retour

Retourne une référence à la valeur suivante dans le mappage.

### <a name="remarks"></a>Notes

Met à jour le compteur de position actuelle, *pos*. S’il n’y a aucune entrée dans le mappage, le compteur de position est défini sur NULL.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlMap::CAtlMap](#catlmap).

##  <a name="getstartposition"></a>  CAtlMap::GetStartPosition

Appelez cette méthode pour démarrer une itération de la carte.

```
POSITION GetStartPosition() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne que la position de début, ou NULL est retournée si le mappage est vide.

### <a name="remarks"></a>Notes

Appel de cette méthode pour démarrer une itération de la carte en retournant une POSITION de valeur qui peut être passé à la `GetNextAssoc` (méthode).

> [!NOTE]
>  La séquence d’itération n’est pas prévisible

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlMap::CAtlMap](#catlmap).

##  <a name="getvalueat"></a>  CAtlMap::GetValueAt

Appelez cette méthode pour récupérer la valeur stockée à une position donnée dans le `CAtlMap` objet.

```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

### <a name="return-value"></a>Valeur de retour

Retourne une référence à la valeur stockée à la position donnée dans le `CAtlMap` objet.

##  <a name="inithashtable"></a>  CAtlMap::InitHashTable

Appelez cette méthode pour initialiser la table de hachage.

```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```

### <a name="parameters"></a>Paramètres

*nBins*<br/>
Le nombre d’emplacements utilisés par la table de hachage. Consultez [CAtlMap::CAtlMap](#catlmap) pour obtenir une explication.

*bAllocNow*<br/>
Une indication de l’indicateur lors de la mémoire doit être allouée.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE lors de l’initialisation de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

`InitHashTable` doit être appelée avant que tous les éléments sont stockés dans la table de hachage.  Si cette méthode n’est pas appelée explicitement, elle sera appelée automatiquement la première fois qu’un élément est ajouté à l’aide du compte de l’emplacement spécifié par le `CAtlMap` constructeur.  Sinon, la carte sera initialisée en utilisant le nouveau nombre d’emplacement spécifié par le *nBins* paramètre.

Si le *bAllocNow* paramètre a la valeur false, la mémoire requise par la table de hachage n’est pas affectée jusqu'à ce qu’il est tout d’abord nécessaire. Cela peut être utile s’il est incertain si la carte doit être utilisée.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlMap::CAtlMap](#catlmap).

##  <a name="isempty"></a>  CAtlMap::IsEmpty

Appelez cette méthode pour tester un objet de mappage vide.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le mappage est vide, sinon FALSE.

##  <a name="kinargtype"></a>  CAtlMap::KINARGTYPE

Type utilisé lorsqu’une touche est passée comme argument d’entrée.

```
typedef KTraits::INARGTYPE KINARGTYPE;
```

##  <a name="koutargtype"></a>  CAtlMap::KOUTARGTYPE

Type utilisé pour une clé est retournée comme un argument de sortie.

```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```

##  <a name="lookup"></a>  CAtlMap::Lookup

Appelez cette méthode pour rechercher des clés ou des valeurs dans le `CAtlMap` objet.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la clé qui identifie l’élément à rechercher.

*value*<br/>
Variable qui reçoit la valeur recherché.

### <a name="return-value"></a>Valeur de retour

La première forme de la méthode retourne la valeur true si la clé est trouvée, sinon false. Les deuxième et troisième formes retournent un pointeur désignant un [CPair](#cpair_class) qui peut être utilisé comme position de pour les appels à [CAtlMap::GetNext](#getnext) et ainsi de suite.

### <a name="remarks"></a>Notes

`Lookup` utilise un algorithme de hachage pour trouver rapidement l’élément de carte contenant une clé correspondant exactement le paramètre de clé donné.

##  <a name="operator_at"></a>  CAtlMap::operator \[\]

Remplace ou ajoute un nouvel élément à la `CAtlMap`.

```
V& operator[](kinargtype key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
La clé de l’élément à ajouter ou remplacer.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à la valeur associée à la clé donnée.

### <a name="example"></a>Exemple

Si la clé existe déjà, l’élément est remplacé. Si la clé n’existe pas, un nouvel élément est ajouté. Consultez l’exemple de [CAtlMap::CAtlMap](#catlmap).

##  <a name="rehash"></a>  CAtlMap::Rehash

Appelez cette méthode pour rehash le `CAtlMap` objet.

```
void Rehash(UINT nBins = 0);
```

### <a name="parameters"></a>Paramètres

*nBins*<br/>
Nouveau nombre de compartiments à utiliser dans la table de hachage. Consultez [CAtlMap::CAtlMap](#catlmap) pour obtenir une explication.

### <a name="remarks"></a>Notes

Si *nBins* est 0, `CAtlMap` calcule un nombre raisonnable en fonction du nombre d’éléments de la carte et le paramètre de charge optimale. Normalement, le processus rehashing est automatique, mais si [CAtlMap::DisableAutoRehash](#disableautorehash) a été appelée, cette méthode effectue le redimensionnement nécessaire.

##  <a name="removeall"></a>  CAtlMap::RemoveAll

Appelez cette méthode pour supprimer tous les éléments à partir de la `CAtlMap` objet.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Notes

Efface le `CAtlMap` objet, la mémoire utilisée pour stocker les éléments.

##  <a name="removeatpos"></a>  CAtlMap::RemoveAtPos

Appelez cette méthode pour supprimer l’élément à la position donnée dans le `CAtlMap` objet.

```
void RemoveAtPos(POSITION pos) throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

### <a name="remarks"></a>Notes

Supprime la paire clé/valeur stockée à la position spécifiée. La mémoire utilisée pour stocker l’élément est libérée. La POSITION référencée par *pos* devient non valide et pendant que la POSITION de tous les autres éléments dans la carte reste valide, elles ne font pas nécessairement conserver le même ordre.

##  <a name="removekey"></a>  CAtlMap::RemoveKey

Appelez cette méthode pour supprimer un élément à partir de la `CAtlMap` objet, en fonction de la clé.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
La clé correspondant à la paire de l’élément que vous souhaitez supprimer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si la clé est trouvée et supprimée, FALSE en cas d’échec.

### <a name="example"></a>Exemple

Consultez l’exemple de [CAtlMap::CAtlMap](#catlmap).

##  <a name="setat"></a>  CAtlMap::SetAt

Appelez cette méthode pour insérer une paire de l’élément dans la classe map.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
La valeur de clé à ajouter à la `CAtlMap` objet.

*value*<br/>
La valeur à ajouter à la `CAtlMap` objet.

### <a name="return-value"></a>Valeur de retour

Retourne la position de la paire d’élément de clé/valeur dans la `CAtlMap` objet.

### <a name="remarks"></a>Notes

`SetAt` remplace un élément existant si une clé correspondante est trouvée. Si la clé est introuvable, une nouvelle paire clé/valeur est créée.

##  <a name="setoptimalload"></a>  CAtlMap::SetOptimalLoad

Appelez cette méthode pour définir la charge optimale de la `CAtlMap` objet.

```
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```

### <a name="parameters"></a>Paramètres

*fOptimalLoad*<br/>
Le taux de charge optimale.

*fLoThreshold*<br/>
Le seuil inférieur pour le taux de charge.

*fHiThreshold*<br/>
Le seuil supérieur pour le taux de charge.

*bRehashNow*<br/>
Indicateur spécifiant si la table de hachage doit être recalculée.

### <a name="remarks"></a>Notes

Cette méthode redéfinit la valeur de la charge optimale pour le `CAtlMap` objet. Consultez [CAtlMap::CAtlMap](#catlmap) pour une discussion sur les différents paramètres. Si *bRehashNow* a la valeur true et le nombre d’éléments est en dehors des valeurs minimales et maximales, la table de hachage est recalculée.

##  <a name="setvalueat"></a>  CAtlMap::SetValueAt

Appelez cette méthode pour modifier la valeur stockée à une position donnée dans le `CAtlMap` objet.

```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Le compteur de position, retourné par un appel précédent à [CAtlMap::GetNextAssoc](#getnextassoc) ou [CAtlMap::GetStartPosition](#getstartposition).

*value*<br/>
La valeur à ajouter à la `CAtlMap` objet.

### <a name="remarks"></a>Notes

Modifie l’élément de la valeur stockée à la position donnée dans le `CAtlMap` objet.

##  <a name="vinargtype"></a>  CAtlMap::VINARGTYPE

Type utilisé lorsqu’une valeur est passée comme argument d’entrée.

```
typedef VTraits::INARGTYPE VINARGTYPE;
```

##  <a name="voutargtype"></a>  CAtlMap::VOUTARGTYPE

Type utilisé lorsqu’une valeur est passée comme un argument de sortie.

```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```

##  <a name="m_key"></a>  CAtlMap::CPair::m_key

Le stockage de l’élément clé de membre de données.

```
const K m_key;
```

### <a name="parameters"></a>Paramètres

*K*<br/>
Le type d’élément clé.

##  <a name="m_value"></a>  CAtlMap::CPair::m_value

Le membre de données stocker l’élément de valeur.

```
V  m_value;
```

### <a name="parameters"></a>Paramètres

*V*<br/>
Le type d’élément de valeur.

## <a name="see-also"></a>Voir aussi

[Exemple de texte défilant](../../overview/visual-cpp-samples.md)<br/>
[Exemple UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
