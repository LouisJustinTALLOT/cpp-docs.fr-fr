---
title: Crecentfilelist, classe
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
ms.openlocfilehash: 30536d91d057de4e551b5a28200dd903e12713b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372177"
---
# <a name="crecentfilelist-class"></a>Crecentfilelist, classe

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
|[CRecentFileList::Add](#add)|Ajoute un fichier à la liste des fichiers MRU.|
|[CRecentFileList::GetDisplayName](#getdisplayname)|Fournit un nom d’affichage pour l’affichage du menu d’un nom de fichier des derniers fichiers utilisés.|
|[CRecentFileList::GetSize](#getsize)|Récupère le nombre de fichiers dans la liste des fichiers MRU.|
|[CRecentFileList::ReadList](#readlist)|Lit la liste des fichiers des derniers fichiers utilisés dans le Registre ou. Fichier INI.|
|[CRecentFileList::Remove](#remove)|Supprime un fichier à partir de la liste des fichiers MRU.|
|[CRecentFileList::UpdateMenu](#updatemenu)|Met à jour l’affichage du menu de la liste des fichiers MRU.|
|[CRecentFileList::WriteList](#writelist)|Écrit la liste des fichiers des derniers fichiers utilisés à partir du Registre ou. Fichier INI.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CRecentFileList::operator \[ \]](#operator_at)|Retourne un `CString` objet à une position donnée.|

## <a name="remarks"></a>Notes

Les fichiers peuvent être ajoutés ou supprimés à partir de la liste des fichiers des derniers fichiers utilisés, la liste des fichiers permettre être lues ou écrite dans le Registre ou un. Fichier INI et le menu Affichage de la liste des fichiers MRU peuvent être mis à jour.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CRecentFileList`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxadv.h

##  <a name="add"></a>  CRecentFileList::Add

Ajoute un fichier à la liste des fichiers récemment utilisée (MRU).

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
Spécifie l’ID de modèle d’Application utilisateur pour l’application.

*pItem*<br/>
Spécifie un pointeur vers l’élément d’interpréteur de commandes à ajouter à la liste.

*pLink*<br/>
Spécifie un pointeur vers le lien d’interpréteur de commandes à ajouter à la liste.

*pidl*<br/>
Spécifie la liste d’ID pour l’élément d’interpréteur de commandes qui doit être ajouté au dossier docs récente.

### <a name="remarks"></a>Notes

Le nom de fichier sera ajouté en haut de la liste des derniers fichiers utilisés. Si le nom de fichier existe déjà dans la liste des derniers fichiers utilisés, il sera déplacé vers le haut.

##  <a name="crecentfilelist"></a>  CRecentFileList::CRecentFileList

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
Décalage de la numérotation dans l’affichage du menu de la liste des fichiers MRU (le plus récemment utilisé).

*lpszSection*<br/>
Pointe vers le nom de la section du Registre ou l’application. Fichier INI dans lequel la liste des fichiers MRU est lu et/ou écrite.

*lpszEntryFormat*<br/>
Pointe vers une chaîne de format à utiliser pour les noms des entrées stockées dans le Registre ou l’application. Fichier INI.

*nSize*<br/>
Nombre maximal de fichiers dans la liste des fichiers MRU.

*nMaxDispLen*<br/>
Longueur maximale, en caractères, disponibles pour l’affichage du menu d’un nom de fichier dans la liste des fichiers MRU.

### <a name="remarks"></a>Notes

La chaîne de format vers lequel pointe *lpszEntryFormat* doit contenir « %d », qui sera utilisé pour la substitution de l’index de chaque élément de la liste des fichiers récents. Par exemple, si la chaîne de format est `"file%d"` alors les entrées seront nommées `file0`, `file1`, et ainsi de suite.

##  <a name="getdisplayname"></a>  CRecentFileList::GetDisplayName

Obtient un nom d’affichage pour un fichier dans la liste des fichiers MRU, pour une utilisation dans l’affichage du menu de la liste des derniers fichiers utilisés.

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
Chemin d’accès complet du fichier dont le nom doit être affiché dans la liste de menu des fichiers de la liste des fichiers récents.

*nIndex*<br/>
Index de base zéro du fichier dans la liste des fichiers MRU.

*lpszCurDir*<br/>
Chaîne contenant le répertoire actif.

*nCurDir*<br/>
Longueur de la chaîne de répertoire en cours.

*bAtLeastName*<br/>
Si elle est différente de zéro, indique que le nom du fichier de base doit être retourné, même si elle dépasse la longueur maximale d’affichage (passée en tant que le *nMaxDispLen* paramètre à la `CRecentFileList` constructeur).

### <a name="return-value"></a>Valeur de retour

**FALSE** s’il n’existe aucun nom de fichier à l’index spécifié dans la liste des fichiers récemment utilisée (MRU).

### <a name="remarks"></a>Notes

Si le fichier est dans le répertoire actif, la fonction laisse le répertoire désactive l’affichage. Si le nom de fichier est trop long, le répertoire et l’extension sont supprimés. Si le nom de fichier est toujours trop long, le nom d’affichage est défini sur une chaîne vide, sauf si *bAtLeastName* est différent de zéro.

##  <a name="getsize"></a>  CRecentFileList::GetSize

Récupère le nombre de fichiers dans la liste des fichiers MRU.

```
int GetSize() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de fichiers en cours plus récemment (MRU) fichiers utilisés.

##  <a name="operator_at"></a>  CRecentFileList::operator [ ]

L’indice surchargé (`[]`) opérateur retourne un seul `CString` spécifié par l’index de base zéro dans *nIndex*.

```
CString& operator[ ](int nindex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro d’un `CString` dans un ensemble de `CString`s.

##  <a name="readlist"></a>  CRecentFileList::ReadList

Lit le plus récemment (MRU) liste des fichiers utilisés à partir du Registre ou de l’application. Fichier INI.

```
virtual void ReadList();
```

##  <a name="remove"></a>  CRecentFileList::Remove

Supprime un fichier à partir de la liste des fichiers MRU.

```
virtual void Remove(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
Index de base zéro du fichier à supprimer de la liste des fichiers récemment utilisée (MRU).

##  <a name="updatemenu"></a>  CRecentFileList::UpdateMenu

Met à jour l’affichage du menu de la liste des fichiers MRU.

```
virtual void UpdateMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Paramètres

*pCmdUI*<br/>
Un pointeur vers le [CCmdUI](../../mfc/reference/ccmdui-class.md) objet pour le menu de liste des derniers fichiers utilisé (MRU) fichier.

##  <a name="writelist"></a>  CRecentFileList::WriteList

Écrit le plus récemment (MRU) liste des fichiers utilisés dans le Registre ou l’application. Fichier INI.

```
virtual void WriteList();
```

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
