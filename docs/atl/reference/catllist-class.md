---
title: Classe de CAtlList | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlList
- ATLCOLL/ATL::CAtlList
- ATLCOLL/ATL::CAtlList::INARGTYPE
- ATLCOLL/ATL::CAtlList::CAtlList
- ATLCOLL/ATL::CAtlList::AddHead
- ATLCOLL/ATL::CAtlList::AddHeadList
- ATLCOLL/ATL::CAtlList::AddTail
- ATLCOLL/ATL::CAtlList::AddTailList
- ATLCOLL/ATL::CAtlList::AssertValid
- ATLCOLL/ATL::CAtlList::Find
- ATLCOLL/ATL::CAtlList::FindIndex
- ATLCOLL/ATL::CAtlList::GetAt
- ATLCOLL/ATL::CAtlList::GetCount
- ATLCOLL/ATL::CAtlList::GetHead
- ATLCOLL/ATL::CAtlList::GetHeadPosition
- ATLCOLL/ATL::CAtlList::GetNext
- ATLCOLL/ATL::CAtlList::GetPrev
- ATLCOLL/ATL::CAtlList::GetTail
- ATLCOLL/ATL::CAtlList::GetTailPosition
- ATLCOLL/ATL::CAtlList::InsertAfter
- ATLCOLL/ATL::CAtlList::InsertBefore
- ATLCOLL/ATL::CAtlList::IsEmpty
- ATLCOLL/ATL::CAtlList::MoveToHead
- ATLCOLL/ATL::CAtlList::MoveToTail
- ATLCOLL/ATL::CAtlList::RemoveAll
- ATLCOLL/ATL::CAtlList::RemoveAt
- ATLCOLL/ATL::CAtlList::RemoveHead
- ATLCOLL/ATL::CAtlList::RemoveHeadNoReturn
- ATLCOLL/ATL::CAtlList::RemoveTail
- ATLCOLL/ATL::CAtlList::RemoveTailNoReturn
- ATLCOLL/ATL::CAtlList::SetAt
- ATLCOLL/ATL::CAtlList::SwapElements
dev_langs:
- C++
helpviewer_keywords:
- CAtlList class
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4bfe961ef3ac02a0ed068b8cc2b74f2a6cce22ae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366430"
---
# <a name="catllist-class"></a>Classe de CAtlList
Cette classe fournit des méthodes pour créer et gérer un objet de liste.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename E, class ETraits = CElementTraits<E>>  
class CAtlList
```  
  
#### <a name="parameters"></a>Paramètres  
 `E`  
 Type de l’élément.  
  
 `ETraits`  
 Le code utilisé pour copier ou déplacer des éléments. Consultez [CElementTraits classe](../../atl/reference/celementtraits-class.md) pour plus d’informations.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlList::INARGTYPE](#inargtype)||  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlList::CAtlList](#catllist)|Constructeur.|  
|[CAtlList :: ~ CAtlList](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlList::AddHead](#addhead)|Appelez cette méthode pour ajouter un élément au début de la liste.|  
|[CAtlList::AddHeadList](#addheadlist)|Appelez cette méthode pour ajouter une liste existante vers le début de la liste.|  
|[CAtlList::AddTail](#addtail)|Appelez cette méthode pour ajouter un élément à la fin de cette liste.|  
|[CAtlList::AddTailList](#addtaillist)|Appelez cette méthode pour ajouter une liste existante à la fin de cette liste.|  
|[CAtlList::AssertValid](#assertvalid)|Appelez cette méthode pour confirmer la validité de la liste.|  
|[CAtlList::Find](#find)|Appelez cette méthode pour rechercher la liste de l’élément spécifié.|  
|[CAtlList::FindIndex](#findindex)|Appelez cette méthode pour obtenir la position d’un élément, une valeur d’index.|  
|[CAtlList::GetAt](#getat)|Appelez cette méthode pour retourner l’élément à la position spécifiée dans la liste.|  
|[CAtlList::GetCount](#getcount)|Appelez cette méthode pour retourner le nombre d’objets dans la liste.|  
|[CAtlList::GetHead](#gethead)|Appelez cette méthode pour retourner l’élément au début de la liste.|  
|[CAtlList::GetHeadPosition](#getheadposition)|Appelez cette méthode pour obtenir la position de la tête de la liste.|  
|[CAtlList::GetNext](#getnext)|Appelez cette méthode pour retourner l’élément suivant dans la liste.|  
|[CAtlList::GetPrev](#getprev)|Appelez cette méthode pour retourner l’élément précédent dans la liste.|  
|[CAtlList::GetTail](#gettail)|Appelez cette méthode pour retourner l’élément à la fin de la liste.|  
|[CAtlList::GetTailPosition](#gettailposition)|Appelez cette méthode pour obtenir la position de la fin de la liste.|  
|[CAtlList::InsertAfter](#insertafter)|Appelez cette méthode pour insérer un nouvel élément dans la liste après la position spécifiée.|  
|[CAtlList::InsertBefore](#insertbefore)|Appelez cette méthode pour insérer un nouvel élément dans la liste avant la position spécifiée.|  
|[CAtlList::IsEmpty](#isempty)|Appelez cette méthode pour déterminer si la liste est vide.|  
|[CAtlList::MoveToHead](#movetohead)|Appelez cette méthode pour déplacer l’élément spécifié au début de la liste.|  
|[CAtlList::MoveToTail](#movetotail)|Appelez cette méthode pour déplacer l’élément spécifié à la fin de la liste.|  
|[CAtlList::RemoveAll](#removeall)|Appelez cette méthode pour supprimer tous les éléments de la liste.|  
|[CAtlList::RemoveAt](#removeat)|Appelez cette méthode pour supprimer un seul élément dans la liste.|  
|[CAtlList::RemoveHead](#removehead)|Appelez cette méthode pour supprimer l’élément au début de la liste.|  
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|Appelez cette méthode pour supprimer l’élément au début de la liste sans retourner une valeur.|  
|[CAtlList::RemoveTail](#removetail)|Appelez cette méthode pour supprimer l’élément à la fin de la liste.|  
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|Appelez cette méthode pour supprimer l’élément à la fin de la liste sans retourner une valeur.|  
|[CAtlList::SetAt](#setat)|Appelez cette méthode pour définir la valeur de l’élément à une position donnée dans la liste.|  
|[CAtlList::SwapElements](#swapelements)|Appelez cette méthode pour remplacer les éléments de la liste.|  
  
## <a name="remarks"></a>Notes  
 La `CAtlList` classe prend en charge les listes ordonnées d’objets non uniques accessibles séquentiellement ou par valeur. `CAtlList` listes se comportent comme une liste doublement liée. Chaque liste a un début et une fin, et les nouveaux éléments (ou les listes dans certains cas) peuvent être ajoutés à chaque extrémité de la liste, ou insérer avant ou après des éléments spécifiques.  
  
 La plupart de la `CAtlList` méthodes utilisent une valeur de position. Cette valeur est utilisée par les méthodes pour faire référence à l’emplacement mémoire réel où les éléments sont stockés et ne doivent pas être calculées ou prédit directement. S’il est nécessaire pour accéder à la *n*élément th dans la liste, la méthode [CAtlList::FindIndex](#findindex) retournera la valeur correspondante de la position d’un index donné. Les méthodes [CAtlList::GetNext](#getnext) et [CAtlList::GetPrev](#getprev) peut être utilisé pour effectuer une itération au sein des objets de la liste.  
  
 Pour plus d’informations sur les classes de collection disponibles avec ATL, consultez [Classes de Collection ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcoll.h  
  
##  <a name="addhead"></a>  CAtlList::AddHead  
 Appelez cette méthode pour ajouter un élément au début de la liste.  
  
```
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```  
  
### <a name="parameters"></a>Paramètres  
 `element`  
 Le nouvel élément.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la position de l’élément qui vient d’être ajouté.  
  
### <a name="remarks"></a>Notes  
 Si la première version est utilisée, un élément vide est créé à l’aide de son constructeur par défaut, plutôt que son constructeur de copie.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]  
  
##  <a name="addheadlist"></a>  CAtlList::AddHeadList  
 Appelez cette méthode pour ajouter une liste existante vers le début de la liste.  
  
```
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```  
  
### <a name="parameters"></a>Paramètres  
 `plNew`  
 La liste à ajouter.  
  
### <a name="remarks"></a>Notes  
 La liste désignée par `plNew` est inséré au début de la liste existante. Dans les versions debug, un échec d’assertion se produit si `plNew` est égal à NULL.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]  
  
##  <a name="addtail"></a>  CAtlList::AddTail  
 Appelez cette méthode pour ajouter un élément à la fin de cette liste.  
  
```
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```  
  
### <a name="parameters"></a>Paramètres  
 `element`  
 Élément à ajouter.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la POSITION de l’élément qui vient d’être ajouté.  
  
### <a name="remarks"></a>Notes  
 Si la première version est utilisée, un élément vide est créé à l’aide de son constructeur par défaut, plutôt que son constructeur de copie. L’élément est ajouté à la fin de la liste, et par conséquent, il devient alors la fin. Cette méthode peut être utilisée avec une liste vide.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]  
  
##  <a name="addtaillist"></a>  CAtlList::AddTailList  
 Appelez cette méthode pour ajouter une liste existante à la fin de cette liste.  
  
```
void AddTailList(const CAtlList<E, ETraits>* plNew);
```  
  
### <a name="parameters"></a>Paramètres  
 `plNew`  
 La liste à ajouter.  
  
### <a name="remarks"></a>Notes  
 La liste désignée par `plNew` est inséré après le dernier élément (le cas échéant) de l’objet de liste. Le dernier élément dans le `plNew` liste devient donc la fin. Dans les versions debug, un échec d’assertion se produit si *plNew* est égal à NULL.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]  
  
##  <a name="assertvalid"></a>  CAtlList::AssertValid  
 Appelez cette méthode pour confirmer la validité de la liste.  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>Notes  
 Dans les versions debug, un échec d’assertion se produit si l’objet de liste n’est pas valide. Pour être valide, une liste vide doit avoir à la fois les emplacements qui pointe sur la valeur NULL, et une liste qui n’est pas vide doit avoir à la fois les emplacements pointant vers des adresses valides.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]  
  
##  <a name="catllist"></a>  CAtlList::CAtlList  
 Constructeur.  
  
```
CAtlList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nBlockSize`  
 La taille du bloc.  
  
### <a name="remarks"></a>Notes  
 Le constructeur de la `CAtlList` objet. La taille de bloc est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est requis. Tailles de bloc supérieures réduisent les appels aux routines d’allocation de mémoire, mais utilisent davantage de ressources.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]  
  
##  <a name="dtor"></a>  CAtlList :: ~ CAtlList  
 Destructeur.  
  
```
~CAtlList() throw();
```  
  
### <a name="remarks"></a>Notes  
 Libère toutes les ressources attribuées, y compris un appel à [CAtlList::RemoveAll](#removeall) pour supprimer tous les éléments de la liste.  
  
 Dans les versions debug, un échec d’assertion se produit si la liste contient toujours des éléments après l’appel à `RemoveAll`.  
  
##  <a name="find"></a>  CAtlList::Find  
 Appelez cette méthode pour rechercher la liste de l’élément spécifié.  
  
```
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `element`  
 L’élément à trouver dans la liste.  
  
 `posStartAfter`  
 La position de début de la recherche. Si aucune valeur n’est spécifiée, la recherche commence par l’élément head.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur POSITION de l’élément s’il existe, sinon retourne NULL.  
  
