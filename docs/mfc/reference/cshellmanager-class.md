---
title: Classe de CShellManager | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CShellManager
- AFXSHELLMANAGER/CShellManager
- AFXSHELLMANAGER/CShellManager::CShellManager
- AFXSHELLMANAGER/CShellManager::BrowseForFolder
- AFXSHELLMANAGER/CShellManager::ConcatenateItem
- AFXSHELLMANAGER/CShellManager::CopyItem
- AFXSHELLMANAGER/CShellManager::CreateItem
- AFXSHELLMANAGER/CShellManager::FreeItem
- AFXSHELLMANAGER/CShellManager::GetItemCount
- AFXSHELLMANAGER/CShellManager::GetItemSize
- AFXSHELLMANAGER/CShellManager::GetNextItem
- AFXSHELLMANAGER/CShellManager::GetParentItem
- AFXSHELLMANAGER/CShellManager::ItemFromPath
dev_langs:
- C++
helpviewer_keywords:
- CShellManager [MFC], CShellManager
- CShellManager [MFC], BrowseForFolder
- CShellManager [MFC], ConcatenateItem
- CShellManager [MFC], CopyItem
- CShellManager [MFC], CreateItem
- CShellManager [MFC], FreeItem
- CShellManager [MFC], GetItemCount
- CShellManager [MFC], GetItemSize
- CShellManager [MFC], GetNextItem
- CShellManager [MFC], GetParentItem
- CShellManager [MFC], ItemFromPath
ms.assetid: f15c4c1a-6fae-487d-9913-9b7369b33da0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1052c7197d8679272cc917402a8936983649acb
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079236"
---
# <a name="cshellmanager-class"></a>Classe de CShellManager
Implémente plusieurs méthodes qui permettent d'utiliser des pointeurs vers des listes d'identificateurs (PIDL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CShellManager : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CShellManager::CShellManager](#cshellmanager)|Construit un objet `CShellManager`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CShellManager::BrowseForFolder](#browseforfolder)|Affiche une boîte de dialogue qui permet à l’utilisateur de sélectionner un dossier d’environnement.|  
|[CShellManager::ConcatenateItem](#concatenateitem)|Concatène deux identificateurs PIDL.|  
|[CShellManager::CopyItem](#copyitem)|Crée un nouveau PIDL et copie le PIDL fourni à ce dernier.|  
|[CShellManager::CreateItem](#createitem)|Crée un nouveau PIDL de la taille spécifiée.|  
|[CShellManager::FreeItem](#freeitem)|Supprime le PIDL fourni.|  
|[CShellManager::GetItemCount](#getitemcount)|Retourne le nombre d’éléments dans le PIDL fourni.|  
|[CShellManager::GetItemSize](#getitemsize)|Retourne la taille de la PIDL fourni.|  
|[CShellManager::GetNextItem](#getnextitem)|Retourne l’élément suivant à partir de la PIDL.|  
|[CShellManager::GetParentItem](#getparentitem)|Récupère l’élément parent de l’élément fourni.|  
|[CShellManager::ItemFromPath](#itemfrompath)|Récupère le PIDL pour l’élément identifié par le chemin d’accès fourni.|  
  
## <a name="remarks"></a>Notes  
 Les méthodes de la `CShellManager` classe gèrent tous les identificateurs PIDL. Un PIDL est un identificateur unique pour un objet de l’interpréteur de commandes.  
  
 Vous ne devez pas créer un `CShellManager` objet manuellement. Il sera créé automatiquement par l’infrastructure de votre application. Toutefois, vous devez appeler [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) pendant le processus d’initialisation de votre application. Pour obtenir un pointeur vers le Gestionnaire de shell pour votre application, appelez [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CShellManager](../../mfc/reference/cshellmanager-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxshellmanager.h  
  
##  <a name="browseforfolder"></a>  CShellManager::BrowseForFolder  
 Affiche une boîte de dialogue qui permet à l’utilisateur de sélectionner un dossier d’environnement.  
  
```  
BOOL BrowseForFolder(
    CString& strOutFolder,  
    CWnd* pWndParent = NULL,  
    LPCTSTR lplszInitialFolder = NULL,  
    LPCTSTR lpszTitle = NULL,  
    UINT ulFlags = BIF_RETURNONLYFSDIRS,  
    LPINT piFolderImage = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [out] *strOutFolder*  
 La chaîne utilisée par la méthode pour stocker le chemin d’accès du dossier sélectionné.  
  
 [in] *pWndParent*  
 Pointeur vers la fenêtre parente.  
  
 [in] *lplszInitialFolder*  
 Chaîne qui contenait le dossier qui est sélectionné par défaut lorsque la boîte de dialogue s’affiche.  
  
 [in] *lpszTitle*  
 Le titre de la boîte de dialogue.  
  
 [in] *ulFlags*  
 Indicateurs qui spécifient des options de la boîte de dialogue. Consultez [Parcourir données](http://msdn.microsoft.com/library/windows/desktop/bb773205) une description détaillée.  
  
 [out] *piFolderImage*  
 Pointeur vers la valeur d’entier dans lequel la méthode écrit à l’index d’image du dossier sélectionné.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’utilisateur sélectionne un dossier à partir de la boîte de dialogue Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Lorsque vous appelez cette méthode, l’application crée et affiche une boîte de dialogue qui permet à l’utilisateur à sélectionner un dossier. La méthode écrit le chemin d’accès du dossier dans le *strOutFolder* paramètre.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment récupérer une référence à un `CShellManager` objet à l’aide de la `CWinAppEx::GetShellManager` (méthode) et comment utiliser le `BrowseForFolder` (méthode). Cet extrait de code fait partie de la [exemple d’Explorateur](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]  
  
##  <a name="concatenateitem"></a>  CShellManager::ConcatenateItem  
 Crée une liste contenant deux identificateurs PIDL.  
  
```  
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,  
    LPCITEMIDLIST pidl2);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pidl1*  
 Le premier élément.  
  
 [in] *pidl2*  
 Le deuxième élément.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la nouvelle liste d’éléments si la fonction réussit, sinon `NULL`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode crée un nouveau [ITEMIDLIST](http://msdn.microsoft.com/library/windows/desktop/bb773321) suffisamment grande pour contenir les deux *pidl1* et *pidl2*. Il copie ensuite *pidl1* et *pidl2* à la nouvelle liste.  
  
##  <a name="copyitem"></a>  CShellManager::CopyItem  
 Copie d’une liste d’éléments.  
  
```  
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pidlSource*  
 La liste d’éléments d’origine.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la liste de l’élément qui vient d’être créé en cas de réussite ; dans le cas contraire `NULL`.  
  
### <a name="remarks"></a>Notes  
 La liste de l’élément qui vient d’être créé a la même taille que la liste d’éléments de source.  
  
##  <a name="createitem"></a>  CShellManager::CreateItem  
 Crée un nouveau PIDL.  
  
```  
LPITEMIDLIST CreateItem(UINT cbSize);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *cbSize*  
 La taille de la liste d’éléments.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la liste de l’élément créé en cas de réussite ; dans le cas contraire `NULL`.  
  
##  <a name="cshellmanager"></a>  CShellManager::CShellManager  
 Construit un objet `CShellManager`.  
  
```  
CShellManager();
```  
  
### <a name="remarks"></a>Notes  
 Dans la plupart des cas, vous n’avez pas à créer un `CShellManager` directement. Par défaut, l’infrastructure crée une pour vous. Pour obtenir un pointeur vers le `CShellManager`, appelez [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager). Si vous ne créez pas un `CShellManager` manuellement, vous devez l’initialiser avec la méthode [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager).  
  
##  <a name="freeitem"></a>  CShellManager::FreeItem  
 Supprime une liste d’éléments.  
  
```  
void FreeItem(LPITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pidl*  
 Une liste d’éléments à supprimer.  
  
##  <a name="getitemcount"></a>  CShellManager::GetItemCount  
 Retourne le nombre d’éléments dans une liste d’éléments.  
  
```  
UINT GetItemCount(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pidl*  
 Pointeur vers une liste d’éléments.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans la liste d’éléments.  
  
##  <a name="getitemsize"></a>  CShellManager::GetItemSize  
 Retourne la taille d’une liste d’éléments.  
  
```  
UINT GetItemSize(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pidl*  
 Pointeur vers une liste d’éléments.  
  
### <a name="return-value"></a>Valeur de retour  
 La taille de la liste d’éléments.  
  
##  <a name="getnextitem"></a>  CShellManager::GetNextItem  
 Récupère l’élément suivant à partir d’un pointeur vers une liste d’identificateur élément (PIDL).  
  
```  
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pidl*  
 La liste des éléments à itérer.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’élément suivant dans la liste.  
  
### <a name="remarks"></a>Notes  
 Si il n’y a aucun élément dans la liste, cette méthode retourne `NULL`.  
  
##  <a name="getparentitem"></a>  CShellManager::GetParentItem  
 Récupère le parent d’un pointeur vers une liste d’identificateur élément (PIDL).  
  
```  
int GetParentItem(
    LPCITEMIDLIST lpidl,  
    LPITEMIDLIST& lpidlParent);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpidl*  
 Un PIDL dont le parent est récupéré.  
  
 [out] *lpidlParent*  
 Une référence à un PIDL où la méthode stocke le résultat.  
  
### <a name="return-value"></a>Valeur de retour  
 Le niveau du parent PIDL.  
  
### <a name="remarks"></a>Notes  
 Le niveau d’un PIDL est relatif au bureau. Le bureau PIDL est considérée comme ayant un niveau de 0.  
  
##  <a name="itemfrompath"></a>  CShellManager::ItemFromPath  
 Récupère le pointeur vers une liste d’identificateur élément (PIDL) à partir de l’élément identifié par un chemin d’accès de la chaîne.  
  
```  
HRESULT ItemFromPath(
    LPCTSTR lpszPath,  
    LPITEMIDLIST& pidl);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpszPath*  
 Chaîne qui spécifie le chemin d’accès de l’élément.  
  
 [out] *pidl*  
 Une référence à un PIDL. La méthode utilise cette PIDL pour stocker le pointeur à sa valeur de retour.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `NOERROR` en cas de réussite ; une valeur d’erreur défini par OLE.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)
