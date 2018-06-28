---
title: CMap (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c477ee69b8bc8e824aae6df1f74ba97d2825524f
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039153"
---
# <a name="cmap-class"></a>CMap (classe)
Classe de collection de dictionnaires qui mappe des clés uniques à des valeurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class KEY, class ARG_KEY, class VALUE, class ARG_VALUE>class CMap : public CObject  
```  
  
#### <a name="parameters"></a>Paramètres  
 *KEY*  
 Classe de l’objet utilisé comme clé pour la carte.  
  
 *ARG_KEY*  
 Type de données utilisé pour *clé* arguments ; généralement une référence à *clé*.  
  
 *VALEUR*  
 Classe de l’objet stocké dans le mappage.  
  
 *ARG_VALUE*  
 Type de données utilisé pour *valeur* arguments ; généralement une référence à *valeur*.  
  
## <a name="members"></a>Membres  
  
### <a name="public-structures"></a>Structures publiques  
  
|Name|Description|  
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
|[CMap::IsEmpty](#isempty)|Vérifie si la condition de table vide (aucun élément).|  
|[CMap::Lookup](#lookup)|Recherche la valeur mappée à une clé donnée.|  
|[CMap::PGetFirstAssoc](#pgetfirstassoc)|Retourne un pointeur vers le premier élément.|  
|[CMap::PGetNextAssoc](#pgetnextassoc)|Obtient un pointeur vers l’élément suivant pour une itération.|  
|[CMap::PLookup](#plookup)|Retourne un pointeur vers une clé dont la valeur correspond à la valeur spécifiée.|  
|[CMap::RemoveAll](#removeall)|Supprime tous les éléments de cette carte.|  
|[CMap::RemoveKey](#removekey)|Supprime un élément spécifié par une clé.|  
|[CMap::SetAt](#setat)|Insère un élément dans l’objet map. remplace un élément existant si une clé est trouvée.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[[] De CMap::operator](#operator_at)|Insère un élément dans la classe map : substitution de l’opérateur pour `SetAt`.|  
  
## <a name="remarks"></a>Notes  
 Une fois que vous avez inséré une paire clé-valeur (élément) dans le mappage, vous pouvez efficacement récupérer ou supprimer la paire à l’aide de la clé d’accès. Vous pouvez également itérer sur tous les éléments dans le mappage.  
  
 Une variable de type **POSITION** est utilisé pour un autre accès aux entrées. Vous pouvez utiliser un **POSITION** pour « se souviennent » une entrée et une itération au sein de la carte. Vous pouvez considérer que cette itération est séquentielle par valeur de clé ; Il n’est pas le cas. La séquence des éléments récupérés est indéterminée.  
  
 Certaines fonctions membres de cet appel de la classe d’assistance globales des fonctions qui doivent être adaptées pour la plupart des utilisations de la `CMap` classe. Consultez [Assistants de classe de Collection](../../mfc/reference/collection-class-helpers.md) dans la section de Macros et objet Globals de la `MFC Reference`.  
  
 `CMap` substitue [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) pour prendre en charge la sérialisation et le vidage de ses éléments. Si un mappage est stocké dans une archive à l’aide de `Serialize`, chaque élément cartographique est sérialisé à son tour. L’implémentation par défaut de la `SerializeElements` fonction d’assistance effectue une écriture au niveau du bit. Pour plus d’informations sur la sérialisation des éléments de collecte de pointeur dérivé `CObject` ou autres types définis par l’utilisateur, consultez [Comment : définir une Collection de Type sécurisé](../../mfc/how-to-make-a-type-safe-collection.md).  
  
 Si vous avez besoin d’un vidage de diagnostic de chaque élément dans le mappage (les clés et valeurs), vous devez définir la profondeur du contexte de vidage à 1 ou supérieur.  
  
 Lorsqu’un `CMap` objet est supprimé, ou lorsque ses éléments sont supprimés, les clés et valeurs sont supprimés.  
  
 Dérivation de classe de carte est similaire à la dérivation de la liste. Consultez l’article [Collections](../../mfc/collections.md) pour une illustration de la dérivation d’une classe de liste de spécial.  
  
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
 *nBlockSize*  
 Spécifie la granularité d’allocation de mémoire pour l’extension de la carte.  
  
### <a name="remarks"></a>Notes  
 À mesure que la carte augmente, la mémoire est allouée en unités de *nBlockSize* entrées.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCollections#56](../../mfc/codesnippet/cpp/cmap-class_1.cpp)]  
  
##  <a name="cpair"></a>  CMap::CPair  
 Contient une valeur de clé et la valeur de l’objet associé.  
  
### <a name="remarks"></a>Notes  
 Il s’agit d’une structure imbriquée dans la classe [CMap](../../mfc/reference/cmap-class.md).  
  
 La structure est composée de deux champs :  
  
- **clé** la valeur réelle du type de clé.  
  
- **valeur** la valeur de l’objet associé.  
  
 Il est utilisé pour stocker les valeurs de retour à partir de [CMap::PLookup](#plookup), [CMap::PGetFirstAssoc](#pgetfirstassoc), et [CMap::PGetNextAssoc](#pgetnextassoc).  
  
### <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation, consultez l’exemple de [CMap::PLookup](#plookup).  
  
##  <a name="getcount"></a>  CMap::GetCount  
 Récupère le nombre d’éléments de la carte.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Nombre d'éléments.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CMap::Lookup](#lookup).  
  
##  <a name="gethashtablesize"></a>  CMap::GetHashTableSize  
 Détermine le nombre d’éléments dans la table de hachage de la carte.  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans la table de hachage.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCollections#57](../../mfc/codesnippet/cpp/cmap-class_2.cpp)]  
  
##  <a name="getnextassoc"></a>  CMap::GetNextAssoc  
 Récupère l’élément de mappage à `rNextPosition`, puis met à jour `rNextPosition` pour faire référence à l’élément suivant dans la carte.  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,
    KEY& rKey,
    VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *rNextPosition*  
 Spécifie une référence à un **POSITION** valeur retournée par une précédente `GetNextAssoc` ou `GetStartPosition` appeler.  
  
 *KEY*  
 Paramètre de modèle qui spécifie le type de clé de la carte.  
  
 *rKey*  
 Spécifie la clé retournée de l’élément récupéré.  
  
 *VALEUR*  
 Paramètre de modèle qui spécifie le type de valeur de la carte.  
  
 *rValue*  
 Spécifie la valeur retournée de l’élément récupéré.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est particulièrement utile pour l’itération au sein de tous les éléments dans le mappage. Notez que la séquence de position n’est pas nécessairement identique à la séquence de la valeur de clé.  
  
 Si l’élément récupéré est le dernier dans le mappage, puis la nouvelle valeur de *rNextPosition* a la valeur **NULL**.  
  
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
 Appelez cette méthode pour récupérer le nombre d’éléments de la carte.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="getstartposition"></a>  CMap::GetStartPosition  
 Démarre une itération de la carte en retournant un **POSITION** valeur qui peut être passé à un `GetNextAssoc` appeler.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A **POSITION** valeur qui indique une position de départ pour une itération de la carte ; ou **NULL** si la carte est vide.  
  
### <a name="remarks"></a>Notes  
 La séquence d’itération n’est pas prévisible ; Par conséquent, le « premier élément dans le mappage de » n’a aucune signification spéciale.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CMap::SetAt](#setat).  
  
##  <a name="inithashtable"></a>  CMap::InitHashTable  
 Initialise la table de hachage.  
  
```  
void InitHashTable(UINT hashSize, BOOL  bAllocNow = TRUE);  
```  
  
### <a name="parameters"></a>Paramètres  
 *hashSize*  
 Nombre d’entrées dans la table de hachage.  
  
 *bAllocNow*  
 Si **TRUE**, alloue de la table de hachage lors de l’initialisation ; sinon, la table est allouée lorsque nécessaire.  
  
### <a name="remarks"></a>Notes  
 Pour de meilleures performances, la taille de table de hachage doit être un nombre premier. Pour réduire les conflits, la taille doit être environ 20 pour cent supérieur le plus grand jeu de données prévu.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CMap::Lookup](#lookup).  
  
##  <a name="isempty"></a>  CMap::IsEmpty  
 Détermine si la carte est vide.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si ce mappage ne contient aucun élément ; Sinon, 0.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CMap::RemoveAll](#removeall).  
  
##  <a name="lookup"></a>  CMap::Lookup  
 Recherche la valeur mappée à une clé donnée.  
  
```  
BOOL Lookup(ARG_KEY key, VALUE& rValue) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *ARG_KEY*  
 Paramètre de modèle qui spécifie le type de la *clé* valeur.  
  
 *key*  
 Spécifie la clé qui identifie l’élément à rechercher.  
  
 *VALEUR*  
 Spécifie le type de la valeur à rechercher.  
  
 *rValue*  
 Reçoit la valeur recherchée.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément a été trouvé ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 `Lookup` utilise un algorithme de hachage pour trouver rapidement l’élément de carte avec une clé correspondant exactement à la clé donnée.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCollections#58](../../mfc/codesnippet/cpp/cmap-class_3.cpp)]  
  
##  <a name="operator_at"></a>  [] De CMap::operator  
 Pratique pour remplacer le `SetAt` fonction membre.  
  
```  
VALUE& operator[](arg_key key);
```  
  
### <a name="parameters"></a>Paramètres  
 *VALEUR*  
 Paramètre de modèle qui spécifie le type de la valeur de la carte.  
  
 *ARG_KEY*  
 Paramètre de modèle qui spécifie le type de la valeur de clé.  
  
 *key*  
 La clé utilisée pour récupérer la valeur de la carte.  
  
### <a name="remarks"></a>Notes  
 Par conséquent, il peut être utilisé uniquement sur le côté gauche d’une instruction d’assignation (une l-value). S’il n’existe aucun élément de carte avec la clé spécifiée, un nouvel élément est créé.  
  
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
 Un pointeur vers la première entrée de la carte ; consultez [CMap::CPair](#cpair). Si la carte ne contient aucune entrée, la valeur est **NULL**.  
  
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
 *pAssocRet*  
 Pointe vers une entrée de mappage retournée par une précédente [PGetNextAssoc](#pgetnextassoc) ou [CMap::PGetFirstAssoc](#pgetfirstassoc) appeler.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers l’entrée suivante dans l’objet map. consultez [CMap::CPair](#cpair). Si l’élément est le dernier dans le mappage, la valeur est **NULL**.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour itérer sur tous les éléments dans le mappage. Récupérer le premier élément avec un appel à `PGetFirstAssoc` , puis itérer la carte avec les appels successifs à `PGetNextAssoc`.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CMap::PGetFirstAssoc](#pgetfirstassoc).  
  
##  <a name="plookup"></a>  CMap::PLookup  
 Recherche la valeur mappée à une clé donnée.  
  
```  
const CPair* PLookup(ARG_KEY key) const;
CPair* PLookup(ARG_KEY key);  
```  
  
### <a name="parameters"></a>Paramètres  
 *key*  
 Clé de l’élément à rechercher.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers une structure de clés ; consultez [CMap::CPair](#cpair). Si aucune correspondance n’est trouvée, `CMap::PLookup` retourne `NULL`.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour rechercher un élément de carte avec une clé correspondant exactement à la clé donnée.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCollections#60](../../mfc/codesnippet/cpp/cmap-class_5.cpp)]  
  
##  <a name="removeall"></a>  CMap::RemoveAll  
 Supprime toutes les valeurs de ce mappage en appelant la fonction d’assistance globales **DestructElements**.  
  
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
 *ARG_KEY*  
 Paramètre de modèle qui spécifie le type de la clé.  
  
 *key*  
 Clé de l’élément à supprimer.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’entrée a été trouvée et supprimée avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le **DestructElements** fonction d’assistance est utilisée pour supprimer l’entrée.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CMap::SetAt](#setat).  
  
##  <a name="setat"></a>  CMap::SetAt  
 Le principal moyen d’insérer un élément dans un mappage.  
  
```  
void SetAt(ARG_KEY key, ARG_VALUE newValue);
```  
  
### <a name="parameters"></a>Paramètres  
 *ARG_KEY*  
 Paramètre de modèle qui spécifie le type de la *clé* paramètre.  
  
 *key*  
 Spécifie la clé du nouvel élément.  
  
 *ARG_VALUE*  
 Paramètre de modèle qui spécifie le type de la *newValue* paramètre.  
  
 *nouvelle valeur*  
 Spécifie la valeur du nouvel élément.  
  
### <a name="remarks"></a>Notes  
 Tout d’abord, la clé est recherchée. Si la clé est trouvée, la valeur correspondante est modifiée. Sinon, une nouvelle paire clé-valeur est créée.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCCollections#62](../../mfc/codesnippet/cpp/cmap-class_7.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC COLLECT](../../visual-cpp-samples.md)   
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)  
