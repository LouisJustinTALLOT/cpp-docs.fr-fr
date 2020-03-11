---
title: CFile, classe
ms.date: 06/12/2018
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
ms.openlocfilehash: a9161764f6c8646766a73add01c25cce5619ad19
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855293"
---
# <a name="cfile-class"></a>CFile, classe

Classe de base pour les classes de fichier Microsoft Foundation Class.

## <a name="syntax"></a>Syntaxe

```
class CFile : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CFile :: CFile](#cfile)|Construit un objet `CFile` à partir d’un chemin d’accès ou d’un handle de fichier.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CFile :: Abort](#abort)|Ferme un fichier en ignorant tous les avertissements et erreurs.|
|[CFile :: Close](#close)|Ferme un fichier et supprime l’objet.|
|[CFile ::D quée](#duplicate)|Construit un objet en double basé sur ce fichier.|
|[CFile :: Flush](#flush)|Vide toutes les données encore à écrire.|
|[CFile :: GetFileName](#getfilename)|Récupère le nom du fichier sélectionné.|
|[CFile :: GetFilePath](#getfilepath)|Récupère le chemin d’accès complet au fichier sélectionné.|
|[CFile :: GetFileTitle](#getfiletitle)|Récupère le titre du fichier sélectionné.|
|[CFile :: GetLength](#getlength)|Récupère la longueur du fichier.|
|[CFile :: GetPosition](#getposition)|Récupère le pointeur de fichier actuel.|
|[CFile :: GetStatus](#getstatus)|Récupère l’état du fichier ouvert, ou dans la version statique, récupère l’état du fichier spécifié (fonction virtuelle statique).|
|[CFile :: LockRange](#lockrange)|Verrouille une plage d’octets dans un fichier.|
|[CFile :: Open](#open)|Ouvre un fichier en toute sécurité avec une option de test d’erreur.|
|[CFile :: Read](#read)|Lit (sans mise en mémoire tampon) des données à partir d’un fichier à la position de fichier actuelle.|
|[CFile :: Remove](#remove)|Supprime le fichier spécifié (fonction statique).|
|[CFile :: Rename](#rename)|Renomme le fichier spécifié (fonction statique).|
|[CFile :: Seek](#seek)|Positionne le pointeur de fichier actuel.|
|[CFile :: SeekToBegin](#seektobegin)|Positionne le pointeur de fichier actuel au début du fichier.|
|[CFile :: SeekToEnd](#seektoend)|Positionne le pointeur de fichier actuel à la fin du fichier.|
|[CFile :: SetFilePath](#setfilepath)|Définit le chemin d’accès complet du fichier sélectionné.|
|[CFile :: SetLength](#setlength)|Modifie la longueur du fichier.|
|[CFile :: SetStatus](#setstatus)|Définit l’état du fichier spécifié (fonction virtuelle statique).|
|[CFile :: UnlockRange](#unlockrange)|Déverrouille une plage d’octets dans un fichier.|
|[CFile :: Write](#write)|Écrit (sans mise en mémoire tampon) des données dans un fichier à la position de fichier actuelle.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[HANDLE CFile :: Operator](#operator_handle)|Handle d’un objet `CFile`.|

### <a name="public-data-members"></a>Membres de données publiques

|Name|Description|
|----------|-----------------|
|[CFile :: hFileNull](#hfilenull)|Détermine si l’objet `CFile` a un handle valide.|
|[CFile :: m_hFile](#m_hfile)|Contient généralement le descripteur de fichier du système d’exploitation.|

### <a name="protected-data-members"></a>Membres de données protégées

|Name|Description|
|----------|-----------------|
|[CFile :: m_pTM](#m_ptm)|Pointeur vers `CAtlTransactionManager` objet.|

## <a name="remarks"></a>Notes

Il fournit directement des services d’entrée/sortie de disque binaires non mis en mémoire tampon, et il prend indirectement en charge les fichiers texte et les fichiers de mémoire par le biais de ses classes dérivées. `CFile` fonctionne conjointement avec la classe `CArchive` pour prendre en charge la sérialisation d’objets Microsoft Foundation Class.

La relation hiérarchique entre cette classe et ses classes dérivées permet à votre programme de fonctionner sur tous les objets de fichier par le biais de l’interface de `CFile` polymorphe. Un fichier de mémoire, par exemple, se comporte comme un fichier sur disque.

Utilisez `CFile` et ses classes dérivées pour les e/s de disque à usage général. Utilisez `ofstream` ou d’autres classes de `iostream` Microsoft pour le texte mis en forme envoyé à un fichier sur disque.

Normalement, un fichier disque est ouvert automatiquement sur `CFile` construction et fermé lors de la destruction. Les fonctions membres statiques vous permettent d’interroger l’état d’un fichier sans ouvrir le fichier.

Pour plus d’informations sur l’utilisation de `CFile`, consultez les articles [fichiers dans MFC](../../mfc/files-in-mfc.md) et [gestion des fichiers](../../c-runtime-library/file-handling.md) dans la référence de la *bibliothèque Runtime*.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="abort"></a>CFile :: Abort

Ferme le fichier associé à cet objet et rend le fichier indisponible pour la lecture ou l’écriture.

```
virtual void Abort();
```

### <a name="remarks"></a>Notes

Si vous n’avez pas fermé le fichier avant de détruire l’objet, le destructeur le ferme pour vous.

Lors de la gestion des exceptions, `CFile::Abort` diffère de `CFile::Close` de deux façons importantes. Tout d’abord, la fonction `Abort` ne lève pas d’exception en cas d’échec, car les échecs sont ignorés par `Abort`. Deuxièmement, `Abort` n' **affirmera** pas si le fichier n’a pas été ouvert ou a été fermé précédemment.

Si vous avez utilisé **New** pour allouer l’objet `CFile` sur le tas, vous devez le supprimer après avoir fermé le fichier. `Abort` définit `m_hFile` sur `CFile::hFileNull`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

##  <a name="cfile"></a>CFile :: CFile

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

*hFile*<br/>
Handle d'un fichier à attacher à l'objet `CFile`.

*lpszFileName*<br/>
Chemin d'accès relatif ou complet d'un fichier à attacher à l'objet `CFile`.

*nOpenFlags*<br/>
Combinaison de bits (OR) ou options d'accès au fichier pour le fichier spécifié. Consultez la section Notes pour connaître les options possibles.

*pTM*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="remarks"></a>Notes

Les cinq tableaux suivants répertorient les options possibles pour le paramètre *nOpenFlags* .

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
|`CFile::typeText`|Définit le mode texte avec un traitement spécial pour les paires retour chariot-saut de ligne (utilisé dans les classes dérivées uniquement).|
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
|`CFile::modeCreate`|Crée un nouveau fichier si aucun fichier n’existe. Si le fichier existe déjà, il est remplacé et sa longueur initiale est égale à zéro.|
|`CFile::modeNoTruncate`|Crée un fichier s’il n’existe pas de fichier ; Sinon, si le fichier existe déjà, il est attaché à l’objet `CFile`.|

Choisissez les options de mise en cache de fichiers suivantes d'après leur description. Par défaut, le système utilise un schéma de mise en cache à usage général qui n’est pas disponible en tant qu’option.

|Valeur|Description|
|-----------|-----------------|
|`CFile::osNoBuffer`|Le système n’utilise pas de cache intermédiaire pour le fichier. Cette option annule les deux options suivantes.|
|`CFile::osRandomAccess`|Le cache de fichiers est optimisé pour l'accès aléatoire. N’utilisez pas cette option et l’option d’analyse séquentielle.|
|`CFile::osSequentialScan`|Le cache de fichiers est optimisé pour l'accès séquentiel. N’utilisez pas cette option et l’option d’accès aléatoire.|
|`CFile::osWriteThrough`|Les opérations d’écriture sont effectuées sans délai.|

Choisissez l'option de sécurité suivante pour empêcher l'héritage du handle de fichier. Par défaut, tous les nouveaux processus enfants peuvent utiliser le handle de fichier.

|Valeur|Description|
|-----------|-----------------|
|`CFile::modeNoInherit`|Empêche les processus enfants d'utiliser le handle de fichier.|

Le constructeur par défaut initialise des membres, mais n’attache pas de fichier à l’objet `CFile`. Après l’utilisation de ce constructeur, utilisez la méthode [CFile :: Open](#open) pour ouvrir un fichier et l’attacher à l’objet `CFile`.

Le constructeur avec un seul paramètre initialise les membres et attache un fichier existant à l'objet `CFile`.

Le constructeur avec deux paramètres initialise les membres et tente d'ouvrir le fichier spécifié. Si ce constructeur ouvre correctement le fichier spécifié, le fichier est attaché à l'objet `CFile`. Sinon, ce constructeur émet un pointeur vers un objet `CInvalidArgException`. Pour plus d’informations sur la gestion des exceptions, consultez [exceptions](../../mfc/exception-handling-in-mfc.md).

Si un objet `CFile` ouvre correctement un fichier spécifié, il ferme automatiquement ce fichier lors de la destruction de l’objet `CFile`. dans le cas contraire, vous devez fermer explicitement le fichier une fois qu’il n’est plus attaché à l’objet `CFile`.

### <a name="example"></a>Exemple

Le code suivant illustre l'utilisation de `CFile`.

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

##  <a name="close"></a>CFile :: Close

Ferme le fichier associé à cet objet et rend le fichier indisponible pour la lecture ou l’écriture.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Si vous n’avez pas fermé le fichier avant de détruire l’objet, le destructeur le ferme pour vous.

Si vous avez utilisé **New** pour allouer l’objet `CFile` sur le tas, vous devez le supprimer après avoir fermé le fichier. `Close` définit `m_hFile` sur `CFile::hFileNull`.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CFile :: CFile](#cfile).

##  <a name="duplicate"></a>CFile ::D quée

Construit un objet `CFile` dupliqué pour un fichier donné.

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CFile` dupliqué.