### <a name="remarks"></a>Notes  
 Dans les versions debug, un échec d’assertion se produit si l’objet de liste n’est pas valide, ou si le `posStartAfter` est hors limites.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]  
  
##  <a name="findindex"></a>  CAtlList::FindIndex  
 Appelez cette méthode pour obtenir la position d’un élément, une valeur d’index.  
  
```
POSITION FindIndex(size_t iElement) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `iElement`  
 Index de base zéro de l’élément de liste requise.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de la POSITION correspondante, ou NULL si `iElement` est hors limites.  
  
### <a name="remarks"></a>Notes  
 Cette méthode retourne la POSITION correspondant à une valeur d’index donnée, ce qui permet d’accéder à la *n*élément th dans la liste.  
  
 Dans les versions debug, un échec d’assertion se produit si l’objet de liste n’est pas valide.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]  
  
##  <a name="getat"></a>  CAtlList::GetAt  
 Appelez cette méthode pour retourner l’élément à la position spécifiée dans la liste.  
  
```
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pos`  
 La valeur de POSITION en spécifiant un élément particulier.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à, ou une copie de l’élément.  
  
### <a name="remarks"></a>Notes  
 Si la liste est **const**, `GetAt` retourne une copie de l’élément. Cela permet à la méthode à être utilisé uniquement sur le côté droit d’une instruction d’assignation et protège la liste à partir de la modification.  
  
 Si la liste n’est pas **const**, `GetAt` retourne une référence à l’élément. Cela permet la méthode à utiliser sur chaque côté d’une instruction d’assignation et par conséquent, les entrées de liste à modifier.  
  
 Dans les versions debug, un échec d’assertion se produit si `pos` est égal à NULL.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CAtlList::FindIndex](#findindex).  
  
##  <a name="getcount"></a>  CAtlList::GetCount  
 Appelez cette méthode pour retourner le nombre d’objets dans la liste.  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nombre d'éléments figurant dans la liste.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CAtlList::Find](#find).  
  
##  <a name="gethead"></a>  CAtlList::GetHead  
 Appelez cette méthode pour retourner l’élément au début de la liste.  
  
```
E& GetHead() throw();
const E& GetHead() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une référence, ou une copie de l’élément au début de la liste.  
  
