---
title: Classe de CRecentFileList | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 337ecf8227f1d5c2abe0369abdea5662f882f3d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377251"
---
# <a name="crecentfilelist-class"></a>Classe de CRecentFileList
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
|[CRecentFileList::Add](#add)|Ajoute un fichier à la liste des fichiers des derniers fichiers utilisés.|  
|[CRecentFileList::GetDisplayName](#getdisplayname)|Fournit un nom d’affichage pour l’affichage du menu d’un nom de fichier des derniers fichiers utilisés.|  
|[CRecentFileList::GetSize](#getsize)|Récupère le nombre de fichiers dans la liste des derniers fichiers utilisés.|  
|[CRecentFileList::ReadList](#readlist)|Lit la liste des fichiers des derniers fichiers utilisés dans le Registre ou. Fichier INI.|  
|[CRecentFileList::Remove](#remove)|Supprime un fichier dans la liste des derniers fichiers utilisés.|  
|[CRecentFileList::UpdateMenu](#updatemenu)|Met à jour l’affichage du menu de la liste des fichiers des derniers fichiers utilisés.|  
|[CRecentFileList::WriteList](#writelist)|Écrit la dernière liste de fichiers à partir du Registre ou. Fichier INI.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[[] De CRecentFileList::operator](#operator_at)|Retourne un `CString` objet à une position donnée.|  
  
## <a name="remarks"></a>Notes  
 Les fichiers peuvent être ajoutés ou supprimés dans la liste des derniers fichiers utilisés, la liste des fichiers peut être lues ou écrite dans le Registre ou un. Ini et le menu Affichage de la liste des derniers fichiers peuvent être mis à jour.  
  
 Pour plus d’informations sur les éléments de menu des derniers fichiers utilisés, consultez  
  
-   L’article de la Base de connaissances Q243751 : Comment : ajouter des gestionnaires de commandes pour les éléments de Menu des derniers fichiers utilisés dans une Application MFC  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CRecentFileList`  
  
## <a name="requirements"></a>Spécifications  
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
 `lpszPathName`  
 Spécifie le chemin d’accès à ajouter à la liste.  
  
 `lpszAppID`  
 Spécifie l’ID de modèle d’Application utilisateur pour l’application.  
  
 `pItem`  
 Spécifie un pointeur vers l’élément de l’interpréteur de commandes à ajouter à la liste.  
  
 `pLink`  
 Spécifie un pointeur vers le lien d’interpréteur de commandes à ajouter à la liste.  
  
 `pidl`  
 Spécifie le conjointe pour l’élément de l’interpréteur de commandes qui doit être ajouté dans le dossier de documents récents.  
  
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
 `nStart`  
 Décalage de la numérotation dans l’affichage du menu de la liste des fichiers MRU (le plus récemment utilisé).  
  
 `lpszSection`  
 Pointe vers le nom de la section du Registre ou de l’application. Fichier INI dans lequel la liste des fichiers MRU est lu et/ou écrite.  
  
 `lpszEntryFormat`  
 Pointe vers une chaîne de format à utiliser pour les noms des entrées stockées dans le Registre ou l’application. Fichier INI.  
  
 `nSize`  
 Nombre maximal de fichiers dans la liste des derniers fichiers utilisés.  
  
 `nMaxDispLen`  
 Longueur maximale, en caractères, disponibles pour l’affichage du menu d’un nom de fichier dans la liste des derniers fichiers utilisés.  
  
### <a name="remarks"></a>Notes  
 La chaîne de format vers lequel pointe `lpszEntryFormat` doit contenir « %d », qui sera utilisé pour la substitution de l’index de chaque élément des derniers fichiers utilisés. Par exemple, si la chaîne de format est `"file%d"` ensuite les entrées sont nommées `file0`, `file1`, et ainsi de suite.  
  
##  <a name="getdisplayname"></a>  CRecentFileList::GetDisplayName  
 Obtient un nom d’affichage d’un fichier dans la liste des fichiers des derniers fichiers utilisés, pour une utilisation dans l’affichage du menu de la liste des derniers fichiers utilisés.  
  
```  
virtual BOOL GetDisplayName(
    CString& strName,  
    int nIndex,  
    LPCTSTR lpszCurDir,  
    int nCurDir,  
    BOOL bAtLeastName = TRUE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `strName`  
 Chemin d’accès complet du fichier dont le nom est affiché dans la liste de menu des fichiers de la liste des fichiers.  
  
 `nIndex`  
 Index de base zéro du fichier dans la liste des derniers fichiers utilisés.  
  
 *lpszCurDir*  
 Chaîne contenant le répertoire actif.  
  
 *nCurDir*  
 Longueur de la chaîne du répertoire en cours.  
  
 `bAtLeastName`  
 Si elle est différente de zéro, indique que le nom du fichier de base doit être retourné, même si elle dépasse la longueur maximale d’affichage (passée en tant que le `nMaxDispLen` paramètre à la `CRecentFileList` constructeur).  
  
### <a name="return-value"></a>Valeur de retour  
 **FALSE** si il n’existe aucun nom de fichier à l’index spécifié dans la liste des fichiers récemment utilisée (MRU).  
  
### <a name="remarks"></a>Notes  
 Si le fichier est dans le répertoire actif, la fonction laisse le répertoire désactive l’affichage. Si le nom de fichier est trop long, le répertoire et l’extension sont supprimés. Si le nom de fichier est toujours trop long, le nom d’affichage est défini sur une chaîne vide, sauf si `bAtLeastName` est différente de zéro.  
  
##  <a name="getsize"></a>  CRecentFileList::GetSize  
 Récupère le nombre de fichiers dans la liste des derniers fichiers utilisés.  
  
```  
int GetSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de fichiers en cours plus récemment (MRU) fichiers utilisés.  
  
##  <a name="operator_at"></a>  [] De CRecentFileList::operator  
 L’indice surchargé ( `[]`) opérateur retourne une seule `CString` spécifié par l’index de base zéro dans `nIndex`.  
  
```  
CString& operator[ ](int nindex);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index de base zéro d’un `CString` dans un ensemble de `CString`s.  
  
##  <a name="readlist"></a>  CRecentFileList::ReadList  
 Lit la liste des fichiers (MRU) à partir du Registre ou de l’application utilisés récemment. Fichier INI.  
  
```  
virtual void ReadList();
```  
  
##  <a name="remove"></a>  CRecentFileList::Remove  
 Supprime un fichier dans la liste des derniers fichiers utilisés.  
  
```  
virtual void Remove(int nIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index de base zéro du fichier à supprimer de la liste des fichiers récemment utilisée (MRU).  
  
##  <a name="updatemenu"></a>  CRecentFileList::UpdateMenu  
 Met à jour l’affichage du menu de la liste des fichiers des derniers fichiers utilisés.  
  
```  
virtual void UpdateMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Paramètres  
 `pCmdUI`  
 Un pointeur vers le [CCmdUI](../../mfc/reference/ccmdui-class.md) objet pour le menu de liste des derniers fichiers utilisé (MRU) fichier.  
  
##  <a name="writelist"></a>  CRecentFileList::WriteList  
 Écrit le plus récemment (MRU) fichiers utilisés dans le Registre ou l’application. Fichier INI.  
  
```  
virtual void WriteList();
```  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



