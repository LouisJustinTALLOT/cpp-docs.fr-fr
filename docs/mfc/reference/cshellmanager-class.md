---
title: Cshellmanager, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: ec2abf243e7f3865609f81fa4f3bf81e1b4c3d92
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58769972"
---
# <a name="cshellmanager-class"></a>Cshellmanager, classe

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
|[CShellManager::BrowseForFolder](#browseforfolder)|Affiche une boîte de dialogue qui permet à l’utilisateur sélectionner un dossier de l’interpréteur de commandes.|
|[CShellManager::ConcatenateItem](#concatenateitem)|Concatène deux PIDLs.|
|[CShellManager::CopyItem](#copyitem)|Crée un nouveau PIDL et copie le PIDL fourni vers celui-ci.|
|[CShellManager::CreateItem](#createitem)|Crée un nouveau PIDL de la taille spécifiée.|
|[CShellManager::FreeItem](#freeitem)|Supprime le PIDL fourni.|
|[CShellManager::GetItemCount](#getitemcount)|Retourne le nombre d’éléments dans le PIDL fourni.|
|[CShellManager::GetItemSize](#getitemsize)|Retourne la taille de la PIDL fourni.|
|[CShellManager::GetNextItem](#getnextitem)|Retourne l’élément suivant à partir de la PIDL.|
|[CShellManager::GetParentItem](#getparentitem)|Récupère l’élément parent de l’élément fourni.|
|[CShellManager::ItemFromPath](#itemfrompath)|Récupère le PIDL pour l’élément identifié par le chemin d’accès fourni.|

## <a name="remarks"></a>Notes

Les méthodes de la `CShellManager` classe tous les gère-t-elle les PIDLs. Un PIDL est un identificateur unique pour un objet de l’interpréteur de commandes.

Vous ne devez pas créer un `CShellManager` objet manuellement. Il sera créé automatiquement par l’infrastructure de votre application. Toutefois, vous devez appeler [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) pendant le processus d’initialisation de votre application. Pour obtenir un pointeur vers le Gestionnaire de shell pour votre application, appelez [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CShellManager](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête :** afxshellmanager.h

##  <a name="browseforfolder"></a>  CShellManager::BrowseForFolder

Affiche une boîte de dialogue qui permet à l’utilisateur sélectionner un dossier de l’interpréteur de commandes.

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

*strOutFolder*<br/>
[out] La chaîne utilisée par la méthode pour stocker le chemin d’accès du dossier sélectionné.

*pWndParent*<br/>
[in] Pointeur vers la fenêtre parente.

*lplszInitialFolder*<br/>
[in] Chaîne qui contient le dossier qui est sélectionné par défaut lorsque la boîte de dialogue s’affiche.

*lpszTitle*<br/>
[in] Titre de la boîte de dialogue.

*ulFlags*<br/>
[in] Indicateurs spécifiant des options pour la boîte de dialogue. Consultez [Parcourir données](/windows/desktop/api/shlobj_core/ns-shlobj_core-_browseinfoa) pour une description détaillée.

*piFolderImage*<br/>
[out] Pointeur vers la valeur d’entier dans lequel la méthode écrit à l’index d’image du dossier sélectionné.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur sélectionne un dossier à partir de la boîte de dialogue ; sinon 0.

### <a name="remarks"></a>Notes

Lorsque vous appelez cette méthode, l’application crée et affiche une boîte de dialogue qui permet à l’utilisateur sélectionner un dossier. La méthode écrit le chemin d’accès du dossier dans le *strOutFolder* paramètre.

### <a name="example"></a>Exemple

L’exemple suivant montre comment récupérer une référence à un `CShellManager` objet à l’aide de la `CWinAppEx::GetShellManager` (méthode) et comment utiliser le `BrowseForFolder` (méthode). Cet extrait de code fait partie de la [exemple Explorer](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

##  <a name="concatenateitem"></a>  CShellManager::ConcatenateItem

Crée une nouvelle liste contenant deux PIDLs.

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>Paramètres

*pidl1*<br/>
[in] Le premier élément.

*pidl2*<br/>
[in] Le deuxième élément.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la nouvelle liste d’éléments si la fonction réussit, sinon NULL.

### <a name="remarks"></a>Notes

Cette méthode crée un nouveau [ITEMIDLIST](/windows/desktop/api/shtypes/ns-shtypes-_itemidlist) suffisamment grande pour contenir les deux *pidl1* et *pidl2*. Elle copie ensuite *pidl1* et *pidl2* dans la nouvelle liste.

##  <a name="copyitem"></a>  CShellManager::CopyItem

Copie une liste d’éléments.

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>Paramètres

*pidlSource*<br/>
[in] La liste d’éléments d’origine.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la liste de l’élément qui vient d’être créé en cas de réussite ; Sinon, NULL.

### <a name="remarks"></a>Notes

La liste d’éléments nouvellement créée a la même taille que la liste d’éléments source.

##  <a name="createitem"></a>  CShellManager::CreateItem

Crée un nouveau PIDL.

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>Paramètres

*cbSize*<br/>
[in] La taille de la liste d’éléments.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la liste d’éléments créé en cas de réussite ; Sinon, NULL.

##  <a name="cshellmanager"></a>  CShellManager::CShellManager

Construit un objet `CShellManager`.

```
CShellManager();
```

### <a name="remarks"></a>Notes

Dans la plupart des cas, vous n’avez pas à créer un `CShellManager` directement. Par défaut, l’infrastructure crée un pour vous. Pour obtenir un pointeur vers le `CShellManager`, appelez [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager). Si vous ne créez pas un `CShellManager` manuellement, vous devez l’initialiser avec la méthode [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager).

##  <a name="freeitem"></a>  CShellManager::FreeItem

Supprime une liste d’éléments.

```
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>Paramètres

*pidl*<br/>
[in] Une liste d’éléments à supprimer.

##  <a name="getitemcount"></a>  CShellManager::GetItemCount

Retourne le nombre d’éléments dans une liste d’éléments.

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Paramètres

*pidl*<br/>
[in] Pointeur vers une liste d’éléments.

### <a name="return-value"></a>Valeur de retour

Le nombre d’éléments dans la liste d’éléments.

##  <a name="getitemsize"></a>  CShellManager::GetItemSize

Retourne la taille d’une liste d’éléments.

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Paramètres

*pidl*<br/>
[in] Pointeur vers une liste d’éléments.

### <a name="return-value"></a>Valeur de retour

La taille de la liste d’éléments.

##  <a name="getnextitem"></a>  CShellManager::GetNextItem

Récupère l’élément suivant à partir d’un pointeur désignant une liste d’identificateur élément (PIDL).

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Paramètres

*pidl*<br/>
[in] La liste des éléments pour effectuer une itération.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’élément suivant dans la liste.

### <a name="remarks"></a>Notes

S’il n’y a pas d’autres éléments dans la liste, cette méthode retourne NULL.

##  <a name="getparentitem"></a>  CShellManager::GetParentItem

Récupère le parent d’un pointeur vers une liste d’identificateur éléments (PIDL).

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>Paramètres

*lpidl*<br/>
[in] Un PIDL dont le parent est récupéré.

*lpidlParent*<br/>
[out] Une référence à un PIDL où la méthode stocke le résultat.

### <a name="return-value"></a>Valeur de retour

Le niveau du parent PIDL.

### <a name="remarks"></a>Notes

Le niveau d’un PIDL est relatif le bureau. Le bureau PIDL est considérée comme ayant un niveau de 0.

##  <a name="itemfrompath"></a>  CShellManager::ItemFromPath

Récupère le pointeur désignant une liste d’identificateur élément (PIDL) à partir de l’élément identifié par un chemin d’accès de la chaîne.

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>Paramètres

*lpszPath*<br/>
[in] Chaîne qui spécifie le chemin d’accès pour l’élément.

*pidl*<br/>
[out] Une référence à un PIDL. La méthode utilise cette PIDL pour stocker le pointeur vers sa valeur de retour.

### <a name="return-value"></a>Valeur de retour

Retourne NOERROR en cas de réussite ; valeur d’erreur défini par OLE.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
