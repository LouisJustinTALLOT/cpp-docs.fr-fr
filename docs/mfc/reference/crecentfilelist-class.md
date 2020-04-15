---
title: Classe CRecentFileList
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
ms.openlocfilehash: a2102c6a39c14c548828e57ad1c49de6a5bc03dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370906"
---
# <a name="crecentfilelist-class"></a>Classe CRecentFileList

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
|[CRecentFileList::Ajouter](#add)|Ajoute un fichier à la liste de fichiers MRU.|
|[CRecentFileList::GetDisplayName](#getdisplayname)|Fournit un nom d’affichage pour l’affichage du menu d’un nom de fichier MRU.|
|[CRecentFileList::GetSize](#getsize)|Récupère le nombre de fichiers dans la liste de fichiers MRU.|
|[CRecentFileList::ReadList](#readlist)|Lit la liste des fichiers MRU du registre ou . Fichier INI.|
|[CRecentFileList::Supprimer](#remove)|Supprime un fichier de la liste de fichiers MRU.|
|[CRecentFileList::UpdateMenu](#updatemenu)|Mise à jour de l’affichage du menu de la liste de fichiers MRU.|
|[CRecentFileList::WriteList](#writelist)|Rédige la liste des fichiers MRU du registre ou . Fichier INI.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CRecentFileList::opérateur \[\]](#operator_at)|Renvoie `CString` un objet à une position donnée.|

## <a name="remarks"></a>Notes

Les fichiers peuvent être ajoutés ou supprimés de la liste de fichiers MRU, la liste des fichiers peut être lue ou écrite au registre ou à un . Le fichier INI et le menu affichant la liste de fichiers MRU peuvent être mis à jour.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CRecentFileList`

## <a name="requirements"></a>Spécifications

**En-tête:** afxadv.h

## <a name="crecentfilelistadd"></a><a name="add"></a>CRecentFileList::Ajouter

Ajoute un fichier à la liste de fichiers la plus récemment utilisée (MRU).

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

*lpszPathName (en)*<br/>
Spécifie le nom de chemin à ajouter à la liste.

*lpszAppID (en)*<br/>
Spécifie l’ID modèle d’utilisateur d’application pour l’application.

*pItem (en)*<br/>
Spécifie un pointeur à Shell Item à ajouter à la liste.

*Plink*<br/>
Spécifie un pointeur sur Shell Link à ajouter à la liste.

*pidl pidl*<br/>
Spécifie l’IDLIST pour l’élément shell qui doit être ajouté au dossier docs récent.

### <a name="remarks"></a>Notes

Le nom du fichier sera ajouté au haut de la liste MRU. Si le nom du fichier existe déjà dans la liste MRU, il sera déplacé vers le haut.

## <a name="crecentfilelistcrecentfilelist"></a><a name="crecentfilelist"></a>CRecentFileList::CRecentFileList

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

*nStart (en)*<br/>
Décalage pour la numérotation dans l’affichage du menu de la liste de fichiers MRU (plus récemment utilisée).

*lpszSection*<br/>
Indique le nom de la section du registre ou de la demande . Fichier INI où la liste des fichiers MRU est lue et/ou écrite.

*lpszEntryFormat (en)*<br/>
Points à une chaîne de format à utiliser pour les noms des entrées stockées dans le registre ou l’application . Fichier INI.

*nSize (en)*<br/>
Nombre maximum de fichiers dans la liste de fichiers MRU.

*nMaxDispLen (en)*<br/>
Longueur maximale, en caractères, disponible pour l’affichage du menu d’un nom de fichier dans la liste de fichiers MRU.

### <a name="remarks"></a>Notes

La chaîne de format indiquée par *lpszEntryFormat* devrait contenir "%d", qui sera utilisé pour remplacer l’index de chaque article MRU. Par exemple, si la `"file%d"` chaîne de format `file0` `file1`est alors les entrées seront nommées, , et ainsi de suite.

## <a name="crecentfilelistgetdisplayname"></a><a name="getdisplayname"></a>CRecentFileList::GetDisplayName

Obtient un nom d’affichage pour un fichier dans la liste de fichiers MRU, pour une utilisation dans l’affichage du menu de la liste MRU.

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
Chemin complet du fichier dont le nom doit être affiché dans la liste de menu des fichiers MRU.

*nIndex*<br/>
Indice zéro du fichier dans la liste de fichiers MRU.

*lpszCurDir*<br/>
Chaîne tenant le répertoire actuel.

*nCurDir (en)*<br/>
Longueur de la chaîne répertoire actuelle.

*bAtLeastName (en)*<br/>
Si nonzero, indique que le nom de base du fichier doit être retourné, même s’il dépasse `CRecentFileList` la longueur maximale de l’affichage (passé comme le paramètre *nMaxDispLen* au constructeur).

### <a name="return-value"></a>Valeur de retour

**FALSE** s’il n’y a pas de nom de fichier à l’indice spécifié dans la liste de fichiers la plus récemment utilisée (MRU).

### <a name="remarks"></a>Notes

Si le fichier est dans l’annuaire actuel, la fonction laisse le répertoire hors de l’écran. Si le nom de fichier est trop long, l’annuaire et l’extension sont dépouillés. Si le nom de fichier est encore trop long, le nom d’affichage est réglé sur une chaîne vide à moins que *bAtLeastName* ne soit nonzero.

## <a name="crecentfilelistgetsize"></a><a name="getsize"></a>CRecentFileList::GetSize

Récupère le nombre de fichiers dans la liste de fichiers MRU.

```
int GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de fichiers dans la liste de fichiers la plus utilisée récemment (MRU).

## <a name="crecentfilelistoperator--"></a><a name="operator_at"></a>CRecentFileList::opérateur [ ]

Le sous-scriptum`[]`surchargé () `CString` opérateur retourne un seul spécifié par l’indice zéro dans *nIndex*.

```
CString& operator[ ](int nindex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Indice zéro d’un `CString` dans `CString`un ensemble de s.

## <a name="crecentfilelistreadlist"></a><a name="readlist"></a>CRecentFileList::ReadList

Lit la liste de fichiers la plus récemment utilisée (MRU) du registre ou de la demande . Fichier INI.

```
virtual void ReadList();
```

## <a name="crecentfilelistremove"></a><a name="remove"></a>CRecentFileList::Supprimer

Supprime un fichier de la liste de fichiers MRU.

```
virtual void Remove(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index zéro du fichier à supprimer de la liste de fichiers la plus utilisée récemment (MRU).

## <a name="crecentfilelistupdatemenu"></a><a name="updatemenu"></a>CRecentFileList::UpdateMenu

Mise à jour de l’affichage du menu de la liste de fichiers MRU.

```
virtual void UpdateMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI (en)*<br/>
Un pointeur à l’objet [CCmdUI](../../mfc/reference/ccmdui-class.md) pour le menu de liste de fichiers le plus récemment utilisé (MRU).

## <a name="crecentfilelistwritelist"></a><a name="writelist"></a>CRecentFileList::WriteList

Écrit la liste de fichiers la plus récemment utilisée (MRU) dans le registre ou celui de la demande . Fichier INI.

```
virtual void WriteList();
```

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