### <a name="remarks"></a>Notes

Cette fonction est équivalente à la fonction Runtime C `_dup`.

##  <a name="flush"></a>CFile :: Flush

Force l’écriture dans le fichier des données restantes dans le tampon de fichier.

```
virtual void Flush();
```

### <a name="remarks"></a>Notes

L’utilisation de `Flush` ne garantit pas le vidage des tampons de `CArchive`. Si vous utilisez une archive, appelez [CArchive :: Flush](../../mfc/reference/carchive-class.md#flush) en premier.

### <a name="example"></a>Exemple

Consultez l’exemple pour [CFile :: SetFilePath](#setfilepath).

##  <a name="getfilename"></a>CFile :: GetFileName

Appelez cette fonction membre pour récupérer le nom d’un fichier spécifié.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Valeur de retour

Nom du fichier.

### <a name="remarks"></a>Notes

Par exemple, lorsque vous appelez `GetFileName` pour générer un message à l’utilisateur sur le fichier `c:\windows\write\myfile.wri`, le nom de fichier, `myfile.wri`, est retourné.

Pour retourner le chemin d’accès complet au fichier, y compris le nom, appelez [GetFilePath](#getfilepath). Pour retourner le titre du fichier (`myfile`), appelez [GetFileTitle](#getfiletitle).

### <a name="example"></a>Exemple

Ce fragment de code ouvre le système. Fichier INI dans votre répertoire WINDOWS. S’il est trouvé, l’exemple affiche le nom et le chemin d’accès et le titre, comme le montre la sortie :

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

##  <a name="getfilepath"></a>CFile :: GetFilePath

Appelez cette fonction membre pour récupérer le chemin d’accès complet d’un fichier spécifié.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Valeur de retour

Chemin d’accès complet du fichier spécifié.

### <a name="remarks"></a>Notes

Par exemple, lorsque vous appelez `GetFilePath` pour générer un message à l’utilisateur sur le fichier `c:\windows\write\myfile.wri`, le chemin d’accès du fichier, `c:\windows\write\myfile.wri`, est retourné.

Pour retourner uniquement le nom du fichier (`myfile.wri`), appelez [GetFileName](#getfilename). Pour retourner le titre du fichier (`myfile`), appelez [GetFileTitle](#getfiletitle).

### <a name="example"></a>Exemple

Consultez l’exemple pour [GetFileName](#getfilename).

##  <a name="getfiletitle"></a>CFile :: GetFileTitle

Appelez cette fonction membre pour récupérer le titre du fichier (nom complet) du fichier.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Valeur de retour

Titre du fichier sous-jacent.

### <a name="remarks"></a>Notes

Cette méthode appelle [GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew) pour récupérer le titre du fichier. En cas de réussite, la méthode retourne la chaîne que le système utiliserait pour afficher le nom de fichier à l’utilisateur. Sinon, la méthode appelle [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) pour récupérer le nom de fichier (y compris l’extension de fichier) du fichier sous-jacent. Cela signifie que l’extension de fichier n’est pas toujours incluse dans la chaîne de titre du fichier retourné. Pour plus d’informations, consultez [GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew) et [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) dans la SDK Windows.

Pour retourner le chemin d’accès complet au fichier, y compris le nom, appelez [GetFilePath](#getfilepath). Pour retourner uniquement le nom du fichier, appelez [GetFileName](#getfilename).

### <a name="example"></a>Exemple

Consultez l’exemple pour [GetFileName](#getfilename).

##  <a name="getlength"></a>CFile :: GetLength

Obtient la longueur logique actuelle du fichier, en octets.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Valeur de retour

Longueur du fichier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

##  <a name="getposition"></a>CFile :: GetPosition

Obtient la valeur actuelle du pointeur de fichier qui peut être utilisé dans les appels ultérieurs à `Seek`.

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur de fichier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

##  <a name="getstatus"></a>CFile :: GetStatus

Cette méthode récupère les informations d’État relatives à une instance d’objet `CFile` donnée ou à un chemin d’accès de fichier donné.

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Paramètres

*rStatus*<br/>
Référence à une structure `CFileStatus` fournie par l’utilisateur qui recevra les informations d’État. La structure `CFileStatus` contient les champs suivants :

- `CTime m_ctime` la date et l’heure de création du fichier.

- `CTime m_mtime` la date et l’heure de la dernière modification du fichier.

- `CTime m_atime` la date et l’heure du dernier accès au fichier pour la lecture.

- `ULONGLONG m_size` la taille logique du fichier en octets, comme indiqué par la commande DIR.

- `BYTE m_attribute` l’octet d’attribut du fichier.

- `char m_szFullName[_MAX_PATH]` le nom de fichier absolu dans le jeu de caractères Windows.

*lpszFileName*<br/>
Chaîne dans le jeu de caractères Windows qui correspond au chemin d’accès au fichier souhaité. Le chemin d’accès peut être relatif ou absolu, ou peut contenir un nom de chemin d’accès réseau.

*pTM*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="return-value"></a>Valeur de retour

TRUE si les informations d’État du fichier spécifié sont obtenues avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

La version non statique de `GetStatus` récupère les informations d’État du fichier ouvert associé à l’objet `CFile` donné.  La version statique de `GetStatus` obtient l’état du fichier à partir d’un chemin d’accès de fichier donné sans réellement ouvrir le fichier. Cette version est utile pour tester l’existence et les droits d’accès d’un fichier.

Le membre `m_attribute` de la structure `CFileStatus` fait référence à l’ensemble d’attributs de fichier. La classe `CFile` fournit le type d’énumération d' **attribut** , ce qui permet de spécifier des attributs de fichier symboliquement :

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

##  <a name="hfilenull"></a>CFile :: hFileNull

Détermine la présence d’un handle de fichier valide pour l’objet `CFile`.

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>Notes

Cette constante est utilisée pour déterminer si l’objet `CFile` a un handle de fichier valide.

L’exemple suivant illustre cette opération :

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

##  <a name="lockrange"></a>CFile :: LockRange

Verrouille une plage d’octets dans un fichier ouvert, en levant une exception si le fichier est déjà verrouillé.

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Paramètres

*dwPos*<br/>
Offset d’octet du début de la plage d’octets à verrouiller.

*dwCount*<br/>
Nombre d’octets dans la plage à verrouiller.

### <a name="remarks"></a>Notes

Le verrouillage d’octets dans un fichier empêche l’accès à ces octets par d’autres processus. Vous pouvez verrouiller plusieurs régions d’un fichier, mais aucune région se chevauchant n’est autorisée.

Lorsque vous déverrouillez la région à l’aide de la fonction membre `UnlockRange`, la plage d’octets doit correspondre exactement à la région précédemment verrouillée. La fonction `LockRange` ne fusionne pas les zones adjacentes. Si deux régions verrouillées sont adjacentes, vous devez déverrouiller chaque région séparément.

> [!NOTE]
>  Cette fonction n’est pas disponible pour la classe dérivée de `CMemFile`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="m_hfile"></a>CFile :: m_hFile

Contient le descripteur de fichier du système d’exploitation pour un fichier ouvert.

```
HANDLE m_hFile;
```

### <a name="remarks"></a>Notes

`m_hFile` est une variable publique de type UINT. Il contient `CFile::hFileNull`, un indicateur de fichier vide indépendant du système d’exploitation, si le handle n’a pas été assigné.

L’utilisation de `m_hFile` n’est pas recommandée, car la signification du membre dépend de la classe dérivée. `m_hFile` est un membre public pour faciliter la prise en charge de l’utilisation des non polymorphes de la classe.

##  <a name="m_ptm"></a>CFile :: m_pTM

Pointeur vers un objet `CAtlTransactionManager`.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Notes

##  <a name="open"></a>CFile :: Open

Surchargé. `Open` est conçu pour être utilisé avec le constructeur de `CFile` par défaut.

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

*lpszFileName*<br/>
Chaîne qui contient le chemin d’accès au fichier souhaité. Le chemin d’accès peut être relatif, absolu ou un nom de réseau (UNC).

*nOpenFlags*<br/>
UINT qui définit le mode de partage et d’accès du fichier. Elle spécifie l’action à exécuter lors de l’ouverture du fichier. Vous pouvez combiner des options à l’aide de l’opérateur **&#124;** de bits or (). Une autorisation d’accès et une option de partage sont requises. les modes `modeCreate` et `modeNoInherit` sont facultatifs. Consultez le constructeur [CFile](#cfile) pour obtenir la liste des options de mode.

*pError*<br/>
Pointeur vers un objet d’exception de fichier existant qui recevra l’état d’une opération ayant échoué.

*pTM*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’ouverture a réussi ; Sinon, 0. Le paramètre *perror* est significatif uniquement si la valeur 0 est retournée.

### <a name="remarks"></a>Notes

Les deux fonctions `Open` sont des méthodes « sûres » pour l’ouverture d’un fichier, où une défaillance est une condition normale et attendue.

Tandis que le constructeur `CFile` lève une exception dans une condition d’erreur, `Open` retourne la valeur FALSe pour les conditions d’erreur. Toutefois, `Open` peut toujours initialiser un objet [CFileException](../../mfc/reference/cfileexception-class.md) pour décrire l’erreur. Si vous ne fournissez pas le paramètre *perror* , ou si vous transmettez la valeur null pour *perror*, `Open` retourne la valeur false et ne lève pas d' `CFileException`. Si vous transmettez un pointeur à un `CFileException`existant et que `Open` rencontre une erreur, la fonction le remplit avec les informations qui décrivent cette erreur. `Open` ne lève pas d’exception dans les deux cas.

Le tableau suivant décrit les résultats possibles de `Open`.

|`pError`|Erreur rencontrée|Valeur retournée|Contenu CFileException|
|--------------|------------------------|------------------|----------------------------|
|NULL|Non|TRUE|n/a|
|PTR pour `CFileException`|Non|TRUE|inchangé|
|NULL|Oui|FALSE|n/a|
|PTR pour `CFileException`|Oui|FALSE|initialisé pour décrire l’erreur|

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

##  <a name="operator_handle"></a>HANDLE CFile :: Operator

Utilisez cet opérateur pour passer un handle à un objet `CFile` à des fonctions telles que [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) et [GetFileTime](/windows/win32/api/fileapi/nf-fileapi-getfiletime) qui attendent une `HANDLE`.

```
operator HANDLE() const;
```

##  <a name="read"></a>CFile :: Read

Lit les données dans une mémoire tampon à partir du fichier associé à l’objet `CFile`.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Pointeur vers la mémoire tampon fournie par l’utilisateur qui doit recevoir les données lues à partir du fichier.

*nCount*<br/>
Nombre maximal d’octets à lire à partir du fichier. Pour les fichiers en mode texte, les paires retour chariot-saut de ligne sont comptées comme des caractères simples.

### <a name="return-value"></a>Valeur de retour

Nombre d'octets transférés dans la mémoire tampon. Pour toutes les classes `CFile`, la valeur de retour peut être inférieure à *nCount* si la fin du fichier a été atteinte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

Pour un autre exemple, consultez [CFile :: Open](#open).

##  <a name="remove"></a>CFile :: Remove

Cette fonction statique supprime le fichier spécifié par le chemin d’accès.

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszFileName*<br/>
Chaîne qui correspond au chemin d’accès au fichier souhaité. Le chemin d’accès peut être relatif ou absolu et peut contenir un nom de réseau.

*pTM*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="remarks"></a>Notes

`Remove` ne supprime pas un répertoire.

La fonction membre `Remove` lève une exception si le fichier connecté est ouvert ou si le fichier ne peut pas être supprimé. Cette fonction est équivalente à la commande DEL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

##  <a name="rename"></a>CFile :: Rename

Cette fonction statique renomme le fichier spécifié.

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszOldName*<br/>
Ancien chemin d’accès.

*lpszNewName*<br/>
Nouveau chemin d’accès.

*pTM*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="remarks"></a>Notes

Les répertoires ne peuvent pas être renommés. Cette fonction est équivalente à la commande REN.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

##  <a name="seek"></a>CFile :: Seek

Repositionne le pointeur de fichier dans un fichier ouvert.

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>Paramètres

*lOff*<br/>
Nombre d’octets pour déplacer le pointeur de fichier. Les valeurs positives déplacent le pointeur de fichier vers la fin du fichier ; les valeurs négatives déplacent le pointeur de fichier vers le début du fichier.

*Ndepuis*<br/>
Position à partir de laquelle effectuer la recherche. Consultez la section Notes pour connaître les valeurs possibles.

### <a name="return-value"></a>Valeur de retour

Position du pointeur de fichier si la méthode a réussi ; Sinon, la valeur de retour n’est pas définie et un pointeur vers une exception `CFileException` est levée.

### <a name="remarks"></a>Notes

Le tableau suivant répertorie les valeurs possibles pour le paramètre *ndepuis* .

|Valeur|Description|
|-----------|-----------------|
|`CFile::begin`|Recherche à partir du début du fichier.|
|`CFile::current`|Recherche à partir de l’emplacement actuel du pointeur de fichier.|
|`CFile::end`|Recherche à partir de la fin du fichier.|

Lorsqu’un fichier est ouvert, le pointeur de fichier est positionné sur 0, le début du fichier.

Vous pouvez définir le pointeur de fichier sur une position au-delà de la fin d’un fichier. Dans ce cas, la taille du fichier n’augmente pas tant que vous n’avez pas écrit dans le fichier.

Le gestionnaire d’exceptions pour cette méthode doit supprimer l’objet exception après le traitement de l’exception.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

##  <a name="seektobegin"></a>CFile :: SeekToBegin

Définit la valeur du pointeur de fichier au début du fichier.

```
void SeekToBegin();
```

### <a name="remarks"></a>Notes

`SeekToBegin()` équivaut à `Seek( 0L, CFile::begin )`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="seektoend"></a>CFile :: SeekToEnd

Définit la valeur du pointeur de fichier à la fin logique du fichier.

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>Valeur de retour

Longueur du fichier en octets.

### <a name="remarks"></a>Notes

`SeekToEnd()` équivaut à `CFile::Seek( 0L, CFile::end )`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="setfilepath"></a>CFile :: SetFilePath

Appelez cette fonction pour spécifier le chemin d’accès du fichier. Par exemple, si le chemin d’accès d’un fichier n’est pas disponible lors de la construction d’un objet [CFile](../../mfc/reference/cfile-class.md) , appelez `SetFilePath` pour le fournir.

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Paramètres

*lpszNewName*<br/>
Pointeur vers une chaîne spécifiant le nouveau chemin d’accès.

### <a name="remarks"></a>Notes

> [!NOTE]
> `SetFilePath` n’ouvre pas le fichier ou ne crée pas le fichier ; Il associe simplement l’objet `CFile` à un nom de chemin d’accès, qui peut ensuite être utilisé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

##  <a name="setlength"></a>CFile :: SetLength

Appelez cette fonction pour modifier la longueur du fichier.

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>Paramètres

*dwNewLen*<br/>
Longueur souhaitée du fichier en octets. Cette valeur peut être supérieure ou inférieure à la longueur actuelle du fichier. Le fichier sera étendu ou tronqué, selon le cas.

### <a name="remarks"></a>Notes

> [!NOTE]
>  Avec `CMemFile`, cette fonction peut lever un objet `CMemoryException`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

##  <a name="setstatus"></a>CFile :: SetStatus

Définit l’état du fichier associé à cet emplacement de fichier.

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszFileName*<br/>
Chaîne qui correspond au chemin d’accès au fichier souhaité. Le chemin d’accès peut être relatif ou absolu et peut contenir un nom de réseau.

*statut*<br/>
Mémoire tampon qui contient les nouvelles informations d’État. Appelez la fonction membre `GetStatus` pour préremplir la structure `CFileStatus` avec les valeurs actuelles, puis apportez les modifications nécessaires. Si une valeur est égale à 0, l’élément d’état correspondant n’est pas mis à jour. Pour obtenir une description de la structure `CFileStatus`, consultez la fonction membre [GetStatus](#getstatus) .

*pTM*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="remarks"></a>Notes

Pour définir l’heure, modifiez le champ `m_mtime` de l' *État*.

Lorsque vous effectuez un appel à `SetStatus` dans une tentative de modifier uniquement les attributs du fichier, et que le `m_mtime` membre de la structure d’état de fichier est différent de zéro, les attributs peuvent également être affectés (la modification de l’horodatage peut avoir des effets secondaires sur les attributs). Si vous souhaitez modifier uniquement les attributs du fichier, définissez d’abord le `m_mtime` membre de la structure d’état de fichier sur zéro, puis effectuez un appel à `SetStatus`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

##  <a name="unlockrange"></a>CFile :: UnlockRange

Déverrouille une plage d’octets dans un fichier ouvert.

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Paramètres

*dwPos*<br/>
Offset d’octet du début de la plage d’octets à déverrouiller.

*dwCount*<br/>
Nombre d’octets dans la plage à déverrouiller.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez la description de la fonction membre [LockRange](#lockrange) .

> [!NOTE]
>  Cette fonction n’est pas disponible pour la classe dérivée de `CMemFile`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="write"></a>CFile :: Write

Écrit des données à partir d’une mémoire tampon dans le fichier associé à l’objet `CFile`.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Pointeur vers la mémoire tampon fournie par l’utilisateur qui contient les données à écrire dans le fichier.

*nCount*<br/>
Nombre d’octets à transférer à partir de la mémoire tampon. Pour les fichiers en mode texte, les paires retour chariot-saut de ligne sont comptées comme des caractères simples.

### <a name="remarks"></a>Notes

`Write` lève une exception en réponse à plusieurs conditions, y compris la condition Disk-Full.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

Consultez également les exemples pour [CFile :: CFile](#cfile) et [CFile :: Open](#open).

## <a name="see-also"></a>Voir aussi

[Exemple MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CStdioFile, classe](../../mfc/reference/cstdiofile-class.md)<br/>
[CMemFile, classe](../../mfc/reference/cmemfile-class.md)