### <a name="remarks"></a>Notes  
 Si la liste est **const**, `GetHead` retourne une copie de l’élément au début de la liste. Cela permet à la méthode à être utilisé uniquement sur le côté droit d’une instruction d’assignation et protège la liste à partir de la modification.  
  
 Si la liste n’est pas **const**, `GetHead` retourne une référence à l’élément au début de la liste. Cela permet la méthode à utiliser sur chaque côté d’une instruction d’assignation et par conséquent, les entrées de liste à modifier.  
  
 Dans les versions debug, un échec d’assertion se produit si le début de la liste de pointe avec la valeur NULL.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CAtlList::AddHead](#addhead).  
  
##  <a name="getheadposition"></a>  CAtlList::GetHeadPosition  
 Appelez cette méthode pour obtenir la position de la tête de la liste.  
  
```
POSITION GetHeadPosition() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur POSITION correspondant à l’élément au début de la liste.  
  
### <a name="remarks"></a>Notes  
 Si la liste est vide, la valeur retournée est NULL.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]  
  
##  <a name="getnext"></a>  CAtlList::GetNext  
 Appelez cette méthode pour retourner l’élément suivant dans la liste.  
  
```
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pos`  
 Une valeur POSITION, retournée par un appel précédent à `GetNext`, [CAtlList::GetHeadPosition](#getheadposition), ou d’autres `CAtlList` (méthode).  
  
### <a name="return-value"></a>Valeur de retour  
 Si la liste est **const**, `GetNext` retourne une copie de l’élément suivant de la liste. Cela permet à la méthode à être utilisé uniquement sur le côté droit d’une instruction d’assignation et protège la liste à partir de la modification.  
  
 Si la liste n’est pas **const**, `GetNext` retourne une référence à l’élément suivant de la liste. Cela permet la méthode à utiliser sur chaque côté d’une instruction d’assignation et par conséquent, les entrées de liste à modifier.  
  
### <a name="remarks"></a>Notes  
 Le compteur de POSITION, `pos`, est mis à jour pour pointer vers l’élément suivant dans la liste, ou NULL si aucun élément plus. Dans les versions debug, un échec d’assertion se produit si `pos` est égal à NULL.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CAtlList::GetHeadPosition](#getheadposition).  
  
##  <a name="getprev"></a>  CAtlList::GetPrev  
 Appelez cette méthode pour retourner l’élément précédent dans la liste.  
  
```
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pos`  
 Une valeur POSITION, retournée par un appel précédent à `GetPrev`, [CAtlList::GetTailPosition](#gettailposition), ou d’autres `CAtlList` (méthode).  
  
### <a name="return-value"></a>Valeur de retour  
 Si la liste est **const**, `GetPrev` retourne une copie d’un élément de la liste. Cela permet à la méthode à être utilisé uniquement sur le côté droit d’une instruction d’assignation et protège la liste à partir de la modification.  
  
 Si la liste n’est pas **const**, `GetPrev` retourne une référence à un élément de la liste. Cela permet la méthode à utiliser sur chaque côté d’une instruction d’assignation et par conséquent, les entrées de liste à modifier.  
  
### <a name="remarks"></a>Notes  
 Le compteur de POSITION, `pos`, est mis à jour pour pointer vers l’élément précédent dans la liste, ou NULL si aucun élément plus. Dans les versions debug, un échec d’assertion se produit si `pos` est égal à NULL.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CAtlList::GetTailPosition](#gettailposition).  
  
##  <a name="gettail"></a>  CAtlList::GetTail  
 Appelez cette méthode pour retourner l’élément à la fin de la liste.  
  
```
E& GetTail() throw();
const E& GetTail() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une référence, ou une copie de l’élément à la fin de la liste.  
  
### <a name="remarks"></a>Notes  
 Si la liste est **const**, `GetTail` retourne une copie de l’élément au début de la liste. Cela permet à la méthode à être utilisé uniquement sur le côté droit d’une instruction d’assignation et protège la liste à partir de la modification.  
  
 Si la liste n’est pas **const**, `GetTail` retourne une référence à l’élément au début de la liste. Cela permet la méthode à utiliser sur chaque côté d’une instruction d’assignation et par conséquent, les entrées de liste à modifier.  
  
 Dans les versions debug, un échec d’assertion se produit si la fin de la liste de pointe avec la valeur NULL.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CAtlList::AddTail](#addtail).  
  
##  <a name="gettailposition"></a>  CAtlList::GetTailPosition  
 Appelez cette méthode pour obtenir la position de la fin de la liste.  
  
```
POSITION GetTailPosition() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur POSITION correspondant à l’élément à la fin de la liste.  
  
### <a name="remarks"></a>Notes  
 Si la liste est vide, la valeur retournée est NULL.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]  
  
##  <a name="inargtype"></a>  CAtlList::INARGTYPE  
 Type utilisé lorsqu’un élément est passé comme argument d’entrée.  
  
```
typedef ETraits::INARGTYPE INARGTYPE;
```  
  
##  <a name="insertafter"></a>  CAtlList::InsertAfter  
 Appelez cette méthode pour insérer un nouvel élément dans la liste après la position spécifiée.  
  
```
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```  
  
### <a name="parameters"></a>Paramètres  
 `pos`  
 La valeur de POSITION après lequel le nouvel élément doit être inséré.  
  
 `element`  
 L’élément à insérer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de la POSITION du nouvel élément.  
  
### <a name="remarks"></a>Notes  
 Dans les versions debug, un échec d’assertion se produit si la liste n’est pas valide, si l’insertion échoue, ou si une tentative est faite pour insérer l’élément après la fin.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]  
  
##  <a name="insertbefore"></a>  CAtlList::InsertBefore  
 Appelez cette méthode pour insérer un nouvel élément dans la liste avant la position spécifiée.  
  
```
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```  
  
### <a name="parameters"></a>Paramètres  
 `pos`  
 Le nouvel élément est inséré dans la liste avant cette valeur POSITION.  
  
 `element`  
 L’élément à insérer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur de la POSITION du nouvel élément.  
  
### <a name="remarks"></a>Notes  
 Dans les versions debug, un échec d’assertion se produit si la liste n’est pas valide, si l’insertion échoue, ou si une tentative est faite pour insérer l’élément avant le début.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]  
  
##  <a name="isempty"></a>  CAtlList::IsEmpty  
 Appelez cette méthode pour déterminer si la liste est vide.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true si la liste ne contient pas d’objets, sinon, false.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]  
  
##  <a name="movetohead"></a>  CAtlList::MoveToHead  
 Appelez cette méthode pour déplacer l’élément spécifié au début de la liste.  
  
```
void MoveToHead(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pos`  
 La valeur de la POSITION de l’élément à déplacer.  
  
### <a name="remarks"></a>Notes  
 L’élément spécifié est déplacée depuis sa position actuelle vers le début de la liste. Dans les versions debug, un échec d’assertion se produit si `pos` est égal à NULL.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]  
  
##  <a name="movetotail"></a>  CAtlList::MoveToTail  
 Appelez cette méthode pour déplacer l’élément spécifié à la fin de la liste.  
  
```
void MoveToTail(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pos`  
 La valeur de la POSITION de l’élément à déplacer.  
  
### <a name="remarks"></a>Notes  
 L’élément spécifié est déplacée depuis sa position actuelle et la fin de la liste. Dans les versions debug, un échec d’assertion se produit si `pos` est égal à NULL.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CAtlList::MoveToHead](#movetohead).  
  
##  <a name="removeall"></a>  CAtlList::RemoveAll  
 Appelez cette méthode pour supprimer tous les éléments de la liste.  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode supprime tous les éléments de la liste et libère la mémoire allouée. Dans les versions débogue un ATLASSERT ; sera déclenchée si tous les éléments ne sont pas supprimés, ou si la structure de liste a été endommagée.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CAtlList::IsEmpty](#isempty).  
  
##  <a name="removeat"></a>  CAtlList::RemoveAt  
 Appelez cette méthode pour supprimer un seul élément dans la liste.  
  
```
void RemoveAt(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `pos`  
 La valeur de la POSITION de l’élément à supprimer.  
  
### <a name="remarks"></a>Notes  
 L’élément référencé par `pos` est supprimé, et la mémoire est libérée. Il est acceptable d’utiliser `RemoveAt` pour supprimer la tête ou queue de la liste.  
  
 Dans les versions debug, un échec d’assertion se produit si la liste n’est pas valide ou si la liste de mémoire qui ne fait pas partie de la structure de la liste entraîne une suppression de l’élément.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]  
  
##  <a name="removehead"></a>  CAtlList::RemoveHead  
 Appelez cette méthode pour supprimer l’élément au début de la liste.  
  
```
E RemoveHead();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’élément au début de la liste.  
  
### <a name="remarks"></a>Notes  
 L’élément head est supprimé de la liste, et la mémoire est libérée. Une copie de l’élément est retournée. Dans les versions debug, un échec d’assertion se produit si la liste est vide.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]  
  
##  <a name="removeheadnoreturn"></a>  CAtlList::RemoveHeadNoReturn  
 Appelez cette méthode pour supprimer l’élément au début de la liste sans retourner une valeur.  
  
```
void RemoveHeadNoReturn() throw();
```  
  
### <a name="remarks"></a>Notes  
 L’élément head est supprimé de la liste, et la mémoire est libérée. Dans les versions debug, un échec d’assertion se produit si la liste est vide.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CAtlList::IsEmpty](#isempty).  
  
##  <a name="removetail"></a>  CAtlList::RemoveTail  
 Appelez cette méthode pour supprimer l’élément à la fin de la liste.  
  
```
E RemoveTail();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’élément à la fin de la liste.  
  
### <a name="remarks"></a>Notes  
 L’élément de fin est supprimé de la liste, et la mémoire est libérée. Une copie de l’élément est retournée. Dans les versions debug, un échec d’assertion se produit si la liste est vide.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]  
  
##  <a name="removetailnoreturn"></a>  CAtlList::RemoveTailNoReturn  
 Appelez cette méthode pour supprimer l’élément à la fin de la liste sans retourner une valeur.  
  
```
void RemoveTailNoReturn() throw();
```  
  
### <a name="remarks"></a>Notes  
 L’élément de fin est supprimé de la liste, et la mémoire est libérée. Dans les versions debug, un échec d’assertion se produit si la liste est vide.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CAtlList::IsEmpty](#isempty).  
  
##  <a name="setat"></a>  CAtlList::SetAt  
 Appelez cette méthode pour définir la valeur de l’élément à une position donnée dans la liste.  
  
```
void SetAt(POSITION pos, INARGTYPE element);
```  
  
### <a name="parameters"></a>Paramètres  
 `pos`  
 La valeur POSITION correspondant à l’élément à modifier.  
  
 `element`  
 La nouvelle valeur de l’élément.  
  
### <a name="remarks"></a>Notes  
 Remplace la valeur existante avec `element`. Dans les versions debug, un échec d’assertion se produit si `pos` est égal à NULL.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]  
  
##  <a name="swapelements"></a>  CAtlList::SwapElements  
 Appelez cette méthode pour remplacer les éléments de la liste.  
  
```
void SwapElements(POSITION pos1, POSITION pos2) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *pos1*  
 La première valeur POSITION.  
  
 *pos2*  
 La deuxième valeur POSITION.  
  
### <a name="remarks"></a>Notes  
 Échange les éléments à deux positions spécifiées. Dans les versions debug, un échec d’assertion se produit si une valeur de position est égale à NULL.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [CList (classe)](../../mfc/reference/clist-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
