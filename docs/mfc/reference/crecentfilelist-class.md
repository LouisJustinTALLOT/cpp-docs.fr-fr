---
description: 'En savoir plus sur : classe CRecentFileList'
title: CRecentFileList, classe
ms.date: 11/04/2016
f1_keywords:
- CRecentFileList
- AFXADV/CRecentFileList
- AFXADV/CRecentFileList::CRecentFileList
- AFXADV/CRecentFileList::Add
- AFXADV/CRecentFileList::GetDisplayName
- AFXADV/CRecentFileList::GetSize
- AFXADV/CRecentFileList::ReadList
- AFXADV/CRecentFileList::Remove
- AFXADV/CRecentFileList::UpdateMenu
- AFXADV/CRecentFileList::WriteList
helpviewer_keywords:
- CRecentFileList [MFC], CRecentFileList
- CRecentFileList [MFC], Add
- CRecentFileList [MFC], GetDisplayName
- CRecentFileList [MFC], GetSize
- CRecentFileList [MFC], ReadList
- CRecentFileList [MFC], Remove
- CRecentFileList [MFC], UpdateMenu
- CRecentFileList [MFC], WriteList
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
ms.openlocfilehash: 9433e65336cba1018c7bff8cf3a90e239ae5e3eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301124"
---
# <a name="crecentfilelist-class"></a>CRecentFileList, classe

Prend en charge le contrôle de la liste des derniers fichiers utilisés (MRU).

## <a name="syntax"></a>Syntaxe

```
class CRecentFileList
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRecentFileList::CRecentFileList](#crecentfilelist)|Construit un objet `CRecentFileList`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRecentFileList :: Add](#add)|Ajoute un fichier à la liste des fichiers MRU.|
|[CRecentFileList :: GetDisplayName](#getdisplayname)|Fournit un nom d’affichage pour l’affichage du menu d’un nom de fichier MRU.|
|[CRecentFileList :: est à obtenir](#getsize)|Récupère le nombre de fichiers dans la liste des fichiers MRU.|
|[CRecentFileList :: ReadList (lire](#readlist)|Lit la liste des fichiers MRU à partir du registre ou. Fichier INI.|
|[CRecentFileList :: Remove](#remove)|Supprime un fichier de la liste des fichiers MRU.|
|[CRecentFileList::UpdateMenu](#updatemenu)|Met à jour l’affichage du menu de la liste des fichiers MRU.|
|[CRecentFileList::WriteList](#writelist)|Écrit la liste de fichiers MRU à partir du registre ou. Fichier INI.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CRecentFileList ::, opérateur \[\]](#operator_at)|Retourne un `CString` objet à une position donnée.|

## <a name="remarks"></a>Notes

Les fichiers peuvent être ajoutés ou supprimés de la liste des fichiers MRU, la liste des fichiers peut être lue ou écrite dans le registre ou un. INI et le menu affichant la liste des fichiers MRU peut être mis à jour.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CRecentFileList`

## <a name="requirements"></a>Spécifications

**En-tête :** afxadv. h

## <a name="crecentfilelistadd"></a><a name="add"></a> CRecentFileList :: Add

Ajoute un fichier à la liste des derniers fichiers utilisés (MRU).

```
virtual void Add(LPCTSTR lpszPathName);

virtual void Add(
    LPCTSTR lpszPathName,
    LPCTSTR lpszAppID);

void Add(
    IShellItem* pItem,
    LPCTSTR lpszAppID);

void Add(
    IShellLink* pLink,
    LPCTSTR lpszAppID);

void Add(
    PIDLIST_ABSOLUTE pidl,
    LPCTSTR lpszAppID);
```

### <a name="parameters"></a>Paramètres

*lpszPathName*<br/>
Spécifie le chemin d’accès à ajouter à la liste.

*lpszAppID*<br/>
Spécifie l’ID du modèle utilisateur de l’application.

*pItem*<br/>
Spécifie un pointeur vers un élément de Shell à ajouter à la liste.

*pLink*<br/>
Spécifie un pointeur vers le lien de l’interpréteur de commandes à ajouter à la liste.

*pidl*<br/>
Spécifie le IDLIST pour l’élément de Shell qui doit être ajouté au dossier docs récent.

### <a name="remarks"></a>Notes

Le nom de fichier est ajouté en haut de la liste MRU. Si le nom de fichier existe déjà dans la liste MRU, il sera déplacé vers le haut.

## <a name="crecentfilelistcrecentfilelist"></a><a name="crecentfilelist"></a> CRecentFileList::CRecentFileList

Construit un objet `CRecentFileList`.

```
CRecentFileList(
    UINT nStart,
    LPCTSTR lpszSection,
    LPCTSTR lpszEntryFormat,
    int nSize,
    int nMaxDispLen = AFX_ABBREV_FILENAME_LEN);
```

