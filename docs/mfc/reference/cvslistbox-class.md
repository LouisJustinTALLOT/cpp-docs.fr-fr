---
title: Classe de CVSListBox | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CVSListBox
- AFXVSLISTBOX/CVSListBox
- AFXVSLISTBOX/CVSListBox::CVSListBox
- AFXVSLISTBOX/CVSListBox::AddItem
- AFXVSLISTBOX/CVSListBox::EditItem
- AFXVSLISTBOX/CVSListBox::GetCount
- AFXVSLISTBOX/CVSListBox::GetItemData
- AFXVSLISTBOX/CVSListBox::GetItemText
- AFXVSLISTBOX/CVSListBox::GetSelItem
- AFXVSLISTBOX/CVSListBox::RemoveItem
- AFXVSLISTBOX/CVSListBox::SelectItem
- AFXVSLISTBOX/CVSListBox::SetItemData
- AFXVSLISTBOX/CVSListBox::GetListHwnd
dev_langs:
- C++
helpviewer_keywords:
- CVSListBox [MFC], CVSListBox
- CVSListBox [MFC], AddItem
- CVSListBox [MFC], EditItem
- CVSListBox [MFC], GetCount
- CVSListBox [MFC], GetItemData
- CVSListBox [MFC], GetItemText
- CVSListBox [MFC], GetSelItem
- CVSListBox [MFC], RemoveItem
- CVSListBox [MFC], SelectItem
- CVSListBox [MFC], SetItemData
- CVSListBox [MFC], GetListHwnd
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 582ddd1340dd94f367d5401d517e9335d370b634
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122635"
---
# <a name="cvslistbox-class"></a>Classe de CVSListBox
La `CVSListBox` classe prend en charge un contrôle de liste modifiable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CVSListBox : public CVSListBoxBase  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CVSListBox::CVSListBox](#cvslistbox)|Construit un objet `CVSListBox`.|  
|`CVSListBox::~CVSListBox`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CVSListBox::AddItem](#additem)|Ajoute une chaîne à un contrôle de liste. (Substitue `CVSListBoxBase::AddItem`.)|  
|[CVSListBox::EditItem](#edititem)|Démarre une opération de modification sur le texte d’un élément de contrôle de liste. (Substitue `CVSListBoxBase::EditItem`.)|  
|[CVSListBox::GetCount](#getcount)|Récupère le nombre de chaînes dans un contrôle de liste modifiable. (Substitue `CVSListBoxBase::GetCount`.)|  
|[CVSListBox::GetItemData](#getitemdata)|Récupère une valeur spécifique à l’application 32 bits qui est associée à un élément de contrôle de liste modifiable. (Substitue `CVSListBoxBase::GetItemData`.)|  
|[CVSListBox::GetItemText](#getitemtext)|Récupère le texte d’un élément de contrôle de liste modifiable. (Substitue `CVSListBoxBase::GetItemText`.)|  
|[CVSListBox::GetSelItem](#getselitem)|Récupère l’index de base zéro de l’élément actuellement sélectionné dans un contrôle de liste modifiable. (Substitue `CVSListBoxBase::GetSelItem`.)|  
|`CVSListBox::PreTranslateMessage`|Convertit les messages de fenêtre avant d’être distribués à le [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) et [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) fonctions Windows. Pour plus d’informations et la syntaxe de méthode, consultez [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Substitue `CVSListBoxBase::PreTranslateMessage`.)|  
|[CVSListBox::RemoveItem](#removeitem)|Supprime un élément à partir d’un contrôle de liste modifiable. (Substitue `CVSListBoxBase::RemoveItem`.)|  
|[CVSListBox::SelectItem](#selectitem)|Sélectionne une chaîne de contrôle de liste modifiable. (Substitue `CVSListBoxBase::SelectItem`.)|  
|[CVSListBox::SetItemData](#setitemdata)|Associe une valeur de 32 bits spécifique à l’application à un élément de contrôle de liste modifiable. (Substitue `CVSListBoxBase::SetItemData`.)|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CVSListBox::GetListHwnd](#getlisthwnd)|Retourne le handle vers le contrôle d’affichage liste incorporée actuel.|  
  
## <a name="remarks"></a>Notes  
 La `CVSListBox` classe fournit un ensemble de boutons Modifier qui permettent aux utilisateurs de créer, modifier, supprimer ou réorganiser les éléments d’un contrôle de liste.  
  
 Voici une image du contrôle de liste modifiable. La deuxième entrée de liste, qui est intitulée « Item2 », est sélectionnée pour la modification.  
  
 ![Contrôle CVSListBox](../../mfc/reference/media/cvslistbox.png "cvslistbox")  
  
 Si vous utilisez l’éditeur de ressources pour ajouter un contrôle de liste modifiable, notez que le **boîte à outils** volet de l’éditeur ne fournit pas d’un contrôle de liste modifiable prédéfinie. Au lieu de cela, ajoutez un contrôle statique tel que le **zone de groupe** contrôle. L’infrastructure utilise le contrôle statique comme espace réservé pour spécifier la taille et la position du contrôle de liste modifiable.  
  
 Pour utiliser un contrôle de liste modifiable dans un modèle de boîte de dialogue, vous devez déclarer une `CVSListBox` variable dans votre classe de boîte de dialogue. Pour prendre en charge d’échange de données entre la variable et le contrôle, définissez un `DDX_Control` entrée de macro dans le `DoDataExchange` (méthode) de la boîte de dialogue. Par défaut, le contrôle de liste modifiable est créé sans les boutons Modifier. Utilisez la méthode CVSListBoxBase::SetStandardButtons héritée pour activer les boutons Modifier.  
  
 Pour plus d’informations, consultez le répertoire d’exemples, le `New Controls` exemple, les fichiers Page3.cpp et Page3.h.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CStatic](../../mfc/reference/cstatic-class.md)  
  
 `CVSListBoxBase`  
  
 [CVSListBox](../../mfc/reference/cvslistbox-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxvslistbox.h  
  
##  <a name="additem"></a>  CVSListBox::AddItem  
 Ajoute une chaîne à un contrôle de liste.  
  
```  
virtual int AddItem(
    const CString& strIext,  
    DWORD_PTR dwData=0,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *strIext*  
 Une référence à une chaîne.  
  
 [in] *dwData*  
 Une valeur spécifique à l’application 32 bits qui est associée à la chaîne. La valeur par défaut est 0.  
  
 [in] *iIndex*  
 Index de base zéro de la position qui conserve la chaîne. Si le *iIndex* paramètre est -1, la chaîne est ajoutée à la fin de la liste. La valeur par défaut est -1.  
  
### <a name="return-value"></a>Valeur de retour  
 Index de base zéro de la position de la chaîne dans le contrôle de liste.  
  
### <a name="remarks"></a>Notes  
 Utilisez le [CVSListBox::GetItemData](#getitemdata) méthode pour récupérer la valeur spécifiée par la *dwData* paramètre. Cette valeur peut être un entier spécifiques à l’application ou un pointeur vers d’autres données.  
  
##  <a name="cvslistbox"></a>  CVSListBox::CVSListBox  
 Construit un objet `CVSListBox`.  
  
```  
CVSListBox();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="edititem"></a>  CVSListBox::EditItem  
 Démarre une opération de modification sur le texte d’un élément de contrôle de liste.  
  
```  
virtual BOOL EditItem(int iIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *iIndex*  
 Index de base zéro d’un élément de contrôle de liste.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si l’opération de modification démarre avec succès ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 L’utilisateur commence une opération de modification en double-cliquant sur l’étiquette d’un élément, ou en appuyant sur la **F2** ou **espace** clé lorsqu’un élément a le focus.  
  
##  <a name="getcount"></a>  CVSListBox::GetCount  
 Récupère le nombre de chaînes dans un contrôle de liste modifiable.  
  
```  
virtual int GetCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Nombre d'éléments figurant dans le contrôle de liste.  
  
### <a name="remarks"></a>Notes  
 Notez que le nombre est supérieur à la valeur d’index du dernier élément, car l’index est de base zéro.  
  
##  <a name="getitemdata"></a>  CVSListBox::GetItemData  
 Récupère une valeur spécifique à l’application 32 bits qui est associée à un élément de contrôle de liste modifiable.  
  
```  
virtual DWORD_PTR GetItemData(int iIndex) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *iIndex*  
 Index de base zéro d’un élément de contrôle de liste modifiable.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur de 32 bits qui est associée à l’élément spécifié.  
  
### <a name="remarks"></a>Notes  
 Utilisez le [CVSListBox::SetItemData](#setitemdata) ou [CVSListBox::AddItem](#additem) méthode permet d’associer la valeur 32 bits avec l’élément de contrôle de liste. Cette valeur peut être un entier spécifiques à l’application ou un pointeur vers d’autres données.  
  
##  <a name="getitemtext"></a>  CVSListBox::GetItemText  
 Récupère le texte d’un élément de contrôle de liste modifiable.  
  
```  
virtual CString GetItemText(int iIndex) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `iIndex`  
 Index de base zéro d’un élément de contrôle de liste modifiable.  
  
### <a name="return-value"></a>Valeur de retour  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objet qui contient le texte de l’élément spécifié.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getlisthwnd"></a>  CVSListBox::GetListHwnd  
 Retourne le handle vers le contrôle d’affichage liste incorporée actuel.  
  
```  
virtual HWND GetListHwnd() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Handle vers le contrôle de la vue liste incorporée.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour récupérer un handle du contrôle d’affichage liste incorporée qui prend en charge la `CVSListBox` classe.  
  
##  <a name="getselitem"></a>  CVSListBox::GetSelItem  
 Récupère l’index de base zéro de l’élément actuellement sélectionné dans un contrôle de liste modifiable.  
  
```  
virtual int GetSelItem() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si cette méthode réussit, l’index de base zéro de l’élément actuellement sélectionné ; Sinon, -1.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="removeitem"></a>  CVSListBox::RemoveItem  
 Supprime un élément à partir d’un contrôle de liste modifiable.  
  
```  
virtual BOOL RemoveItem(int iIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *iIndex*  
 Index de base zéro d’un élément de contrôle de liste modifiable.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si l’élément spécifié est supprimé ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="selectitem"></a>  CVSListBox::SelectItem  
 Sélectionne une chaîne de contrôle de liste modifiable.  
  
```  
virtual BOOL SelectItem(int iItem);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *iItem*  
 Index de base zéro d’un élément de contrôle de liste modifiable.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si cette méthode a réussi ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Cette méthode sélectionne l’élément spécifié et si nécessaire, fait défiler l’élément dans la vue.  
  
##  <a name="setitemdata"></a>  CVSListBox::SetItemData  
 Associe une valeur de 32 bits spécifique à l’application à un élément de contrôle de liste modifiable.  
  
```  
virtual void SetItemData(
    int iIndex,  
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *iIndex*  
 Index de base zéro d’un élément de contrôle de liste modifiable.  
  
 [in] *dwData*  
 Une valeur 32 bits. Cette valeur peut être un entier spécifiques à l’application ou un pointeur vers d’autres données.  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)
