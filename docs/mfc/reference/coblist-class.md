---
title: Classe de cObList | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CObList
- AFXCOLL/CObList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
dev_langs:
- C++
helpviewer_keywords:
- objects [C++], lists of
- CObList class
- lists, object
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: dc95f76be56f00f4779724facaf668a72b3d5ed6
ms.contentlocale: fr-fr
ms.lasthandoff: 02/24/2017

---
# <a name="coblist-class"></a>CObList (classe)
fSupports les listes ordonnées d’identifiant `CObject` pointeurs accessibles séquentiellement ou par le pointeur de valeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CObList : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CObList::CObList](#coblist)|Construit une liste vide pour `CObject` des pointeurs.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CObList::AddHead](#addhead)|Ajoute un élément (ou tous les éléments dans une autre liste) au début de la liste (fait une nouvelle tête).|  
|[CObList::AddTail](#addtail)|Ajoute un élément (ou tous les éléments dans une autre liste) à la fin de la liste (fait une nouvelle fin).|  
|[CObList::Find](#find)|Obtient la position d’un élément spécifié par la valeur du pointeur.|  
|[CObList::FindIndex](#findindex)|Obtient la position d’un élément spécifié par un index de base zéro.|  
|[CObList::GetAt](#getat)|Obtient l’élément à une position donnée.|  
|[CObList::GetCount](#getcount)|Renvoie le nombre d’éléments dans cette liste.|  
|[CObList::GetHead](#gethead)|Retourne l’élément head de la liste (ne peut pas être vide).|  
|[CObList::GetHeadPosition](#getheadposition)|Retourne la position de l’élément head de la liste.|  
|[CObList::GetNext](#getnext)|Obtient l’élément suivant pour l’itération.|  
|[CObList::GetPrev](#getprev)|Obtient l’élément précédent pour l’itération.|  
|[CObList::GetSize](#getsize)|Renvoie le nombre d’éléments dans cette liste.|  
|[CObList::GetTail](#gettail)|Retourne l’élément de fin de la liste (ne peut pas être vide).|  
|[CObList::GetTailPosition](#gettailposition)|Retourne la position de l’élément de fin de la liste.|  
|[CObList::InsertAfter](#insertafter)|Insère un nouvel élément après une position donnée.|  
|[CObList::InsertBefore](#insertbefore)|Insère un élément avant une position donnée.|  
|[CObList::IsEmpty](#isempty)|Vérifie si la condition de la liste vide (aucun élément).|  
|[CObList::RemoveAll](#removeall)|Supprime tous les éléments de cette liste.|  
|[CObList::RemoveAt](#removeat)|Supprime un élément de cette liste, spécifiée par position.|  
|[CObList::RemoveHead](#removehead)|Supprime l’élément au début de la liste.|  
|[CObList::RemoveTail](#removetail)|Supprime l’élément de la fin de la liste.|  
|[CObList::SetAt](#setat)|Définit l’élément à une position donnée.|  
  
## <a name="remarks"></a>Remarques  
 `CObList`listes se comportent comme des listes à chaînage double.  
  
 Une variable de type **POSITION** est une clé pour la liste. Vous pouvez utiliser un **POSITION** variable comme un itérateur pour parcourir une liste séquentielle et comme un signet à un espace réservé. Une position n’est pas identique à un index, toutefois.  
  
 Insertion d’éléments est très rapide à la tête de liste, à la fin et à un autre **POSITION**. Une recherche séquentielle est nécessaire pour rechercher un élément par valeur ou index. Cette recherche peut être lente si la liste est longue.  
  
 `CObList` incorpore la macro `IMPLEMENT_SERIAL` pour prendre en charge la sérialisation et le vidage de ses éléments. Si une liste de `CObject` des pointeurs est stocké dans une archive, avec un opérateur d’insertion surchargés ou les `Serialize` fonction membre, chaque `CObject` élément est sérialisé à son tour.  
  
 Si vous avez besoin d’une image de chaque `CObject` éléments dans la liste, vous devez définir la profondeur du contexte de vidage à 1 ou supérieur.  
  
 Lorsqu’un `CObList` objet est supprimé, ou lorsque ses éléments sont supprimés, uniquement le `CObject` pointeurs sont supprimées, pas les objets qu’ils référencent.  
  
 Vous pouvez dériver vos propres classes de `CObList`. Votre nouvelle classe de liste, conçu pour contenir des pointeurs vers des objets dérivés de `CObject`, ajoute de nouveaux membres de données et les nouvelles fonctions membres. Notez que la liste résultante n’est pas strictement type sécurisé, car il autorise l’insertion de n’importe quel `CObject` pointeur.  
  
> [!NOTE]
>  Vous devez utiliser le [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro dans l’implémentation de votre classe dérivée si vous prévoyez de sérialiser la liste.  
  
 Pour plus d’informations sur l’utilisation de `CObList`, consultez l’article [Collections](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CObList`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxcoll.h  
  
##  <a name="addhead"></a>CObList::AddHead  
 Ajoute un nouvel élément ou une liste d’éléments à la tête de la liste.  
  
```  
POSITION AddHead(CObject* newElement);  
void AddHead(CObList* pNewList);
```  
  
### <a name="parameters"></a>Paramètres  
 `newElement`  
 Le `CObject` pointeur à ajouter à cette liste.  
  
 `pNewList`  
 Un pointeur vers un autre `CObList` liste. Les éléments de `pNewList` sera ajouté à cette liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la première version du **POSITION** valeur de l’élément nouvellement inséré.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::AddHead`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION AddHead (void\* ** `newElement` **) ;**<br /><br /> **void AddHead (CPtrList\* ** `pNewList` **) ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION AddHead (const CString se** `newElement` **) ;**<br /><br /> **POSITION AddHead (LPCTSTR** `newElement` **) ;**<br /><br /> **void AddHead (CStringList\* ** `pNewList` **) ;**|  
  
### <a name="remarks"></a>Remarques  
 La liste peut être vide avant l’opération.  
  
### <a name="example"></a>Exemple  
  Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#89;](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]  
  
 Les résultats de ce programme sont les suivantes :  
  
 `AddHead example: A CObList with 2 elements`  
  
 `a CAge at $44A8 40`  
  
 `a CAge at $442A 21`  
  
##  <a name="addtail"></a>CObList::AddTail  
 Ajoute un nouvel élément ou une liste d’éléments à la fin de cette liste.  
  
```  
POSITION AddTail(CObject* newElement);  
void AddTail(CObList* pNewList);
```  
  
### <a name="parameters"></a>Paramètres  
 `newElement`  
 Le `CObject` pointeur à ajouter à cette liste.  
  
 `pNewList`  
 Un pointeur vers un autre `CObList` liste. Les éléments de `pNewList` sera ajouté à cette liste.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la première version du **POSITION** valeur de l’élément nouvellement inséré.  
  
### <a name="remarks"></a>Notes  
 La liste peut être vide avant l’opération.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::AddTail`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION AddTail (void\* ** `newElement` **) ;**<br /><br /> **void AddTail (CPtrList\* ** `pNewList` **) ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION AddTail (const CString se** `newElement` **) ;**<br /><br /> **POSITION AddTail (LPCTSTR** `newElement` **) ;**<br /><br /> **void AddTail (CStringList\* ** `pNewList` **) ;**|  
  
### <a name="example"></a>Exemple  
  Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#90;](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]  
  
 Les résultats de ce programme sont les suivantes :  
  
 `AddTail example: A CObList with 2 elements`  
  
 `a CAge at $444A 21`  
  
 `a CAge at $4526 40`  
  
##  <a name="coblist"></a>CObList::CObList  
 Construit un vide `CObject` liste de pointeurs.  
  
```  
CObList(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Paramètres  
 `nBlockSize`  
 La granularité d’allocation de mémoire pour l’extension de la liste.  
  
### <a name="remarks"></a>Remarques  
 À mesure que la liste augmente, la mémoire est allouée en unités de `nBlockSize` entrées. Si une allocation de mémoire échoue, un `CMemoryException` est levée.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::CObList`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList (INT_PTR** `nBlockSize` **= 10) ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList (INT_PTR** `nBlockSize` **= 10) ;**|  
  
### <a name="example"></a>Exemple  
  Voici un exemple de la `CObject`-classe dérivée `CAge` utilisés dans les exemples de regroupement :  
  
 [!code-cpp[NVC_MFCCollections&#91;](../../mfc/codesnippet/cpp/coblist-class_3.h)]  
  
 Voici un exemple de `CObList` l’utilisation du constructeur :  
  
 [!code-cpp[NVC_MFCCollections&#92;](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]  
  
##  <a name="find"></a>CObList::Find  
 Recherche dans la liste de manière séquentielle pour rechercher la première `CObject` pointeur correspondant spécifié `CObject` pointeur.  
  
```  
POSITION Find(
    CObject* searchValue,  
    POSITION startAfter = NULL) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `searchValue`  
 Le pointeur d’objet à rechercher dans cette liste.  
  
 `startAfter`  
 La position de départ pour la recherche.  
  
### <a name="return-value"></a>Valeur de retour  
 A **POSITION** valeur qui peut être utilisé pour l’itération ou l’extraction de pointeur d’objet ; **NULL** si l’objet est introuvable.  
  
### <a name="remarks"></a>Remarques  
 Notez que les valeurs de pointeur sont comparées, pas le contenu des objets.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::Find`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Recherche POSITION (void\* ** `searchValue` **, POSITION** `startAfter` **= NULL) const ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Recherche POSITION (LPCTSTR** `searchValue` **, POSITION** `startAfter` **= NULL) const ;**|  
  
### <a name="example"></a>Exemple  
 Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#93;](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]  
  
##  <a name="findindex"></a>CObList::FindIndex  
 Utilise la valeur de `nIndex` en tant qu’index dans la liste.  
  
```  
POSITION FindIndex(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index de base zéro de l’élément de liste à rechercher.  
  
### <a name="return-value"></a>Valeur de retour  
 A **POSITION** valeur qui peut être utilisé pour l’itération ou l’extraction de pointeur d’objet ; **NULL** si `nIndex` est trop grande. (L’infrastructure génère une assertion si `nIndex` est négatif.)  
  
### <a name="remarks"></a>Remarques  
 Démarrer une analyse séquentielle de la tête de la liste, l’arrêt de la *n*élément th.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::FindIndex`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION FindIndex (INT_PTR** `nIndex` **) const ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION FindIndex (INT_PTR** `nIndex` **) const ;**|  
  
### <a name="example"></a>Exemple  
 Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#94;](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]  
  
##  <a name="getat"></a>CObList::GetAt  
 Une variable de type **POSITION** est une clé pour la liste.  
  
```  
CObject*& GetAt(POSITION position);  
const CObject*& GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *position*  
 A **POSITION** valeur retournée par une précédente `GetHeadPosition` ou **trouver** appel de fonction membre.  
  
### <a name="return-value"></a>Valeur de retour  
 Consultez la description de la valeur de retour de [GetHead](#gethead).  
  
### <a name="remarks"></a>Remarques  
 Il n’est pas identique à un index, et vous ne pouvez pas utiliser un **POSITION** valeur vous-même. `GetAt`Récupère le `CObject` pointeur associé à une position donnée.  
  
 Vous devez vous assurer que votre **POSITION** valeur représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::GetAt`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void const\*se GetAt (POSITION** *position* **) const ;**<br /><br /> **void\*se GetAt (POSITION** *position* **) ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const GetAt se de CString (POSITION** *position* **) const ;**<br /><br /> **CString se GetAt (POSITION** *position* **) ;**|  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [FindIndex](#findindex).  
  
##  <a name="getcount"></a>CObList::GetCount  
 Obtient le nombre d’éléments dans cette liste.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur entière qui contient le nombre d’éléments.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::GetCount`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR const ; (GetCount)**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR const ; (GetCount)**|  
  
### <a name="example"></a>Exemple  
 Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#95;](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]  
  
##  <a name="gethead"></a>CObList::GetHead  
 Obtient le `CObject` pointeur qui représente l’élément head de cette liste.  
  
```  
CObject*& GetHead();  
const CObject*& GetHead() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si la liste est accessible via un pointeur vers un **CObList const**, puis `GetHead` renvoie un `CObject` pointeur. Cela permet à la fonction doit être utilisé uniquement sur le côté droit d’une instruction d’assignation et qui protège la liste de toute modification.  
  
 Si la liste est accessible directement ou via un pointeur vers un `CObList`, puis `GetHead` renvoie une référence à un `CObject` pointeur. Cela permet la fonction à utiliser sur chaque côté d’une instruction d’assignation et donc les entrées de liste à modifier.  
  
### <a name="remarks"></a>Notes  
 Vous devez vous assurer que la liste n’est pas vide avant d’appeler `GetHead`. Si la liste est vide, la version Debug de la bibliothèque Microsoft Foundation Class déclare. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::GetHead`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void const\*se () GetHead const ; void\*se () GetHead ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const (CString se GetHead) const ; () CString se GetHead ;**|  
  
### <a name="example"></a>Exemple  
 Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 L’exemple suivant illustre l’utilisation de `GetHead` sur le côté gauche d’une instruction d’assignation.  
  
 [!code-cpp[NVC_MFCCollections&#96;](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]  
  
##  <a name="getheadposition"></a>CObList::GetHeadPosition  
 Obtient la position de l’élément head de cette liste.  
  
```  
POSITION GetHeadPosition() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A **POSITION** valeur qui peut être utilisé pour l’itération ou l’extraction de pointeur d’objet ; **NULL** si la liste est vide.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::GetHeadPosition`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION const ; (GetHeadPosition)**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION const ; (GetHeadPosition)**|  
  
### <a name="example"></a>Exemple  
 Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#97;](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]  
  
##  <a name="getnext"></a>CObList::GetNext  
 Obtient l’élément de liste identifié par `rPosition`, puis définit `rPosition` à le `POSITION` la valeur de l’entrée suivante dans la liste.  
  
```  
CObject*& GetNext(POSITION& rPosition);  
const CObject* GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `rPosition`  
 Une référence à un `POSITION` valeur retournée par une précédente `GetNext`, `GetHeadPosition`, ou un autre appel de fonction membre.  
  
### <a name="return-value"></a>Valeur de retour  
 Consultez la description de la valeur de retour de [GetHead](#gethead).  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser `GetNext` dans une boucle d’itération en avant si vous établissez la position initiale avec un appel à `GetHeadPosition` ou `Find`.  
  
 Vous devez vous assurer que votre `POSITION` valeur représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.  
  
 Si l’élément récupéré est le dernier dans la liste, puis la nouvelle valeur de `rPosition` est défini sur `NULL`.  
  
 Il est possible de supprimer un élément lors d’une itération. Consultez l’exemple de [RemoveAt](#removeat).  
  
> [!NOTE]
>  Depuis MFC 8.0, la version de cette méthode const a changé pour retourner `const CObject*` au lieu de `const CObject*&`.  Cette modification a été effectuée pour mettre le compilateur en conformité avec la norme C++.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::GetNext`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|  
  
### <a name="example"></a>Exemple  
  Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#98;](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]  
  
 Les résultats de ce programme sont les suivantes :  
  
 `a CAge at $479C 40`  
  
 `a CAge at $46C0 21`  
  
##  <a name="getprev"></a>CObList::GetPrev  
 Obtient l’élément de liste identifié par `rPosition`, puis définit `rPosition` à le `POSITION` la valeur de l’entrée précédente dans la liste.  
  
```  
CObject*& GetPrev(POSITION& rPosition);  
const CObject* GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `rPosition`  
 Une référence à un `POSITION` valeur retourné par une `GetPrev` ou un autre appel de fonction membre.  
  
### <a name="return-value"></a>Valeur de retour  
 Consultez la description de la valeur de retour de [GetHead](#gethead).  
  
### <a name="remarks"></a>Remarques  
 Vous pouvez utiliser `GetPrev` dans une boucle d’itération inverse si vous établissez la position initiale avec un appel à `GetTailPosition` ou `Find`.  
  
 Vous devez vous assurer que votre `POSITION` valeur représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.  
  
 Si l’élément récupéré est le premier dans la liste, puis la nouvelle valeur de `rPosition` est défini sur `NULL`.  
  
> [!NOTE]
>  Depuis MFC 8.0, la version de cette méthode const a changé pour retourner `const CObject*` au lieu de `const CObject*&`.  Cette modification a été effectuée pour mettre le compilateur en conformité avec la norme C++.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::GetPrev`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|  
  
### <a name="example"></a>Exemple  
  Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#99;](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]  
  
 Les résultats de ce programme sont les suivantes :  
  
 `a CAge at $421C 21`  
  
 `a CAge at $421C 40`  
  
##  <a name="getsize"></a>CObList::GetSize  
 Retourne le nombre d’éléments de liste.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Nombre d'éléments de la liste.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour récupérer le nombre d’éléments dans la liste.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::GetSize`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize () const ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize () const ;**|  
  
### <a name="example"></a>Exemple  
 Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[100 NVC_MFCCollections](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]  
  
##  <a name="gettail"></a>CObList::GetTail  
 Obtient le `CObject` pointeur qui représente l’élément de fin de cette liste.  
  
```  
CObject*& GetTail();  
const CObject*& GetTail() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Consultez la description de la valeur de retour de [GetHead](#gethead).  
  
### <a name="remarks"></a>Notes  
 Vous devez vous assurer que la liste n’est pas vide avant d’appeler `GetTail`. Si la liste est vide, la version Debug de la bibliothèque Microsoft Foundation Class déclare. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::GetTail`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void const\*se () GetTail const ; void\*se () GetTail ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const (CString se GetTail) const ; () CString se GetTail ;**|  
  
### <a name="example"></a>Exemple  
 Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#101;](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]  
  
##  <a name="gettailposition"></a>CObList::GetTailPosition  
 Obtient la position de l’élément de fin de cette liste. **NULL** si la liste est vide.  
  
```  
POSITION GetTailPosition() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A **POSITION** valeur qui peut être utilisé pour l’itération ou l’extraction de pointeur d’objet ; **NULL** si la liste est vide.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::GetTailPosition`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION const ; (GetTailPosition)**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION const ; (GetTailPosition)**|  
  
### <a name="example"></a>Exemple  
 Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#102;](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]  
  
##  <a name="insertafter"></a>CObList::InsertAfter  
 Ajoute un élément à cette liste après l’élément à la position spécifiée.  
  
```  
POSITION InsertAfter(
    POSITION position,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Paramètres  
 *position*  
 Une valeur **POSITION** retournée par un appel précédent de `GetNext`, `GetPrev`ou de la fonction membre **Find** .  
  
 `newElement`  
 Le pointeur d’objet à ajouter à cette liste.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::InsertAfter`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**InsertAfter POSITION (POSITION** *position* **, void\* ** `newElement` **) ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**InsertAfter POSITION (POSITION** *position* **, const CString se** `newElement` **) ;**<br /><br /> **InsertAfter POSITION (POSITION** *position* **, LPCTSTR** `newElement` **) ;**|  
  
### <a name="return-value"></a>Valeur de retour  
 A **POSITION** valeur qui est le même que le *position* paramètre.  
  
### <a name="example"></a>Exemple  
  Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#103;](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]  
  
 Les résultats de ce programme sont les suivantes :  
  
 `InsertAfter example: A CObList with 3 elements`  
  
 `a CAge at $4A44 40`  
  
 `a CAge at $4A64 65`  
  
 `a CAge at $4968 21`  
  
##  <a name="insertbefore"></a>CObList::InsertBefore  
 Ajoute un élément à cette liste avant l’élément à la position spécifiée.  
  
```  
POSITION InsertBefore(
    POSITION position,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Paramètres  
 *position*  
 Une valeur **POSITION** retournée par un appel précédent de `GetNext`, `GetPrev`ou de la fonction membre **Find** .  
  
 `newElement`  
 Le pointeur d’objet à ajouter à cette liste.  
  
### <a name="return-value"></a>Valeur de retour  
 A **POSITION** valeur qui peut être utilisé pour l’itération ou l’extraction de pointeur d’objet ; **NULL** si la liste est vide.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::InsertBefore`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION InsertBefore (POSITION** *position* **, void\* ** `newElement` **) ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION InsertBefore (POSITION** *position* **, const CString se** `newElement` **) ;**<br /><br /> **POSITION InsertBefore (POSITION** *position* **, LPCTSTR** `newElement` **) ;**|  
  
### <a name="example"></a>Exemple  
  Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#104;](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]  
  
 Les résultats de ce programme sont les suivantes :  
  
 `InsertBefore example: A CObList with 3 elements`  
  
 `a CAge at $4AE2 40`  
  
 `a CAge at $4B02 65`  
  
 `a CAge at $49E6 21`  
  
##  <a name="isempty"></a>CObList::IsEmpty  
 Indique si cette liste ne contient aucun élément.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si cette liste est vide. sinon 0.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::IsEmpty`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty () const ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty () const ;**|  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [RemoveAll](#removeall).  
  
##  <a name="removeall"></a>CObList::RemoveAll  
 Supprime tous les éléments de cette liste et libère associé `CObList` mémoire.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Remarques  
 Aucune erreur n’est générée si la liste est déjà vide.  
  
 Lorsque vous supprimez des éléments d’un `CObList`, vous supprimez les pointeurs d’objet de la liste. Il vous incombe de supprimer les objets eux-mêmes.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::RemoveAll`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void () RemoveAll ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void () RemoveAll ;**|  
  
### <a name="example"></a>Exemple  
 Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#105;](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]  
  
##  <a name="removeat"></a>CObList::RemoveAt  
 Supprime l’élément spécifié dans cette liste.  
  
```  
void RemoveAt(POSITION position);
```  
  
### <a name="parameters"></a>Paramètres  
 *position*  
 La position de l’élément à supprimer de la liste.  
  
### <a name="remarks"></a>Notes  
 Lorsque vous supprimez un élément d’un `CObList`, vous supprimez le pointeur d’objet de la liste. Il vous incombe de supprimer les objets eux-mêmes.  
  
 Vous devez vous assurer que votre **POSITION** valeur représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::RemoveAt`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAt (POSITION** *position* **) ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAt (POSITION** *position* **) ;**|  
  
### <a name="example"></a>Exemple  
  Soyez prudent lors de la suppression d’un élément lors d’une itération de la liste. L’exemple suivant illustre une technique de suppression qui garantit une valide **POSITION** valeur [GetNext](#getnext).  
  
 Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#106;](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]  
  
 Les résultats de ce programme sont les suivantes :  
  
 `RemoveAt example: A CObList with 2 elements`  
  
 `a CAge at $4C1E 65`  
  
 `a CAge at $4B22 21`  
  
##  <a name="removehead"></a>CObList::RemoveHead  
 Supprime l’élément au début de la liste et retourne un pointeur vers elle.  
  
```  
CObject* RemoveHead();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le `CObject` pointeur précédemment au début de la liste.  
  
### <a name="remarks"></a>Remarques  
 Vous devez vous assurer que la liste n’est pas vide avant d’appeler `RemoveHead`. Si la liste est vide, la version Debug de la bibliothèque Microsoft Foundation Class déclare. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::RemoveHead`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* () RemoveHead ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**() CString RemoveHead ;**|  
  
### <a name="example"></a>Exemple  
 Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#107;](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]  
  
##  <a name="removetail"></a>CObList::RemoveTail  
 Supprime l’élément de la fin de la liste et retourne un pointeur vers elle.  
  
```  
CObject* RemoveTail();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’objet qui était à la fin de la liste.  
  
### <a name="remarks"></a>Remarques  
 Vous devez vous assurer que la liste n’est pas vide avant d’appeler `RemoveTail`. Si la liste est vide, la version Debug de la bibliothèque Microsoft Foundation Class déclare. Utilisez [IsEmpty](#isempty) pour vérifier que la liste contient des éléments.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::RemoveTail`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* () RemoveTail ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**() CString RemoveTail ;**|  
  
### <a name="example"></a>Exemple  
 Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#108;](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]  
  
##  <a name="setat"></a>CObList::SetAt  
 Définit l’élément à une position donnée.  
  
```  
void SetAt(
    POSITION pos,  
    CObject* newElement);
```  
  
### <a name="parameters"></a>Paramètres  
 `pos`  
 Le **POSITION** de l’élément à définir.  
  
 `newElement`  
 Le `CObject` pointeur à écrire dans la liste.  
  
### <a name="remarks"></a>Remarques  
 Une variable de type **POSITION** est une clé pour la liste. Il n’est pas identique à un index, et vous ne pouvez pas utiliser un **POSITION** valeur vous-même. `SetAt`écrit le `CObject` pointeur vers la position spécifiée dans la liste.  
  
 Vous devez vous assurer que votre **POSITION** valeur représente une position valide dans la liste. Si elle n’est pas valide, la version Debug de la bibliothèque Microsoft Foundation Class déclare.  
  
 Le tableau suivant présente les autres membres qui sont similaires aux fonctions `CObList::SetAt`.  
  
|Classe|Fonction membre|  
|-----------|---------------------|  
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt (POSITION** `pos` **, const CString se** `newElement` **) ;**|  
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt( POSITION** `pos` **, LPCTSTR** `newElement` **);**|  
  
### <a name="example"></a>Exemple  
  Consultez la page [CObList::CObList](#coblist) pour obtenir la liste de la `CAge` classe.  
  
 [!code-cpp[NVC_MFCCollections&#109;](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]  
  
 Les résultats de ce programme sont les suivantes :  
  
 `SetAt example: A CObList with 2 elements`  
  
 `a CAge at $4D98 40`  
  
 `a CAge at $4DB8 65`  
  
## <a name="see-also"></a>Voir aussi  
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique de la hiérarchie](../../mfc/hierarchy-chart.md)   
 [CStringList (classe)](../../mfc/reference/cstringlist-class.md)   
 [CPtrList (classe)](../../mfc/reference/cptrlist-class.md)