### <a name="parameters"></a>Paramètres

*nStart*<br/>
Décalage de la numérotation dans l’affichage du menu de la liste des fichiers MRU (utilisé le plus récemment).

*lpszSection*<br/>
Pointe vers le nom de la section du registre ou de l’application. Fichier INI dans lequel la liste des fichiers MRU est lue et/ou écrite.

*lpszEntryFormat*<br/>
Pointe vers une chaîne de format à utiliser pour les noms des entrées stockées dans le registre ou dans l’application. Fichier INI.

*nSize*<br/>
Nombre maximal de fichiers dans la liste des fichiers MRU.

*nMaxDispLen*<br/>
Longueur maximale, en caractères, disponible pour l’affichage du menu d’un nom de fichier dans la liste des fichiers MRU.

### <a name="remarks"></a>Notes

La chaîne de format vers laquelle pointe *lpszEntryFormat* doit contenir "% d", qui sera utilisée pour remplacer l’index de chaque élément MRU. Par exemple, si la chaîne de format est, `"file%d"` les entrées sont nommées `file0` , `file1` , et ainsi de suite.

## <a name="crecentfilelistgetdisplayname"></a><a name="getdisplayname"></a> CRecentFileList :: GetDisplayName

Obtient le nom complet d’un fichier dans la liste des fichiers MRU, à utiliser dans l’affichage du menu de la liste MRU.

```
virtual BOOL GetDisplayName(
    CString& strName,
    int nIndex,
    LPCTSTR lpszCurDir,
    int nCurDir,
    BOOL bAtLeastName = TRUE) const;
```

### <a name="parameters"></a>Paramètres

*strName*<br/>
Chemin d’accès complet du fichier dont le nom doit être affiché dans la liste de menus des fichiers MRU.

*nIndex*<br/>
Index de base zéro du fichier dans la liste des fichiers MRU.

*lpszCurDir*<br/>
Chaîne contenant le répertoire actif.

*nCurDir*<br/>
Longueur de la chaîne de répertoire active.

*bAtLeastName*<br/>
Si la valeur est différente de zéro, indique que le nom de base du fichier doit être retourné, même s’il dépasse la longueur maximale d’affichage (passé comme paramètre *nMaxDispLen* au `CRecentFileList` constructeur).

### <a name="return-value"></a>Valeur renvoyée

**False** s’il n’existe aucun nom de fichier à l’index spécifié dans la liste des derniers fichiers utilisés (MRU).

### <a name="remarks"></a>Notes

Si le fichier se trouve dans le répertoire actif, la fonction laisse le répertoire en dehors de l’affichage. Si le nom de fichier est trop long, le répertoire et l’extension sont supprimés. Si le nom de fichier est toujours trop long, le nom complet est défini sur une chaîne vide, sauf si *bAtLeastName* est différent de zéro.

## <a name="crecentfilelistgetsize"></a><a name="getsize"></a> CRecentFileList :: est à obtenir

Récupère le nombre de fichiers dans la liste des fichiers MRU.

```
int GetSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de fichiers dans la liste des derniers fichiers utilisés (MRU).

## <a name="crecentfilelistoperator--"></a><a name="operator_at"></a> CRecentFileList :: Operator []

L’opérateur d’indice surchargé ( `[]` ) retourne un unique `CString` spécifié par l’index de base zéro dans *nIndex*.

```
CString& operator[ ](int nindex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro d’un `CString` dans un ensemble de `CString` .

## <a name="crecentfilelistreadlist"></a><a name="readlist"></a> CRecentFileList :: ReadList (lire

Lit la liste des derniers fichiers utilisés (MRU) à partir du registre ou de l’application. Fichier INI.

```
virtual void ReadList();
```

## <a name="crecentfilelistremove"></a><a name="remove"></a> CRecentFileList :: Remove

Supprime un fichier de la liste des fichiers MRU.

```
virtual void Remove(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro du fichier à supprimer de la liste des derniers fichiers utilisés (MRU).

## <a name="crecentfilelistupdatemenu"></a><a name="updatemenu"></a> CRecentFileList::UpdateMenu

Met à jour l’affichage du menu de la liste des fichiers MRU.

```
virtual void UpdateMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI*<br/>
Pointeur vers l’objet [CCmdUI](../../mfc/reference/ccmdui-class.md) pour le menu liste des fichiers utilisés le plus récemment (MRU).

## <a name="crecentfilelistwritelist"></a><a name="writelist"></a> CRecentFileList::WriteList

Écrit la liste des derniers fichiers utilisés (MRU) dans le registre ou dans l’application. Fichier INI.

```
virtual void WriteList();
```

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
