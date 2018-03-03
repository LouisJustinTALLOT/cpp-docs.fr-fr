---
title: CFile (classe) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFile
- AFX/CFile
- AFX/CFile::CFile
- AFX/CFile::Abort
- AFX/CFile::Close
- AFX/CFile::Duplicate
- AFX/CFile::Flush
- AFX/CFile::GetFileName
- AFX/CFile::GetFilePath
- AFX/CFile::GetFileTitle
- AFX/CFile::GetLength
- AFX/CFile::GetPosition
- AFX/CFile::GetStatus
- AFX/CFile::LockRange
- AFX/CFile::Open
- AFX/CFile::Read
- AFX/CFile::Remove
- AFX/CFile::Rename
- AFX/CFile::Seek
- AFX/CFile::SeekToBegin
- AFX/CFile::SeekToEnd
- AFX/CFile::SetFilePath
- AFX/CFile::SetLength
- AFX/CFile::SetStatus
- AFX/CFile::UnlockRange
- AFX/CFile::Write
- AFX/CFile::hFileNull
- AFX/CFile::m_hFile
- AFX/CFile::m_pTM
dev_langs:
- C++
helpviewer_keywords:
- CFile [MFC], CFile
- CFile [MFC], Abort
- CFile [MFC], Close
- CFile [MFC], Duplicate
- CFile [MFC], Flush
- CFile [MFC], GetFileName
- CFile [MFC], GetFilePath
- CFile [MFC], GetFileTitle
- CFile [MFC], GetLength
- CFile [MFC], GetPosition
- CFile [MFC], GetStatus
- CFile [MFC], LockRange
- CFile [MFC], Open
- CFile [MFC], Read
- CFile [MFC], Remove
- CFile [MFC], Rename
- CFile [MFC], Seek
- CFile [MFC], SeekToBegin
- CFile [MFC], SeekToEnd
- CFile [MFC], SetFilePath
- CFile [MFC], SetLength
- CFile [MFC], SetStatus
- CFile [MFC], UnlockRange
- CFile [MFC], Write
- CFile [MFC], hFileNull
- CFile [MFC], m_hFile
- CFile [MFC], m_pTM
ms.assetid: b2eb5757-d499-4e67-b044-dd7d1abaa0f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f7a2b0e1dd95b460d6b6007e79378bc69f1b4ce
ms.sourcegitcommit: 2aeb507a426fc7881ea59115b1d5139c0a30ba91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="cfile-class"></a>CFile (classe)
Classe de base pour les classes de fichier Microsoft Foundation Class.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFile : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CFile::CFile](#cfile)|Construit un `CFile` objet à partir d’un handle de fichier ou chemin d’accès.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CFile::Abort](#abort)|Ferme un fichier en ignorant toutes les erreurs et avertissements.|  
|[CFile::Close](#close)|Ferme un fichier et supprime l’objet.|  
|[CFile::Duplicate](#duplicate)|Construit un objet en double en fonction de ce fichier.|  
|[CFile::Flush](#flush)|Vide toutes les données à écrire.|  
|[CFile::GetFileName](#getfilename)|Récupère le nom de fichier du fichier sélectionné.|  
|[CFile::GetFilePath](#getfilepath)|Récupère le chemin d’accès de fichier complet du fichier sélectionné.|  
|[CFile::GetFileTitle](#getfiletitle)|Récupère le titre du fichier sélectionné.|  
|[CFile::GetLength](#getlength)|Récupère la longueur du fichier.|  
|[CFile::GetPosition](#getposition)|Récupère le pointeur de fichier actuel.|  
|[CFile::GetStatus](#getstatus)|Récupère l’état du fichier ouvert, ou dans la version statique, récupère l’état du fichier spécifié (fonction statique, virtuel).|  
|[CFile::LockRange](#lockrange)|Verrouille une plage d’octets dans un fichier.|  
|[CFile::Open](#open)|En toute sécurité ouvre un fichier avec une option de test d’erreur.|  
|[CFile::Read](#read)|Lit les données (sans tampon) à partir d’un fichier à la position actuelle du fichier.|  
|[CFile::Remove](#remove)|Supprime le fichier spécifié (fonction statique).|  
|[CFile::Rename](#rename)|Renomme le fichier spécifié (fonction statique).|  
|[CFile::Seek](#seek)|Positionne le pointeur de fichier actuel.|  
|[CFile::SeekToBegin](#seektobegin)|Positionne le pointeur de fichier actuel au début du fichier.|  
|[CFile::SeekToEnd](#seektoend)|Positionne le pointeur de fichier en cours à la fin du fichier.|  
|[CFile::SetFilePath](#setfilepath)|Définit le chemin d’accès de fichier complet du fichier sélectionné.|  
|[CFile::SetLength](#setlength)|Modifie la longueur du fichier.|  
|[CFile::SetStatus](#setstatus)|Définit l’état du fichier spécifié (fonction statique, virtuel).|  
|[CFile::UnlockRange](#unlockrange)|Déverrouille une plage d’octets dans un fichier.|  
|[CFile::Write](#write)|Écrit des données (non) dans un fichier à la position actuelle du fichier.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CFile::operator descripteur](#operator_handle)|Un handle vers un `CFile` objet.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CFile::hFileNull](#hfilenull)|Détermine si le `CFile` objet possède un handle valide.|  
|[CFile::m_hFile](#m_hfile)|Contient généralement le handle de fichier du système d’exploitation.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CFile::m_pTM](#m_ptm)|Pointeur vers `CAtlTransactionManager` objet.|  
  
## <a name="remarks"></a>Notes  
 Il fournit directement des services d’entrée/sortie de disque sans tampon, binaire, et il indirectement prend en charge les fichiers texte et les fichiers de mémoire via ses classes dérivées. `CFile`fonctionne en association avec la `CArchive` classe pour prendre en charge la sérialisation d’objets de Microsoft Foundation Class.  
  
 La relation hiérarchique entre cette classe et ses classes dérivées permet au programme de fonctionner sur tous les objets de fichiers via le polymorphe `CFile` interface. Un fichier de mémoire, se comporte, par exemple, comme un fichier de disque.  
  
 Utilisez `CFile` et ses classes dérivées pour les e/s de disque à usage général. Utilisez `ofstream` ou d’autres classes iostream de Microsoft pour le texte mis en forme envoyés vers un fichier de disque.  
  
 Normalement, un fichier de disque est ouvert automatiquement dans `CFile` construction et la destruction de fermé sur. Les fonctions membres statiques permettent d’interroger l’état d’un fichier sans ouvrir le fichier.  
  
 Pour plus d’informations sur l’utilisation de `CFile`, consultez les articles [fichiers dans MFC](../../mfc/files-in-mfc.md) et [gestion des fichiers](../../c-runtime-library/file-handling.md) dans les *Run-Time Library Reference*.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CFile`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h  
  
##  <a name="abort"></a>CFile::Abort  
 Ferme le fichier associé à cet objet et le rend indisponible pour lire ou écrire.  
  
```  
virtual void Abort();
```  
  
### <a name="remarks"></a>Notes  
 Si vous n’avez pas fermé le fichier avant de détruire l’objet, le destructeur ferme pour vous.  
  
 Lors de la gestion des exceptions, `CFile::Abort` diffère `CFile::Close` de deux manières. Tout d’abord, le **abandonner** fonction pas lève une exception lors d’échecs de, car les échecs sont ignorées par **abandonner**. Ensuite, **abandonner** ne seront pas **ASSERT** si le fichier n’a pas été ouverte ou a été précédemment fermé.  
  
 Si vous avez utilisé **nouveau** pour allouer la `CFile` de l’objet sur le tas, vous devez le supprimer après la fermeture du fichier. **Abandonner** définit `m_hFile` à `CFile::hFileNull`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]  
  
##  <a name="cfile"></a>CFile::CFile  
 Construit et initialise un objet `CFile`.  
  
```  
CFile();  
CFile(CAtlTransactionManager* pTM);  
CFile(HANDLE hFile);

 
CFile(
LPCTSTR lpszFileName,  
UINT nOpenFlags);

 
CFile(
LPCTSTR lpszFileName,  
UINT nOpenFlags,  
CAtlTransactionManager* pTM);
```  
  
### <a name="parameters"></a>Paramètres  
 `hFile`  
 Handle d'un fichier à attacher à l'objet `CFile`.  
  
 `lpszFileName`  
 Chemin d'accès relatif ou complet d'un fichier à attacher à l'objet `CFile`.  
  
 `nOpenFlags`  
 Combinaison de bits (OR) ou options d'accès au fichier pour le fichier spécifié. Consultez la section Notes pour connaître les options possibles.  
  
 `pTM`  
 Pointeur vers l'objet CAtlTransactionManager  
  
### <a name="remarks"></a>Notes  
 Les cinq tableaux suivants répertorient les options possibles du paramètre `nOpenFlags`.  
  
 Choisissez une seule des options suivantes pour le mode d'accès aux fichiers. Le mode d'accès aux fichiers par défaut est `CFile::modeRead`, c'est-à-dire en lecture seule.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`CFile::modeRead`|Demande l'accès en lecture uniquement.|  
|`CFile::modeWrite`|Demande l'accès en écriture uniquement.|  
|`CFile::modeReadWrite`|Demande l'accès en lecture et en écriture.|  
  
 Choisissez l'une des options suivantes pour le mode caractère.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`CFile::typeBinary`|Définit le mode binaire (utilisé dans les classes dérivées uniquement).|  
|`CFile::typeText`|Définit le mode texte avec un traitement spécial pour les paires de sauts de ligne de transport (utilisé dans les classes dérivées uniquement).|  
|`CFile::typeUnicode`|Définit le mode Unicode (utilisé dans les classes dérivées uniquement). Le texte est écrit dans le fichier au format Unicode quand l'application est générée dans une configuration Unicode. Aucune marque d'ordre d'octet n'est écrite dans le fichier.|  
  
 Choisissez une seule des options suivantes pour le mode de partage de fichiers. Le mode de partage de fichiers par défaut est `CFile::shareExclusive`, c'est-à-dire exclusif.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`CFile::shareDenyNone`|Aucune restriction de partage.|  
|`CFile::shareDenyRead`|Refuse l'accès en lecture à tous les autres.|  
|`CFile::shareDenyWrite`|Refuse l'accès en écriture à tous les autres.|  
|`CFile::shareExclusive`|Refuse l'accès en lecture et en écriture à tous les autres.|  
  
 Choisissez la première ou les deux options suivantes pour le mode de création de fichiers. Le mode de création par défaut est `CFile::modeNoTruncate`, c'est-à-dire ouvrir l'existant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`CFile::modeCreate`|Crée un nouveau fichier si le fichier n’existe pas. ; Si le fichier existe déjà, [CFileException](../../mfc/reference/cfileexception-class.md) est déclenché.|  
|`CFile::modeNoTruncate`|Crée un fichier s'il n'en existe aucun. Sinon, si le fichier existe déjà, il est attaché à l'objet `CFile`.|  
  
 Choisissez les options de mise en cache de fichiers suivantes d'après leur description. Par défaut, le système utilise un modèle de mise en cache à usage général qui n'est pas disponible en tant qu'option.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`CFile::osNoBuffer`|Le système n'utilise pas de cache intermédiaire pour le fichier. Cette option annule les deux options suivantes.|  
|`CFile::osRandomAccess`|Le cache de fichiers est optimisé pour l'accès aléatoire. N'utilisez pas cette option et l'option d'analyse séquentielle.|  
|`CFile::osSequentialScan`|Le cache de fichiers est optimisé pour l'accès séquentiel. N'utilisez pas cette option et l'option d'accès aléatoire.|  
|`CFile::osWriteThrough`|Les opérations d'écriture sont effectuées sans délai.|  
  
 Choisissez l'option de sécurité suivante pour empêcher l'héritage du handle de fichier. Par défaut, tous les nouveaux processus enfants peuvent utiliser le handle de fichier.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`CFile::modeNoInherit`|Empêche les processus enfants d'utiliser le handle de fichier.|  
  
 Le constructeur par défaut initialise les membres mais n'attache aucun fichier à l'objet `CFile`. Après avoir utilisé ce constructeur, utilisez la [CFile::Open](#open) méthode pour ouvrir un fichier et l’attacher à la `CFile` objet.  
  
 Le constructeur avec un seul paramètre initialise les membres et attache un fichier existant à l'objet `CFile`.  
  
 Le constructeur avec deux paramètres initialise les membres et tente d'ouvrir le fichier spécifié. Si ce constructeur ouvre correctement le fichier spécifié, le fichier est attaché à l'objet `CFile`. Sinon, ce constructeur émet un pointeur vers un objet `CInvalidArgException`. Pour plus d’informations sur la gestion des exceptions, consultez [Exceptions](../../mfc/exception-handling-in-mfc.md).  
  
 Si un objet `CFile` ouvre correctement un fichier spécifié, ce dernier est fermé automatiquement quand l'objet `CFile` est détruit. Sinon, vous devez fermer explicitement le fichier une fois qu'il n'est plus attaché à l'objet `CFile`.  
  
### <a name="example"></a>Exemple  
 Le code suivant illustre l'utilisation de `CFile`.  
  
 [!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]  
  
##  <a name="close"></a>CFile::Close  
 Ferme le fichier associé à cet objet et le rend indisponible pour lire ou écrire.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Notes  
 Si vous n’avez pas fermé le fichier avant de détruire l’objet, le destructeur ferme pour vous.  
  
 Si vous avez utilisé **nouveau** pour allouer la `CFile` de l’objet sur le tas, vous devez le supprimer après la fermeture du fichier. **Fermer** définit `m_hFile` à `CFile::hFileNull`.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CFile::CFile](#cfile).  
  
##  <a name="duplicate"></a>CFile::Duplicate  
 Construit un doublon `CFile` objet pour un fichier donné.  
  
```  
virtual CFile* Duplicate() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un doublon `CFile` objet.  
  
### <a name="remarks"></a>Notes  
 Cela équivaut à la fonction runtime C `_dup`.  
  
##  <a name="flush"></a>CFile::Flush  
 Force toutes les données restantes dans la mémoire tampon de fichier à écrire dans le fichier.  
  
```  
virtual void Flush();
```  
  
### <a name="remarks"></a>Notes  
 L’utilisation de `Flush` ne garantit pas que le vidage de `CArchive` mémoires tampons. Si vous utilisez une archive, appelez [CArchive::Flush](../../mfc/reference/carchive-class.md#flush) premier.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CFile::SetFilePath](#setfilepath).  
  
##  <a name="getfilename"></a>CFile::GetFileName  
 Appelez cette fonction membre pour récupérer le nom d’un fichier spécifié.  
  
```  
virtual CString GetFileName() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Nom du fichier.  
  
### <a name="remarks"></a>Notes  
 Par exemple, lorsque vous appelez `GetFileName` pour générer un message à l’utilisateur sur le fichier `c:\windows\write\myfile.wri`, le nom de fichier, `myfile.wri`, est retourné.  
  
 Pour retourner le chemin d’accès complet du fichier, y compris le nom, appelez [GetFilePath](#getfilepath). Pour renvoyer le titre du fichier ( `myfile`), appelez [GetFileTitle](#getfiletitle).  
  
### <a name="example"></a>Exemple  
 Ce fragment de code s’ouvre le système. Fichier INI dans votre répertoire WINDOWS. Si trouvé, l’exemple imprime le nom et le chemin d’accès et le titre, comme indiqué dans la sortie :  
  
 [!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]  
  
##  <a name="getfilepath"></a>CFile::GetFilePath  
 Appelez cette fonction membre pour récupérer le chemin d’accès complet d’un fichier spécifié.  
  
```  
virtual CString GetFilePath() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le chemin d’accès complet du fichier spécifié.  
  
### <a name="remarks"></a>Notes  
 Par exemple, lorsque vous appelez `GetFilePath` pour générer un message à l’utilisateur sur le fichier `c:\windows\write\myfile.wri`, le chemin d’accès du fichier, `c:\windows\write\myfile.wri`, est retourné.  
  
 Pour retourner uniquement le nom du fichier ( `myfile.wri`), appelez [GetFileName](#getfilename). Pour renvoyer le titre du fichier ( `myfile`), appelez [GetFileTitle](#getfiletitle).  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [GetFileName](#getfilename).  
  
##  <a name="getfiletitle"></a>CFile::GetFileTitle  
 Appelez cette fonction membre pour récupérer le nom du fichier (le nom d’affichage) pour le fichier.  
  
```  
virtual CString GetFileTitle() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le titre du fichier sous-jacent.  
  
### <a name="remarks"></a>Notes  
 Cette méthode appelle [GetFileTitle](http://msdn.microsoft.com/library/windows/desktop/ms646924) pour récupérer le titre du fichier. En cas de réussite, la méthode retourne la chaîne par le système pour afficher le nom de fichier pour l’utilisateur. Sinon, la méthode appelle [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589) pour récupérer le nom de fichier (y compris l’extension de fichier) du fichier sous-jacent. Par conséquent, l’extension de fichier n’est pas toujours être incluse dans la chaîne de titre du fichier retourné. Pour plus d’informations, consultez [GetFileTitle](http://msdn.microsoft.com/library/windows/desktop/ms646924) et [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589) dans le Kit de développement logiciel Windows.  
  
 Pour retourner le chemin d’accès complet du fichier, y compris le nom, appelez [GetFilePath](#getfilepath). Pour retourner uniquement le nom du fichier, appelez [GetFileName](#getfilename).  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [GetFileName](#getfilename).  
  
##  <a name="getlength"></a>CFile::GetLength  
 Obtient la longueur actuelle de la logique du fichier en octets.  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La longueur du fichier.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]  
  
##  <a name="getposition"></a>CFile::GetPosition  
 Obtient la valeur actuelle du pointeur de fichier, qui peut être utilisé dans les appels suivants à `Seek`.  
  
```  
virtual ULONGLONG GetPosition() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le pointeur de fichier.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]  
  
##  <a name="getstatus"></a>CFile::GetStatus  
 Cette méthode récupère les informations d’état relatives à une donnée `CFile` instance d’objet ou un chemin d’accès de fichier donné.  
  
```  
BOOL GetStatus(CFileStatus& rStatus) const;  
  
static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,  
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `rStatus`  
 Une référence à un fourni par l’utilisateur **CFileStatus** structure qui recevront les informations d’état. Le **CFileStatus** structure comprend les champs suivants :  
  
- **CTime m_ctime** date et heure de création du fichier.  
  
- **CTime m_mtime** la date et l’heure de dernière modification du fichier.  
  
- **CTime m_atime** date et heure de dernier accès au fichier pour la lecture.  
  
- **ULONGLONG m_size** la taille logique du fichier en octets, comme indiqué par la commande DIR.  
  
- **OCTETS m_attribute** l’octet de l’attribut du fichier.  
  
- **char m_szFullName [_MAX_PATH]** le nom de fichier absolu dans le jeu de caractères Windows.  
  
 `lpszFileName`  
 Une chaîne de caractères Windows définie qui est le chemin d’accès au fichier souhaité. Le chemin d’accès peut être relatif ou absolu, ou il peut contenir un nom de chemin d’accès réseau.  
  
 `pTM`  
 Pointeur vers l'objet CAtlTransactionManager  
  
### <a name="return-value"></a>Valeur de retour  
 **TRUE** si les informations d’état pour le fichier spécifié sont correctement obtenues ; sinon, **FALSE**.  
  
### <a name="remarks"></a>Notes  
 La version non statiques de **GetStatus** récupère les informations d’état du fichier ouvert associé à la donnée `CFile` objet.  La version statique de **GetStatus** Obtient l’état du fichier à partir d’un chemin d’accès de fichier donné sans réellement l’ouverture du fichier. Cela est utile pour tester les droits d’accès et d’existence d’un fichier.  
  
 Le **m_attribute** membre de la **CFileStatus** structure fait référence à l’ensemble d’attributs de fichier. Le `CFile` classe fournit le **attribut** type d’énumération des attributs de fichier peut donc être spécifiés symboliquement :  
  
```  
enum Attribute {
    normal =    0x00,
    readOnly =  0x01,
    hidden =    0x02,
    system =    0x04,
    volume =    0x08,
    directory = 0x10,
    archive =   0x20
    };
```    
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#10](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_6.cpp)]  
  
##  <a name="hfilenull"></a>CFile::hFileNull  
 Détermine la présence d’un handle de fichier valide pour le `CFile` objet.  
  
```  
static AFX_DATA const HANDLE hFileNull;  
```  
  
### <a name="remarks"></a>Notes  
 Cette constante est utilisée pour déterminer si le `CFile` objet possède un descripteur de fichier valide.  
  
 L’exemple suivant illustre cette opération :  
  
 [!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]  
  
##  <a name="lockrange"></a>CFile::LockRange  
 Verrouille une plage d’octets dans un fichier ouvert, lever une exception si le fichier est déjà verrouillé.  
  
```  
virtual void LockRange(
    ULONGLONG dwPos,  
    ULONGLONG dwCount);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwPos`  
 Décalage d’octet du début de la plage d’octets à verrouiller.  
  
 `dwCount`  
 Le nombre d’octets dans la plage à verrouiller.  
  
### <a name="remarks"></a>Notes  
 Le verrouillage d’octets dans un fichier empêche l’accès à ces octets par d’autres processus. Vous pouvez verrouiller plus d’une région d’un fichier, mais aucune région qui se chevauche n’est autorisées.  
  
 Lorsque vous déverrouillez la région, à l’aide du `UnlockRange` fonction membre, la plage d’octets doit correspondre exactement à la région qui a été précédemment verrouillée. Le `LockRange` fonction ne fusionne pas les régions adjacentes ; Si deux régions verrouillées sont adjacentes, vous devez déverrouiller séparément chaque région.  
  
> [!NOTE]
>  Cette fonction n’est pas disponible pour la `CMemFile`-classe dérivée.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]  
  
##  <a name="m_hfile"></a>CFile::m_hFile  
 Contient le handle de fichier de système d’exploitation pour un fichier ouvert.  
  
```  
HANDLE m_hFile;  
```  
  
### <a name="remarks"></a>Notes  
 `m_hFile`est une variable publique de type **UINT**. Il contient `CFile::hFileNull` (un indicateur de vider le fichier indépendant du système d’exploitation) si le handle n’a pas été affecté.  
  
 Utilisation de `m_hFile` n’est pas recommandée, car les sens du membre dépend de la classe dérivée. `m_hFile`est établie à un membre public à des fins de prise en charge non polymorphes d’utilisation de la classe.  
  
##  <a name="m_ptm"></a>CFile::m_pTM  
 Pointeur vers un `CAtlTransactionManager` objet.  
  
```  
CAtlTransactionManager* m_pTM;  
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="open"></a>CFile::Open  
 Surchargé. **Ouvrez** est conçu pour une utilisation avec la valeur par défaut `CFile` constructeur.  
  
```  
virtual BOOL Open(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM,
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszFileName`  
 Chaîne qui est le chemin d’accès au fichier souhaité. Le chemin d’accès peut être relatif, absolu ou un nom de réseau (UNC).  
  
 `nOpenFlags`  
 A **UINT** qui définit le mode de partage et d’accès du fichier. Il spécifie l’action à entreprendre lors de l’ouverture du fichier. Vous pouvez combiner des options à l’aide de l’opération de bits OR ( **&#124;** ) (opérateur). Autorisation d’accès un à et un seul partage sont requis ; le **modeCreate** et **modeNoInherit** modes sont facultatifs. Consultez le [CFile](#cfile) constructeur pour obtenir la liste des options de mode.  
  
 `pError`  
 Pointeur vers un objet d’exception du fichier existant qui recevra l’état d’une opération ayant échoué.  
  
 `pTM`  
 Pointeur vers l'objet CAtlTransactionManager  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’ouverture a réussi ; Sinon, 0. Le `pError` paramètre n’est significatif uniquement si 0 est retourné.  
  
### <a name="remarks"></a>Notes  
 Les deux fonctions constituent une méthode « sécurisée » pour ouvrir un fichier dans lequel une défaillance est une condition normale, attendue.  
  
 Alors que le `CFile` constructeur lève une exception dans une condition d’erreur, **ouvrir** retournera **FALSE** de conditions d’erreur. **Ouvrez** peut toujours initialiser un [CFileException](../../mfc/reference/cfileexception-class.md) objet décrivant l’erreur, toutefois. Si vous ne fournissez pas le `pError` paramètre, ou si vous passez **NULL** pour `pError`, **ouvrir** retournera **FALSE** et ne pas lever un `CFileException`. Si vous passez un pointeur à une `CFileException`, et **ouvrir** rencontre une erreur, la fonction sera remplir avec des informations décrivant l’erreur. Dans ces cas seront **ouvrir** lève une exception.  
  
 Le tableau suivant décrit les résultats possibles de **ouvrir**.  
  
|`pError`|Erreur rencontrée|Valeur de retour|CFileException contenu|  
|--------------|------------------------|------------------|----------------------------|  
|**NULL**|Non|**TRUE**|N/A|  
|PTR pour`CFileException`|Non|**TRUE**|inchangé|  
|**NULL**|Oui|**FALSE**|N/A|  
|PTR pour`CFileException`|Oui|**FALSE**|initialisé pour décrire l’erreur|  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]  
  
 [!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]  
  
##  <a name="operator_handle"></a>CFile::operator descripteur  
 Utilisez cet opérateur pour passer un handle à un `CFile` de l’objet à des fonctions telles que [ReadFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365468) et [GetFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724320) qui attendent un `HANDLE`.  
  
```  
operator HANDLE() const;  
```  
  
##  <a name="read"></a>CFile::Read  
 Lit les données dans une mémoire tampon à partir du fichier associé à le `CFile` objet.  
  
```  
virtual UINT Read(
    void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpBuf`  
 Pointeur vers la mémoire tampon fournie par l’utilisateur qui doit recevoir les données lues à partir du fichier.  
  
 `nCount`  
 Le nombre maximal d’octets à lire à partir du fichier. Pour les fichiers en mode texte, les paires de sauts de ligne de chariot sont comptabilisés comme caractères uniques.  
  
### <a name="return-value"></a>Valeur de retour  
 Nombre d'octets transférés dans la mémoire tampon. Notez que pour tous les `CFile` classes, la valeur de retour peut être inférieure à `nCount` si la fin du fichier a été atteinte.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]  
  
 Pour un autre exemple, consultez [CFile::Open](#open).  
  
##  <a name="remove"></a>CFile::Remove  
 Cette fonction statique supprime le fichier spécifié par le chemin d’accès.  
  
```  
static void PASCAL Remove(
    LPCTSTR lpszFileName, 
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszFileName`  
 Chaîne qui est le chemin d’accès au fichier souhaité. Le chemin d’accès peut être relatif ou absolu et peut contenir un nom de réseau.  
  
 `pTM`  
 Pointeur vers l'objet CAtlTransactionManager  
  
### <a name="remarks"></a>Notes  
 Elle ne supprime pas un répertoire.  
  
 Le **supprimer** fonction membre lève une exception si le fichier connecté est ouvert ou si le fichier ne peut pas être supprimé. Cela équivaut à la commande DEL.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]  
  
##  <a name="rename"></a>CFile::Rename  
 Cette fonction statique renomme le fichier spécifié.  
  
```  
static void PASCAL Rename(
    LPCTSTR lpszOldName,  
    LPCTSTR lpszNewName,  
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszOldName`  
 L’ancien chemin d’accès.  
  
 `lpszNewName`  
 Le nouveau chemin d’accès.  
  
 `pTM`  
 Pointeur vers l'objet CAtlTransactionManager  
  
### <a name="remarks"></a>Notes  
 Impossible de renommer les répertoires. Cela équivaut à la commande REN.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]  
  
##  <a name="seek"></a>CFile::Seek  
 Repositionne le pointeur de fichier dans un fichier ouvert.  
  
```  
virtual ULONGLONG Seek(
LONGLONG lOff,  
UINT nFrom);
```  
  
### <a name="parameters"></a>Paramètres  
 `lOff`  
 Nombre d’octets à déplacer le pointeur de fichier. Les valeurs positives déplacent le pointeur de fichier vers la fin du fichier ; les valeurs négatives déplacent le pointeur de fichier vers le début du fichier.  
  
 `nFrom`  
 Position à partir de recherche. Consultez la section Notes pour les valeurs possibles.  
  
### <a name="return-value"></a>Valeur de retour  
 La position du pointeur de fichier si la méthode a réussi ; Sinon, la valeur de retour n’est pas définie et un pointeur vers un `CFileException` exception est levée.  
  
### <a name="remarks"></a>Notes  
 Le tableau suivant répertorie les valeurs possibles pour le `nFrom` paramètre.  
  
|Value|Description|  
|-----------|-----------------|  
|`CFile::begin`|Recherche à partir du début du fichier.|  
|`CFile::current`|Recherche de l’emplacement actuel du pointeur de fichier.|  
|`CFile::end`|Recherche de la fin du fichier.|  
  
 Lorsqu’un fichier est ouvert, le pointeur de fichier est positionné sur 0, le début du fichier.  
  
 Vous pouvez définir le pointeur de fichier à une position au-delà de la fin d’un fichier. Si vous faites cela, la taille du fichier n’augmente pas jusqu'à ce que vous écrivez dans le fichier.  
  
 Le Gestionnaire d’exceptions pour cette méthode doit supprimer l’objet exception après le traitement de l’exception.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]  
  
##  <a name="seektobegin"></a>CFile::SeekToBegin  
 Définit la valeur du pointeur de fichier au début du fichier.  
  
```  
void SeekToBegin();
```  
  
### <a name="remarks"></a>Notes  
 `SeekToBegin()` équivaut à `Seek( 0L, CFile::begin )`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]  
  
##  <a name="seektoend"></a>CFile::SeekToEnd  
 Définit la valeur du pointeur de fichier à la fin logique du fichier.  
  
```  
ULONGLONG SeekToEnd();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Longueur du fichier en octets.  
  
### <a name="remarks"></a>Notes  
 `SeekToEnd()` équivaut à `CFile::Seek( 0L, CFile::end )`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]  
  
##  <a name="setfilepath"></a>CFile::SetFilePath  
 Appelez cette fonction pour spécifier le chemin d’accès du fichier. par exemple, si le chemin d’accès d’un fichier n’est pas disponible lorsque une [CFile](../../mfc/reference/cfile-class.md) objet est construit, appelez `SetFilePath` à fournir.  
  
```  
virtual void SetFilePath(LPCTSTR lpszNewName);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszNewName`  
 Pointeur vers une chaîne qui spécifie le nouveau chemin d’accès.  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
> `SetFilePath`ne pas ouvrir le fichier ou de créer le fichier ; Il associe simplement le `CFile` objet avec un nom de chemin d’accès, qui peut ensuite être utilisé.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]  
  
##  <a name="setlength"></a>CFile::SetLength  
 Appelez cette fonction pour modifier la longueur du fichier.  
  
```  
virtual void SetLength(ULONGLONG dwNewLen);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwNewLen`  
 Longueur souhaitée du fichier en octets. Cette valeur peut être supérieure ou inférieure à la longueur actuelle du fichier. Le fichier sera étendu ou tronqué selon le cas.  
  
### <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Avec `CMemFile`, cette fonction peut lever un `CMemoryException` objet.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]  
  
##  <a name="setstatus"></a>CFile::SetStatus  
 Définit l’état du fichier associé à cet emplacement de fichier.  
  
```  
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,  
    const CFileStatus& status,  
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszFileName`  
 Chaîne qui est le chemin d’accès au fichier souhaité. Le chemin d’accès peut être relatif ou absolu et peut contenir un nom de réseau.  
  
 *status*  
 La mémoire tampon qui contient les informations d’état. Appelez le **GetStatus** fonction membre pour renseigner le **CFileStatus** avec les valeurs actuelles de la structure, puis apportez les modifications nécessaires. Si une valeur est 0, l’élément d’état correspondant n’est pas actualisé. Consultez le [GetStatus](#getstatus) fonction membre pour obtenir une description de la **CFileStatus** structure.  
  
 `pTM`  
 Pointeur vers l'objet CAtlTransactionManager  
  
### <a name="remarks"></a>Notes  
 Pour définir l’heure, vous devez modifier le **m_mtime** champ *état*.  
  
 Notez que lorsque vous effectuez un appel à `SetStatus` dans une tentative de modifier uniquement les attributs du fichier et le **m_mtime** membre de la structure d’état de fichier est différente de zéro, les attributs peuvent également être affectées (modification de l’horodatage peut avoir effets sur les attributs). Si vous souhaitez uniquement modifier les attributs du fichier, vous devez tout d’abord définir le **m_mtime** membre de la structure d’état de fichier à zéro et effectuez un appel à `SetStatus`.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]  
  
##  <a name="unlockrange"></a>CFile::UnlockRange  
 Déverrouille une plage d’octets dans un fichier ouvert.  
  
```  
virtual void UnlockRange(
    ULONGLONG dwPos,  
    ULONGLONG dwCount);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwPos`  
 Décalage d’octet du début de la plage d’octets à déverrouiller.  
  
 `dwCount`  
 Le nombre d’octets dans la plage à déverrouiller.  
  
### <a name="remarks"></a>Notes  
 Consultez la description de la [LockRange](#lockrange) fonction membre pour plus d’informations.  
  
> [!NOTE]
>  Cette fonction n’est pas disponible pour la `CMemFile`-classe dérivée.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]  
  
##  <a name="write"></a>CFile::Write  
 Écrit des données à partir d’une mémoire tampon dans le fichier associé à le `CFile` objet.  
  
```  
virtual void Write(
    const void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpBuf`  
 Pointeur vers la mémoire tampon fournie par l’utilisateur qui contient les données à écrire dans le fichier.  
  
 `nCount`  
 Le nombre d’octets à transférer de la mémoire tampon. Pour les fichiers en mode texte, les paires de sauts de ligne de chariot sont comptabilisés comme caractères uniques.  
  
### <a name="remarks"></a>Notes  
 **Écrire** lève une exception en réponse à plusieurs conditions, y compris la condition de disque plein.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]  
  
 En outre, consultez les exemples de [CFile::CFile](#cfile) et [CFile::Open](#open).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC DRAWCLI](../../visual-cpp-samples.md)   
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classe de CStdioFile](../../mfc/reference/cstdiofile-class.md)   
 [CMemFile, classe](../../mfc/reference/cmemfile-class.md)
