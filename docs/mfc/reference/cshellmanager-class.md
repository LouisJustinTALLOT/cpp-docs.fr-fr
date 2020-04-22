---
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
ms.openlocfilehash: 1c2f9ac1658f50f0ec5bd9e2f53d270c09bfcb6a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750321"
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
|[CShellManager::BrowseForFolder](#browseforfolder)|Affiche une boîte de dialogue qui permet à l’utilisateur de sélectionner un dossier shell.|
|[CShellManager::ConcatenateItem](#concatenateitem)|Concatenates deux PIDLs.|
|[CShellManager::CopyItem](#copyitem)|Crée un nouveau PIDL et copie le PIDL fourni.|
|[CShellManager::CreateItem](#createitem)|Crée un nouveau PIDL de la taille spécifiée.|
|[CShellManager::FreeItem](#freeitem)|Supprime le PIDL fourni.|
|[CShellManager::GetItemCount](#getitemcount)|Retourne le nombre d’articles dans le PIDL fourni.|
|[CShellManager::GetItemSize](#getitemsize)|Retourne la taille du PIDL fourni.|
|[CShellManager::GetNextItem](#getnextitem)|Retourne l’article suivant du PIDL.|
|[CShellManager::GetParentItem](#getparentitem)|Récupère l’élément parent de l’article fourni.|
|[CShellManager::ItemDePath](#itemfrompath)|Récupère le PIDL pour l’élément identifié par le chemin fourni.|

## <a name="remarks"></a>Notes

Les méthodes `CShellManager` de la classe traitent toutes des PIDL. Un PIDL est un identifiant unique pour un objet shell.

Vous ne devez `CShellManager` pas créer un objet manuellement. Il sera créé automatiquement par le cadre de votre application. Toutefois, vous devez appeler [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) pendant le processus d’initialisation de votre demande. Pour obtenir un pointeur au gestionnaire de la coquille pour votre application, appelez [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CShellManager](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxshellmanager.h

## <a name="cshellmanagerbrowseforfolder"></a><a name="browseforfolder"></a>CShellManager::BrowseForFolder

Affiche une boîte de dialogue qui permet à l’utilisateur de sélectionner un dossier shell.

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

*strOutFolder (en)*<br/>
[out] La chaîne utilisée par la méthode pour stocker le chemin du dossier sélectionné.

*pWndParent*<br/>
[dans] Un pointeur à la fenêtre parente.

*lplszInitialFolder*<br/>
[dans] Une chaîne qui contient le dossier qui est sélectionné par défaut lorsque la boîte de dialogue est affichée.

*lpszTitle (lpszTitle)*<br/>
[dans] Le titre de la boîte de dialogue.

*ulFlags*<br/>
[dans] Drapeaux spécifiant les options pour la boîte de dialogue. Voir [BROWSEINFO](/windows/win32/api/shlobj_core/ns-shlobj_core-browseinfow) pour la description détaillée.

*piFolderImage*<br/>
[out] Un pointeur à la valeur integer où la méthode écrit l’index d’image du dossier sélectionné.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’utilisateur sélectionne un dossier de la boîte de dialogue; sinon 0.

### <a name="remarks"></a>Notes

Lorsque vous appelez cette méthode, l’application crée et affiche une boîte de dialogue qui permet à l’utilisateur de sélectionner un dossier. La méthode écrira le chemin du dossier dans le paramètre *strOutFolder.*

### <a name="example"></a>Exemple

L’exemple suivant montre comment récupérer `CShellManager` une référence `CWinAppEx::GetShellManager` à un objet `BrowseForFolder` en utilisant la méthode et comment utiliser la méthode. Cet extrait de code fait partie de [l’échantillon Explorer](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

## <a name="cshellmanagerconcatenateitem"></a><a name="concatenateitem"></a>CShellManager::ConcatenateItem

Crée une nouvelle liste contenant deux PIDL.

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>Paramètres

*pidl1*<br/>
[dans] Le premier élément.

*pidl2*<br/>
[dans] Le deuxième élément.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la liste de nouvel élément si la fonction réussit, sinon NULL.

### <a name="remarks"></a>Notes

Cette méthode crée un nouvel [ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist) assez grand pour contenir à la fois *pidl1* et *pidl2*. Il copie ensuite *pidl1* et *pidl2* à la nouvelle liste.

## <a name="cshellmanagercopyitem"></a><a name="copyitem"></a>CShellManager::CopyItem

Copie d’une liste d’objets.

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>Paramètres

*pidlSource*<br/>
[dans] La liste d’objets d’origine.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la liste d’éléments nouvellement créé en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

La liste d’éléments nouvellement créée a la même taille que la liste d’éléments sources.

## <a name="cshellmanagercreateitem"></a><a name="createitem"></a>CShellManager::CreateItem

Crée un nouveau PIDL.

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>Paramètres

*cbSize*<br/>
[dans] La taille de la liste d’objets.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la liste d’éléments créés en cas de succès; autrement NULL.

## <a name="cshellmanagercshellmanager"></a><a name="cshellmanager"></a>CShellManager::CShellManager

Construit un objet `CShellManager`.

```
CShellManager();
```

### <a name="remarks"></a>Notes

Dans la plupart des cas, `CShellManager` vous n’avez pas à créer un directement. Par défaut, le cadre en crée un pour vous. Pour obtenir un `CShellManager`pointeur à la , appelez [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager). Si vous créez `CShellManager` un manuellement, vous devez l’initialiser avec la méthode [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager).

## <a name="cshellmanagerfreeitem"></a><a name="freeitem"></a>CShellManager::FreeItem

Supprime une liste d’éléments.

```cpp
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>Paramètres

*pidl pidl*<br/>
[dans] Une liste d’éléments à supprimer.

## <a name="cshellmanagergetitemcount"></a><a name="getitemcount"></a>CShellManager::GetItemCount

Retourne le nombre d’éléments dans une liste d’éléments.

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Paramètres

*pidl pidl*<br/>
[dans] Un pointeur à une liste d’objets.

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans la liste d’éléments.

## <a name="cshellmanagergetitemsize"></a><a name="getitemsize"></a>CShellManager::GetItemSize

Retourne la taille d’une liste d’objets.

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Paramètres

*pidl pidl*<br/>
[dans] Un pointeur à une liste d’objets.

### <a name="return-value"></a>Valeur de retour

La taille de la liste d’objets.

## <a name="cshellmanagergetnextitem"></a><a name="getnextitem"></a>CShellManager::GetNextItem

Récupère l’élément suivant à partir d’un pointeur à une liste d’identifiants d’élément (PIDL).

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Paramètres

*pidl pidl*<br/>
[dans] La liste des éléments à itérer.

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’élément suivant dans la liste.

### <a name="remarks"></a>Notes

S’il n’y a plus d’éléments dans la liste, cette méthode renvoie NULL.

## <a name="cshellmanagergetparentitem"></a><a name="getparentitem"></a>CShellManager::GetParentItem

Récupère le parent d’un pointeur sur une liste d’identifiants d’élément (PIDL).

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>Paramètres

*lpidl lpidl*<br/>
[dans] Un PIDL dont le parent sera récupéré.

*lpidlParent*<br/>
[out] Une référence à un PIDL où la méthode stockera le résultat.

### <a name="return-value"></a>Valeur de retour

Le niveau de la mère PIDL.

### <a name="remarks"></a>Notes

Le niveau d’un PIDL est relatif au bureau. Le PIDL de bureau est considéré comme ayant un niveau de 0.

## <a name="cshellmanageritemfrompath"></a><a name="itemfrompath"></a>CShellManager::ItemDePath

Récupère le pointeur sur une liste d’identifiants d’élément (PIDL) de l’élément identifié par un chemin de chaîne.

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>Paramètres

*lpszPath*<br/>
[dans] Une chaîne qui spécifie le chemin de l’article.

*pidl pidl*<br/>
[out] Une référence à un PIDL. La méthode utilise ce PIDL pour stocker le pointeur à sa valeur de retour.

### <a name="return-value"></a>Valeur de retour

Retourne NOERROR en cas de succès; une valeur d’erreur définie par l’OL.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
