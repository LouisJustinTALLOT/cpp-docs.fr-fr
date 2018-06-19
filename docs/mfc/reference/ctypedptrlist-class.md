---
title: CTypedPtrList (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTypedPtrList
- AFXTEMPL/CTypedPtrList
- AFXTEMPL/CTypedPtrList::AddHead
- AFXTEMPL/CTypedPtrList::AddTail
- AFXTEMPL/CTypedPtrList::GetAt
- AFXTEMPL/CTypedPtrList::GetHead
- AFXTEMPL/CTypedPtrList::GetNext
- AFXTEMPL/CTypedPtrList::GetPrev
- AFXTEMPL/CTypedPtrList::GetTail
- AFXTEMPL/CTypedPtrList::RemoveHead
- AFXTEMPL/CTypedPtrList::RemoveTail
- AFXTEMPL/CTypedPtrList::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CTypedPtrList [MFC], AddHead
- CTypedPtrList [MFC], AddTail
- CTypedPtrList [MFC], GetAt
- CTypedPtrList [MFC], GetHead
- CTypedPtrList [MFC], GetNext
- CTypedPtrList [MFC], GetPrev
- CTypedPtrList [MFC], GetTail
- CTypedPtrList [MFC], RemoveHead
- CTypedPtrList [MFC], RemoveTail
- CTypedPtrList [MFC], SetAt
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afb32a662c538526c4fe26f6abf46e56a42de728
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374586"
---
# <a name="ctypedptrlist-class"></a>CTypedPtrList (classe)
Fournit un « wrapper » de type sécurisé pour les objets de la classe `CPtrList`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class BASE_CLASS, class TYPE>  
class CTypedPtrList : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>Paramètres  
 `BASE_CLASS`  
 Classe de base de la classe de liste de pointeurs typés. doit être une classe de liste de pointeur ( `CObList` ou `CPtrList`).  
  
 `TYPE`  
 Type des éléments stockés dans la liste de la classe de base.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CTypedPtrList::AddHead](#addhead)|Ajoute un élément (ou tous les éléments dans une autre liste) au début de la liste (fait une nouvelle tête).|  
|[CTypedPtrList::AddTail](#addtail)|Ajoute un élément (ou tous les éléments dans une autre liste) à la fin de la liste (fait une nouvelle fin).|  
|[CTypedPtrList::GetAt](#getat)|Obtient l’élément à une position donnée.|  
|[CTypedPtrList::GetHead](#gethead)|Retourne l’élément principal de la liste (ne peut pas être vide).|  
|[CTypedPtrList::GetNext](#getnext)|Obtient l’élément suivant pour une itération.|  
|[CTypedPtrList::GetPrev](#getprev)|Obtient l’élément précédent pour une itération.|  
|[CTypedPtrList::GetTail](#gettail)|Retourne l’élément de fin de la liste (ne peut pas être vide).|  
|[CTypedPtrList::RemoveHead](#removehead)|Supprime l’élément de la tête de la liste.|  
|[CTypedPtrList::RemoveTail](#removetail)|Supprime l’élément de la fin de la liste.|  
|[CTypedPtrList::SetAt](#setat)|Définit l’élément à une position donnée.|  
  
## <a name="remarks"></a>Notes  
 Lorsque vous utilisez `CTypedPtrList` plutôt que `CObList` ou `CPtrList`, la fonctionnalité de vérification de type C++ vous aide à éliminer les erreurs provoquées par les types pointeur ne correspondent pas.  
  
 En outre, le `CTypedPtrList` wrapper effectue une grande partie des opérations de cast qui serait nécessaire si vous avez utilisé `CObList` ou `CPtrList`.  
  
 Étant donné que tous les `CTypedPtrList` fonctions sont en ligne, l’utilisation de ce modèle n’affecte pas considérablement la taille ou la vitesse de votre code.  
  
 Listes dérivé `CObList` peut être sérialisée, mais ceux dérivés de `CPtrList` ne peut pas.  
  
 Lorsqu’un `CTypedPtrList` objet est supprimé, ou lorsque ses éléments sont supprimés, seuls les pointeurs sont supprimées, pas les entités qu’ils référencent.  
  
 Pour plus d’informations sur l’utilisation de `CTypedPtrList`, consultez les articles [Collections](../../mfc/collections.md) et [Classes basées sur le modèle](../../mfc/template-based-classes.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple crée une instance de `CTypedPtrList`, ajoute un objet, sérialise la liste sur le disque, puis supprime l’objet :  
  
 [!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `BASE_CLASS`  
  
 `_CTypedPtrList`  
  
 `CTypedPtrList`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxtempl.h  
  
##  <a name="addhead"></a>  CTypedPtrList::AddHead  
 Cette fonction membre appelle `BASE_CLASS` **:: AddHead**.  
  
```  
POSITION AddHead(TYPE newElement);  
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>Paramètres  
 *TYPE*  
 Type des éléments stockés dans la liste de la classe de base.  
  
 `newElement`  
 Le pointeur d’objet à ajouter à cette liste. A **NULL** la valeur est autorisée.  
  
 `BASE_CLASS`  
 Classe de base de la classe de liste de pointeurs typés. doit être une classe de liste de pointeur ( [CObList](../../mfc/reference/coblist-class.md) ou [CPtrList](../../mfc/reference/cptrlist-class.md)).  
  
 `pNewList`  
 Un pointeur vers un autre [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) objet. Les éléments de `pNewList` sera ajouté à cette liste.  
  
### <a name="return-value"></a>Valeur de retour  
 La première version retourne le **POSITION** valeur de l’élément nouvellement inséré.  
  
### <a name="remarks"></a>Notes  
 La première version ajoute un nouvel élément avant le début de la liste. La deuxième version ajoute une autre liste d’éléments avant le début.  
  
##  <a name="addtail"></a>  CTypedPtrList::AddTail  
 Cette fonction membre appelle `BASE_CLASS` **:: AddTail**.  
  
```  
POSITION AddTail(TYPE newElement);  
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>Paramètres  
 *TYPE*  
 Type des éléments stockés dans la liste de la classe de base.  
  
 `newElement`  
 Le pointeur d’objet à ajouter à cette liste. A **NULL** la valeur est autorisée.  
  
 `BASE_CLASS`  
 Classe de base de la classe de liste de pointeurs typés. doit être une classe de liste de pointeur ( [CObList](../../mfc/reference/coblist-class.md) ou [CPtrList](../../mfc/reference/cptrlist-class.md)).  
  
 `pNewList`  
 Un pointeur vers un autre [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) objet. Les éléments de `pNewList` sera ajouté à cette liste.  
  
### <a name="return-value"></a>Valeur de retour  
 La première version retourne le **POSITION** valeur de l’élément nouvellement inséré.  
  
### <a name="remarks"></a>Notes  
 La première version ajoute un nouvel élément après la fin de la liste. La deuxième version ajoute une autre liste d’éléments après la fin de la liste.  
  
##  <a name="getat"></a>  CTypedPtrList::GetAt  
 Une variable de type **POSITION** est une clé pour la liste.  
  
```  
TYPE& GetAt(POSITION position);  
TYPE GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *TYPE*  
 Paramètre de modèle qui spécifie le type des éléments stockés dans la liste.  
  
 *Position*  
 A **POSITION** valeur retournée par une précédente `GetHeadPosition` ou **trouver** appel de fonction membre.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la liste est accessible via un pointeur vers un **CTypedPtrList const**, puis `GetAt` retourne un pointeur du type spécifié par le paramètre de modèle *TYPE*. Cela permet à la fonction doit être utilisé uniquement sur le côté droit d’une instruction d’assignation et qui protège donc la liste à partir de la modification.  
  
 Si la liste est accessible directement ou via un pointeur à une `CTypedPtrList`, puis `GetAt` retourne une référence à un pointeur du type spécifié par le paramètre de modèle *TYPE*. Cela permet la fonction doit être utilisé sur chaque côté d’une instruction d’assignation et par conséquent, les entrées de liste à modifier.  
  
### <a name="remarks"></a>Notes  
 Il n’est pas identique à un index, et vous ne pouvez pas utiliser un **POSITION** valeur vous-même. `GetAt` Récupère le `CObject` pointeur associé à une position donnée.  
  
 Vous devez vous assurer que votre **POSITION** valeur représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.  
  
 Cette fonction inline s’appelle `BASE_CLASS` **:: GetAt**.  
  
##  <a name="gethead"></a>  CTypedPtrList::GetHead  
 Obtient le pointeur qui représente l’élément principal de cette liste.  
  
```  
TYPE& GetHead();  
TYPE GetHead() const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *TYPE*  
 Paramètre de modèle qui spécifie le type des éléments stockés dans la liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la liste est accessible via un pointeur vers un **CTypedPtrList const**, puis `GetHead` retourne un pointeur du type spécifié par le paramètre de modèle *TYPE*. Cela permet à la fonction doit être utilisé uniquement sur le côté droit d’une instruction d’assignation et qui protège donc la liste à partir de la modification.  
  
 Si la liste est accessible directement ou via un pointeur à une `CTypedPtrList`, puis `GetHead` retourne une référence à un pointeur du type spécifié par le paramètre de modèle *TYPE*. Cela permet la fonction doit être utilisé sur chaque côté d’une instruction d’assignation et par conséquent, les entrées de liste à modifier.  
  
### <a name="remarks"></a>Notes  
 Vous devez vous assurer que la liste n’est pas vide avant d’appeler `GetHead`. Si la liste est vide, la version Debug de la bibliothèque Microsoft Foundation Class déclare. Utilisez [IsEmpty](../../mfc/reference/coblist-class.md#isempty) pour vérifier que la liste contient des éléments.  
  
##  <a name="getnext"></a>  CTypedPtrList::GetNext  
 Obtient l’élément de liste identifié par `rPosition`, puis définit `rPosition` à la **POSITION** valeur de l’entrée suivante dans la liste.  
  
```  
TYPE& GetNext(POSITION& rPosition);  
TYPE GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *TYPE*  
 Paramètre de modèle qui spécifie le type d’éléments contenus dans cette liste.  
  
 `rPosition`  
 Une référence à un **POSITION** valeur retournée par une précédente `GetNext`, `GetHeadPosition`, ou un autre appel de fonction membre.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la liste est accessible via un pointeur vers un **CTypedPtrList const**, puis `GetNext` retourne un pointeur du type spécifié par le paramètre de modèle *TYPE*. Cela permet à la fonction doit être utilisé uniquement sur le côté droit d’une instruction d’assignation et qui protège donc la liste à partir de la modification.  
  
 Si la liste est accessible directement ou via un pointeur à une `CTypedPtrList`, puis `GetNext` retourne une référence à un pointeur du type spécifié par le paramètre de modèle *TYPE*. Cela permet la fonction doit être utilisé sur chaque côté d’une instruction d’assignation et par conséquent, les entrées de liste à modifier.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser `GetNext` dans une boucle itération vers l’avant, si vous établissez la position initiale avec un appel à `GetHeadPosition` ou [CPtrList::Find](../../mfc/reference/coblist-class.md#find).  
  
 Vous devez vous assurer que votre **POSITION** valeur représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.  
  
 Si l’élément récupéré est le dernier dans la liste, puis la nouvelle valeur de `rPosition` a la valeur **NULL**.  
  
 Il est possible de supprimer un élément lors d’une itération. Consultez l’exemple de [CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat).  
  
##  <a name="getprev"></a>  CTypedPtrList::GetPrev  
 Obtient l’élément de liste identifié par `rPosition`, puis définit `rPosition` à la **POSITION** valeur de l’entrée précédente dans la liste.  
  
```  
TYPE& GetPrev(POSITION& rPosition);  
TYPE GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *TYPE*  
 Paramètre de modèle qui spécifie le type d’éléments contenus dans cette liste.  
  
 `rPosition`  
 Une référence à un **POSITION** valeur retournée par une précédente `GetPrev` ou un autre appel de fonction membre.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la liste est accessible via un pointeur vers un **CTypedPtrList const**, puis `GetPrev` retourne un pointeur du type spécifié par le paramètre de modèle *TYPE*. Cela permet à la fonction doit être utilisé uniquement sur le côté droit d’une instruction d’assignation et qui protège donc la liste à partir de la modification.  
  
 Si la liste est accessible directement ou via un pointeur à une `CTypedPtrList`, puis `GetPrev` retourne une référence à un pointeur du type spécifié par le paramètre de modèle *TYPE*. Cela permet la fonction doit être utilisé sur chaque côté d’une instruction d’assignation et par conséquent, les entrées de liste à modifier.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser `GetPrev` dans une boucle d’itération inverse si vous établissez la position initiale avec un appel à `GetTailPosition` ou **trouver**.  
  
 Vous devez vous assurer que votre **POSITION** valeur représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.  
  
 Si l’élément récupéré est le premier dans la liste, puis la nouvelle valeur de `rPosition` a la valeur **NULL**.  
  
##  <a name="gettail"></a>  CTypedPtrList::GetTail  
 Obtient le pointeur qui représente l’élément principal de cette liste.  
  
```  
TYPE& GetTail();  
TYPE GetTail() const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *TYPE*  
 Paramètre de modèle qui spécifie le type des éléments stockés dans la liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la liste est accessible via un pointeur vers un **CTypedPtrList const**, puis `GetTail` retourne un pointeur du type spécifié par le paramètre de modèle *TYPE*. Cela permet à la fonction doit être utilisé uniquement sur le côté droit d’une instruction d’assignation et qui protège donc la liste à partir de la modification.  
  
 Si la liste est accessible directement ou via un pointeur à une `CTypedPtrList`, puis `GetTail` retourne une référence à un pointeur du type spécifié par le paramètre de modèle *TYPE*. Cela permet la fonction doit être utilisé sur chaque côté d’une instruction d’assignation et par conséquent, les entrées de liste à modifier.  
  
### <a name="remarks"></a>Notes  
 Vous devez vous assurer que la liste n’est pas vide avant d’appeler `GetTail`. Si la liste est vide, la version Debug de la bibliothèque Microsoft Foundation Class déclare. Utilisez [IsEmpty](../../mfc/reference/coblist-class.md#isempty) pour vérifier que la liste contient des éléments.  
  
##  <a name="removehead"></a>  CTypedPtrList::RemoveHead  
 Supprime l’élément de la tête de la liste et le retourne.  
  
```  
TYPE RemoveHead();
```  
  
### <a name="parameters"></a>Paramètres  
 *TYPE*  
 Paramètre de modèle qui spécifie le type des éléments stockés dans la liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Le pointeur précédemment au début de la liste. Ce pointeur est de type spécifié par le paramètre de modèle *TYPE*.  
  
### <a name="remarks"></a>Notes  
 Vous devez vous assurer que la liste n’est pas vide avant d’appeler `RemoveHead`. Si la liste est vide, la version Debug de la bibliothèque Microsoft Foundation Class déclare. Utilisez [IsEmpty](../../mfc/reference/coblist-class.md#isempty) pour vérifier que la liste contient des éléments.  
  
##  <a name="removetail"></a>  CTypedPtrList::RemoveTail  
 Supprime l’élément de la fin de la liste et le retourne.  
  
```  
TYPE RemoveTail();
```  
  
### <a name="parameters"></a>Paramètres  
 *TYPE*  
 Paramètre de modèle qui spécifie le type des éléments stockés dans la liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Le pointeur précédemment à la fin de la liste. Ce pointeur est de type spécifié par le paramètre de modèle *TYPE*.  
  
### <a name="remarks"></a>Notes  
 Vous devez vous assurer que la liste n’est pas vide avant d’appeler `RemoveTail`. Si la liste est vide, la version Debug de la bibliothèque Microsoft Foundation Class déclare. Utilisez [IsEmpty](../../mfc/reference/coblist-class.md#isempty) pour vérifier que la liste contient des éléments.  
  
##  <a name="setat"></a>  CTypedPtrList::SetAt  
 Cette fonction membre appelle `BASE_CLASS` **:: SetAt**.  
  
```  
void SetAt(POSITION pos, TYPE newElement);
```  
  
### <a name="parameters"></a>Paramètres  
 `pos`  
 Le **POSITION** de l’élément à définir.  
  
 *TYPE*  
 Type des éléments stockés dans la liste de la classe de base.  
  
 `newElement`  
 Le pointeur d’objet à écrire dans la liste.  
  
### <a name="remarks"></a>Notes  
 Une variable de type **POSITION** est une clé pour la liste. Il n’est pas identique à un index, et vous ne pouvez pas utiliser un **POSITION** valeur vous-même. `SetAt` écrit le pointeur d’objet à la position spécifiée dans la liste.  
  
 Vous devez vous assurer que votre **POSITION** valeur représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.  
  
 Pour plus de la section Notes, consultez [CObList::SetAt](../../mfc/reference/coblist-class.md#setat).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC COLLECT](../../visual-cpp-samples.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classe de CPtrList](../../mfc/reference/cptrlist-class.md)   
 [CObList, classe](../../mfc/reference/coblist-class.md)
