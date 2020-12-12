---
description: 'En savoir plus sur : classe CShellManager'
title: CShellManager, classe
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
ms.openlocfilehash: 67145782432c11ed62512eb618444fa19a4909ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264646"
---
# <a name="cshellmanager-class"></a>CShellManager, classe

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
|[CShellManager::BrowseForFolder](#browseforfolder)|Affiche une boîte de dialogue qui permet à l’utilisateur de sélectionner un dossier de Shell.|
|[CShellManager::ConcatenateItem](#concatenateitem)|Concatène deux PIDL.|
|[CShellManager :: CopyItem](#copyitem)|Crée un nouveau PIDL et y copie le PIDL fourni.|
|[CShellManager :: CreateItem](#createitem)|Crée un nouveau PIDL de la taille spécifiée.|
|[CShellManager::FreeItem](#freeitem)|Supprime le PIDL fourni.|
|[CShellManager :: GetItemCount](#getitemcount)|Retourne le nombre d’éléments dans le PIDL fourni.|
|[CShellManager::GetItemSize](#getitemsize)|Retourne la taille du PIDL fourni.|
|[CShellManager::GetNextItem](#getnextitem)|Retourne l’élément suivant à partir du PIDL.|
|[CShellManager::GetParentItem](#getparentitem)|Récupère l’élément parent de l’élément fourni.|
|[CShellManager::ItemFromPath](#itemfrompath)|Récupère le PIDL pour l’élément identifié par le chemin d’accès fourni.|

## <a name="remarks"></a>Notes

Les méthodes de la `CShellManager` classe traitent toutes les PIDL. Un PIDL est un identificateur unique pour un objet Shell.

Vous ne devez pas créer un `CShellManager` objet manuellement. Il sera créé automatiquement par l’infrastructure de votre application. Toutefois, vous devez appeler [CWinAppEx :: InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) pendant le processus d’initialisation de votre application. Pour obtenir un pointeur vers le gestionnaire de Shell de votre application, appelez [CWinAppEx :: GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CShellManager](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxshellmanager. h

## <a name="cshellmanagerbrowseforfolder"></a><a name="browseforfolder"></a> CShellManager::BrowseForFolder

Affiche une boîte de dialogue qui permet à l’utilisateur de sélectionner un dossier de Shell.

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
à Chaîne utilisée par la méthode pour stocker le chemin d’accès au dossier sélectionné.

*pWndParent*<br/>
dans Pointeur vers la fenêtre parente.

*lplszInitialFolder*<br/>
dans Chaîne qui contient le dossier sélectionné par défaut lorsque la boîte de dialogue est affichée.

*lpszTitle*<br/>
dans Titre de la boîte de dialogue.

*ulFlags*<br/>
dans Indicateurs spécifiant les options de la boîte de dialogue. Pour obtenir une description détaillée, consultez [BROWSEINFO](/windows/win32/api/shlobj_core/ns-shlobj_core-browseinfow) .

*piFolderImage*<br/>
à Pointeur vers la valeur entière où la méthode écrit l’index d’image du dossier sélectionné.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’utilisateur sélectionne un dossier dans la boîte de dialogue ; Sinon, 0.

### <a name="remarks"></a>Notes

Lorsque vous appelez cette méthode, l’application crée et affiche une boîte de dialogue qui permet à l’utilisateur de sélectionner un dossier. La méthode écrira le chemin d’accès du dossier dans le paramètre *strOutFolder* .

### <a name="example"></a>Exemple

L’exemple suivant montre comment récupérer une référence à un `CShellManager` objet à l’aide de la `CWinAppEx::GetShellManager` méthode et de l’utilisation de la `BrowseForFolder` méthode. Cet extrait de code fait partie de l' [exemple Explorer](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

## <a name="cshellmanagerconcatenateitem"></a><a name="concatenateitem"></a> CShellManager::ConcatenateItem

Crée une nouvelle liste contenant deux PIDL.

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>Paramètres

*pidl1*<br/>
dans Premier élément.

*pidl2*<br/>
dans Deuxième élément.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la nouvelle liste d’éléments si la fonction est réussie, sinon NULL.

### <a name="remarks"></a>Notes

Cette méthode crée un [ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist) suffisamment grand pour contenir à la fois *pidl1* et *pidl2*. Il copie ensuite *pidl1* et *pidl2* dans la nouvelle liste.

## <a name="cshellmanagercopyitem"></a><a name="copyitem"></a> CShellManager :: CopyItem

Copie une liste d’éléments.

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>Paramètres

*pidlSource*<br/>
dans Liste d’éléments d’origine.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la liste d’éléments nouvellement créée en cas de réussite ; Sinon, NULL.

### <a name="remarks"></a>Notes

La liste d’éléments nouvellement créée a la même taille que la liste des éléments sources.

## <a name="cshellmanagercreateitem"></a><a name="createitem"></a> CShellManager :: CreateItem

Crée un nouveau PIDL.

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>Paramètres

*cbSize*<br/>
dans Taille de la liste d’éléments.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la liste d’éléments créés en cas de réussite ; Sinon, NULL.

## <a name="cshellmanagercshellmanager"></a><a name="cshellmanager"></a> CShellManager::CShellManager

Construit un objet `CShellManager`.

```
CShellManager();
```

### <a name="remarks"></a>Notes

Dans la plupart des cas, vous n’avez pas besoin de créer un `CShellManager` directement. Par défaut, le Framework en crée un pour vous. Pour obtenir un pointeur vers le `CShellManager` , appelez [CWinAppEx :: GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager). Si vous créez un `CShellManager` manuellement, vous devez l’initialiser à l’aide de la méthode [CWinAppEx :: InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager).

## <a name="cshellmanagerfreeitem"></a><a name="freeitem"></a> CShellManager::FreeItem

Supprime une liste d’éléments.

```cpp
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>Paramètres

*pidl*<br/>
dans Liste d’éléments à supprimer.

## <a name="cshellmanagergetitemcount"></a><a name="getitemcount"></a> CShellManager :: GetItemCount

Retourne le nombre d’éléments dans une liste d’éléments.

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Paramètres

*pidl*<br/>
dans Pointeur vers une liste d’éléments.

### <a name="return-value"></a>Valeur renvoyée

Nombre d’éléments dans la liste d’éléments.

## <a name="cshellmanagergetitemsize"></a><a name="getitemsize"></a> CShellManager::GetItemSize

Retourne la taille d’une liste d’éléments.

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Paramètres

*pidl*<br/>
dans Pointeur vers une liste d’éléments.

### <a name="return-value"></a>Valeur renvoyée

Taille de la liste d’éléments.

## <a name="cshellmanagergetnextitem"></a><a name="getnextitem"></a> CShellManager::GetNextItem

Récupère l’élément suivant d’un pointeur vers une liste d’identificateurs d’élément (PIDL).

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Paramètres

*pidl*<br/>
dans Liste des éléments à itérer.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’élément suivant dans la liste.

### <a name="remarks"></a>Notes

S’il n’y a plus d’éléments dans la liste, cette méthode retourne la valeur NULL.

## <a name="cshellmanagergetparentitem"></a><a name="getparentitem"></a> CShellManager::GetParentItem

Récupère le parent d’un pointeur vers une liste d’identificateurs d’éléments (PIDL).

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>Paramètres

*lpidl*<br/>
dans PIDL dont le parent sera récupéré.

*lpidlParent*<br/>
à Référence à un PIDL où la méthode stocke le résultat.

### <a name="return-value"></a>Valeur renvoyée

Niveau du PIDL parent.

### <a name="remarks"></a>Notes

Le niveau d’un PIDL est relatif au bureau. Le PIDL de bureau est considéré comme ayant un niveau de 0.

## <a name="cshellmanageritemfrompath"></a><a name="itemfrompath"></a> CShellManager::ItemFromPath

Récupère le pointeur désignant une liste d’identificateurs d’élément (PIDL) à partir de l’élément identifié par un chemin d’accès de chaîne.

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>Paramètres

*lpszPath*<br/>
dans Chaîne qui spécifie le chemin d’accès de l’élément.

*pidl*<br/>
à Référence à un PIDL. La méthode utilise ce PIDL pour stocker le pointeur vers sa valeur de retour.

### <a name="return-value"></a>Valeur renvoyée

Retourne une erreur en cas de réussite ; valeur d’erreur définie par OLE.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
