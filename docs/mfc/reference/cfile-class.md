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
ms.openlocfilehash: 53afaf7732811e25729944eb71130a88e4f17a87
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755001"
---
# <a name="cfile-class"></a>CFile, classe

Classe de base pour les classes de fichier Microsoft Foundation Class.

## <a name="syntax"></a>Syntaxe

```
class CFile : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFile::CFile](#cfile)|Construit un `CFile` objet à partir d’un chemin ou d’une poignée de fichier.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFile::Abort](#abort)|Ferme un fichier ignorant tous les avertissements et erreurs.|
|[CFile::Fermer](#close)|Ferme un fichier et supprime l’objet.|
|[CFile::Duplicate](#duplicate)|Construit un objet en double basé sur ce fichier.|
|[CFile::Flush](#flush)|Flushes toutes les données encore à écrire.|
|[CFile::GetFileName](#getfilename)|Récupère le nom de fichier du fichier sélectionné.|
|[CFile::GetFilePath](#getfilepath)|Récupère le chemin complet du fichier sélectionné.|
|[CFile::GetFileTitle](#getfiletitle)|Récupère le titre du fichier sélectionné.|
|[CFile::GetLength](#getlength)|Récupère la longueur du fichier.|
|[CFile::GetPosition](#getposition)|Récupère le pointeur de fichier actuel.|
|[CFile::GetStatus](#getstatus)|Récupère l’état du fichier ouvert, ou dans la version statique, récupère l’état du fichier spécifié (fonction statique et virtuelle).|
|[CFile::LockRange](#lockrange)|Verrouille une gamme d’octets dans un fichier.|
|[CFile::Ouvert](#open)|Ouvre en toute sécurité un fichier avec une option de test d’erreur.|
|[CFile::Lire](#read)|Lit les données (inbuffered) d’un fichier à la position de fichier actuelle.|
|[CFile::Supprimer](#remove)|Supprime le fichier spécifié (fonction statique).|
|[CFile::Rename](#rename)|Renomme le fichier spécifié (fonction statique).|
|[CFile::Chercher](#seek)|Positionne le pointeur de fichier actuel.|
|[CFile::SeekToBegin](#seektobegin)|Positionne le pointeur de fichier actuel au début du fichier.|
|[CFile::SeekToEnd](#seektoend)|Positionne le pointeur de fichier actuel à la fin du fichier.|
|[CFile::SetFilePath](#setfilepath)|Définit le chemin complet du fichier sélectionné.|
|[CFile::SetLength](#setlength)|Modifications de la longueur du fichier.|
|[CFile::SetStatus](#setstatus)|Définit l’état du fichier spécifié (fonction statique et virtuelle).|
|[CFile::UnlockRange](#unlockrange)|Débloque une gamme d’octets dans un fichier.|
|[CFile::Ecrire](#write)|Écrit des données (inbuffered) dans un fichier à la position de fichier actuelle.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CFile::opérateur HANDLE](#operator_handle)|Une poignée `CFile` à un objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CFile::hFileNull](#hfilenull)|Détermine si `CFile` l’objet a une poignée valide.|
|[CFile::m_hFile](#m_hfile)|Contient habituellement la poignée de fichier système d’exploitation.|

### <a name="protected-data-members"></a>Membres de données protégés

|Nom|Description|
|----------|-----------------|
|[CFile::m_pTM](#m_ptm)|Pointeur `CAtlTransactionManager` à objecter.|

## <a name="remarks"></a>Notes

Il fournit directement des services inbuffered, d’entrée/sortie de disque binaire, et il prend indirectement en charge les fichiers texte et les fichiers mémoire à travers ses classes dérivées. `CFile`travaille en collaboration `CArchive` avec la classe pour soutenir la sérialisation des objets microsoft Foundation Class.

La relation hiérarchique entre cette classe et ses classes dérivées permet `CFile` à votre programme d’opérer sur tous les objets de fichiers à travers l’interface polymorphe. Un fichier mémoire, par exemple, se comporte comme un fichier disque.

Utilisation `CFile` et ses classes dérivées pour le disque à usage général I/O. Utilisez `ofstream` ou `iostream` d’autres classes Microsoft pour le texte formaté envoyé à un fichier disque.

Normalement, un fichier de disque `CFile` est ouvert automatiquement sur la construction et fermé sur la destruction. Les fonctions statiques des membres vous permettent d’interroger l’état d’un fichier sans ouvrir le fichier.

Pour `CFile`plus d’informations sur l’utilisation , voir les articles Fichiers dans [MFC](../../mfc/files-in-mfc.md) et Traitement des [fichiers](../../c-runtime-library/file-handling.md) dans la référence de bibliothèque *Run-Time*.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="cfileabort"></a><a name="abort"></a>CFile::Abort

Ferme le fichier associé à cet objet et rend le fichier indisponible pour la lecture ou l’écriture.

```
virtual void Abort();
```

### <a name="remarks"></a>Notes

Si vous n’avez pas fermé le fichier avant de détruire l’objet, le destructeur le ferme pour vous.

Lors de `CFile::Abort` la manipulation `CFile::Close` des exceptions, diffère de deux façons importantes. Tout d’abord, la `Abort` fonction ne jettera pas une `Abort`exception sur les échecs, parce que les échecs sont ignorés par . Deuxièmement, `Abort` n’affirmera **ASSERT** pas si le fichier n’a pas été ouvert, ou a été fermé précédemment.

Si vous **new** avez utilisé `CFile` nouveau pour allouer l’objet sur le tas, alors vous devez le supprimer après la fermeture du fichier. `Abort``m_hFile` ensembles `CFile::hFileNull`à .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

## <a name="cfilecfile"></a><a name="cfile"></a>CFile::CFile

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

*hFile (en)*<br/>
Handle d'un fichier à attacher à l'objet `CFile`.

*lpszFileName*<br/>
Chemin d'accès relatif ou complet d'un fichier à attacher à l'objet `CFile`.

*nOpenFlags*<br/>
Combinaison de bits (OR) ou options d'accès au fichier pour le fichier spécifié. Consultez la section Notes pour connaître les options possibles.

*Ptm*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="remarks"></a>Notes

Les cinq tableaux suivants répertorient les options possibles pour le *paramètre nOpenFlags.*

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
|`CFile::typeText`|Définit le mode texte avec un traitement spécial pour les paires d’alimentation de retour de chariot (utilisées uniquement dans les classes dérivées).|
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
|`CFile::modeCreate`|Crée un nouveau fichier si aucun fichier n’existe. Si le fichier existe déjà, il est écrasé et initialement réglé à zéro longueur.|
|`CFile::modeNoTruncate`|Crée un nouveau fichier si aucun fichier n’existe; sinon, si le fichier existe déjà, il `CFile` est attaché à l’objet.|

Choisissez les options de mise en cache de fichiers suivantes d'après leur description. Par défaut, le système utilise un système de mise en cache à usage général qui n’est pas disponible en option.

|Valeur|Description|
|-----------|-----------------|
|`CFile::osNoBuffer`|Le système n’utilise pas de cache intermédiaire pour le fichier. Cette option annule les deux options suivantes.|
|`CFile::osRandomAccess`|Le cache de fichiers est optimisé pour l'accès aléatoire. N’utilisez pas cette option et l’option d’analyse séquentielle.|
|`CFile::osSequentialScan`|Le cache de fichiers est optimisé pour l'accès séquentiel. N’utilisez pas cette option et l’option d’accès aléatoire.|
|`CFile::osWriteThrough`|Les opérations d’écriture se font sans délai.|

Choisissez l'option de sécurité suivante pour empêcher l'héritage du handle de fichier. Par défaut, tous les nouveaux processus enfants peuvent utiliser le handle de fichier.

|Valeur|Description|
|-----------|-----------------|
|`CFile::modeNoInherit`|Empêche les processus enfants d'utiliser le handle de fichier.|

Le constructeur par défaut initialise les membres mais `CFile` n’attache pas de fichier à l’objet. Après avoir utilisé ce constructeur, utilisez la méthode [CFile::Open](#open) `CFile` pour ouvrir un fichier et l’attacher à l’objet.

Le constructeur avec un seul paramètre initialise les membres et attache un fichier existant à l'objet `CFile`.

Le constructeur avec deux paramètres initialise les membres et tente d'ouvrir le fichier spécifié. Si ce constructeur ouvre correctement le fichier spécifié, le fichier est attaché à l'objet `CFile`. Sinon, ce constructeur émet un pointeur vers un objet `CInvalidArgException`. Pour plus d’informations sur la façon de gérer les exceptions, voir [Exceptions](../../mfc/exception-handling-in-mfc.md).

Si `CFile` un objet ouvre avec succès un fichier spécifié, il fermera automatiquement ce fichier lorsque l’objet `CFile` est détruit ; sinon, vous devez fermer explicitement le fichier après `CFile` qu’il ne soit plus attaché à l’objet.

### <a name="example"></a>Exemple

Le code suivant illustre l'utilisation de `CFile`.

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

## <a name="cfileclose"></a><a name="close"></a>CFile::Fermer

Ferme le fichier associé à cet objet et rend le fichier indisponible pour la lecture ou l’écriture.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Si vous n’avez pas fermé le fichier avant de détruire l’objet, le destructeur le ferme pour vous.

Si vous **new** avez utilisé `CFile` nouveau pour allouer l’objet sur le tas, alors vous devez le supprimer après la fermeture du fichier. `Close``m_hFile` ensembles `CFile::hFileNull`à .

### <a name="example"></a>Exemple

Voir l’exemple pour [CFile::CFile](#cfile).

## <a name="cfileduplicate"></a><a name="duplicate"></a>CFile::Duplicate

Construit un `CFile` objet en double pour un fichier donné.

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur `CFile` à un objet en double.

### <a name="remarks"></a>Notes

Cette fonction est équivalente à `_dup`la fonction C run-time .

## <a name="cfileflush"></a><a name="flush"></a>CFile::Flush

Force toute donnée restante dans le mémoire tampon à être écrite au fichier.

```
virtual void Flush();
```

### <a name="remarks"></a>Notes

L’utilisation `Flush` de ne garantit `CArchive` pas le rinçage des tampons. Si vous utilisez une archive, appelez [CArchive::Flush](../../mfc/reference/carchive-class.md#flush) d’abord.

### <a name="example"></a>Exemple

Voir l’exemple pour [CFile:SetFilePath](#setfilepath).

## <a name="cfilegetfilename"></a><a name="getfilename"></a>CFile::GetFileName

Appelez cette fonction de membre pour récupérer le nom d’un fichier spécifié.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Valeur de retour

Nom du fichier.

### <a name="remarks"></a>Notes

Par exemple, lorsque `GetFileName` vous appelez pour générer un `c:\windows\write\myfile.wri`message à l’utilisateur sur le fichier , le nom de fichier, `myfile.wri`, est retourné.

Pour retourner tout le chemin du fichier, y compris le nom, appelez [GetFilePath](#getfilepath). Pour retourner le titre `myfile`du fichier ( ), appelez [GetFileTitle](#getfiletitle).

### <a name="example"></a>Exemple

Ce fragment de code ouvre le SYSTEM. Fichier INI dans votre répertoire WINDOWS. S’il est trouvé, l’exemple imprimera le nom, le chemin et le titre, comme le montre La sortie :

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

## <a name="cfilegetfilepath"></a><a name="getfilepath"></a>CFile::GetFilePath

Appelez cette fonction de membre pour récupérer le chemin complet d’un fichier spécifié.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Valeur de retour

Le chemin complet du fichier spécifié.

### <a name="remarks"></a>Notes

Par exemple, lorsque `GetFilePath` vous appelez pour générer un `c:\windows\write\myfile.wri`message à `c:\windows\write\myfile.wri`l’utilisateur sur le fichier , le chemin de fichier, , est retourné.

Pour revenir juste le nom`myfile.wri`du fichier ( ), appelez [GetFileName](#getfilename). Pour retourner le titre`myfile`du fichier ( ), appelez [GetFileTitle](#getfiletitle).

### <a name="example"></a>Exemple

Voir l’exemple pour [GetFileName](#getfilename).

## <a name="cfilegetfiletitle"></a><a name="getfiletitle"></a>CFile::GetFileTitle

Appelez cette fonction de membre pour récupérer le titre du fichier (le nom d’affichage) pour le fichier.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Valeur de retour

Le titre du fichier sous-jacent.

### <a name="remarks"></a>Notes

Cette méthode appelle [GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew) pour récupérer le titre du fichier. En cas de succès, la méthode renvoie la chaîne que le système utiliserait pour afficher le nom du fichier à l’utilisateur. Dans le cas contraire, la méthode appelle [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) pour récupérer le nom du fichier (y compris l’extension du fichier) du fichier sous-jacent. Cela signifie que l’extension du fichier n’est pas toujours incluse dans la chaîne de titre de fichier retourné. Pour plus d’informations, voir [GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew) et [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) dans le Windows SDK.

Pour retourner tout le chemin du fichier, y compris le nom, appelez [GetFilePath](#getfilepath). Pour retourner juste le nom du fichier, appelez [GetFileName](#getfilename).

### <a name="example"></a>Exemple

Voir l’exemple pour [GetFileName](#getfilename).

## <a name="cfilegetlength"></a><a name="getlength"></a>CFile::GetLength

Obtient la longueur logique actuelle du fichier dans les octets.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Valeur de retour

La longueur du fichier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

## <a name="cfilegetposition"></a><a name="getposition"></a>CFile::GetPosition

Obtient la valeur actuelle du pointeur de fichier, `Seek`qui peut être utilisé dans les appels ultérieurs à .

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>Valeur de retour

Le pointeur de fichier.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

## <a name="cfilegetstatus"></a><a name="getstatus"></a>CFile::GetStatus

Cette méthode récupère les informations `CFile` d’état relatives à une instance d’objet donnée ou à un chemin de fichier donné.

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Paramètres

*rStatus*<br/>
Une référence à une `CFileStatus` structure fournie par l’utilisateur qui recevra les informations d’état. La `CFileStatus` structure a les champs suivants:

- `CTime m_ctime`La date et l’heure de la création du fichier.

- `CTime m_mtime`La date et l’heure du fichier ont été modifiées pour la dernière fois.

- `CTime m_atime`La date et l’heure à laquelle le dossier a été consulté pour la dernière fois pour la lecture.

- `ULONGLONG m_size`La taille logique du fichier dans les octets, tel que rapporté par la commande DIR.

- `BYTE m_attribute`L’attribut byte du fichier.

- `char m_szFullName[_MAX_PATH]`Le nom de fichier absolu dans l’ensemble de caractères Windows.

*lpszFileName*<br/>
Une chaîne dans l’ensemble de caractères Windows qui est le chemin vers le fichier désiré. Le chemin peut être relatif ou absolu, ou il peut contenir un nom de chemin réseau.

*Ptm*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="return-value"></a>Valeur de retour

VRAI si les informations d’état du fichier spécifié sont obtenues avec succès; autrement, FALSE.

### <a name="remarks"></a>Notes

La version non `GetStatus` statique de récupère les informations d’état du fichier ouvert associé à l’objet donné. `CFile`  La version `GetStatus` statique d’obtenir le statut de fichier à partir d’une trajectoire de fichier donnée sans réellement ouvrir le fichier. Cette version est utile pour tester l’existence et les droits d’accès d’un fichier.

Le `m_attribute` membre `CFileStatus` de la structure se réfère à l’ensemble d’attribut de fichier. La `CFile` classe fournit le type d’énumération **d’attribut** afin que les attributs de fichier puissent être spécifiés symboliquement :

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

## <a name="cfilehfilenull"></a><a name="hfilenull"></a>CFile::hFileNull

Détermine la présence d’une poignée `CFile` de fichier valide pour l’objet.

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>Notes

Cette constante est utilisée `CFile` pour déterminer si l’objet a une poignée de fichier valide.

L’exemple suivant montre cette opération :

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

## <a name="cfilelockrange"></a><a name="lockrange"></a>CFile::LockRange

Verrouille une gamme d’octets dans un fichier ouvert, en jetant une exception si le fichier est déjà verrouillé.

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Paramètres

*dwPos dwPos*<br/>
Le décalage byte du début de la gamme byte à verrouiller.

*dwCompte*<br/>
Le nombre d’octets dans la plage à verrouiller.

### <a name="remarks"></a>Notes

Le verrouillage d’octets dans un fichier empêche l’accès à ces octets par d’autres processus. Vous pouvez verrouiller plus d’une région d’un fichier, mais aucune région qui se chevauche ne peut être autorisée.

Lorsque vous déverrouillez la région en utilisant la `UnlockRange` fonction membre, la plage d’endlitude doit correspondre exactement à la région qui était auparavant verrouillée. La `LockRange` fonction ne fusionne pas les régions adjacentes. Si deux régions verrouillées sont adjacentes, vous devez déverrouiller chaque région séparément.

> [!NOTE]
> Cette fonction n’est `CMemFile`pas disponible pour la classe dérivée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

## <a name="cfilem_hfile"></a><a name="m_hfile"></a>CFile::m_hFile

Contient la poignée de fichier système d’exploitation pour un fichier ouvert.

```
HANDLE m_hFile;
```

### <a name="remarks"></a>Notes

`m_hFile`est une variable publique de type UINT. Il `CFile::hFileNull`contient , un indicateur de fichier vide indépendant du système d’exploitation, si la poignée n’a pas été attribuée.

L’utilisation de `m_hFile` n’est pas recommandée, parce que la signification du membre dépend de la classe dérivée. `m_hFile`est rendu public pour plus de commodité dans le soutien de l’utilisation non dépolymorphique de la classe.

## <a name="cfilem_ptm"></a><a name="m_ptm"></a>CFile::m_pTM

Pointeur `CAtlTransactionManager` vers un objet.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Notes

## <a name="cfileopen"></a><a name="open"></a>CFile::Ouvert

Surchargé. `Open`est conçu pour une `CFile` utilisation avec le constructeur par défaut.

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
Une chaîne qui contient le chemin vers le fichier désiré. Le chemin peut être relatif, absolu, ou un nom de réseau (UNC).

*nOpenFlags*<br/>
Un UINT qui définit le mode de partage et d’accès du fichier. Il spécifie les mesures à prendre lors de l’ouverture du fichier. Vous pouvez combiner les options en utilisant l’opérateur bitwise-OR ( **&#124;).** Une autorisation d’accès et une option d’action sont requises; les `modeCreate` `modeNoInherit` modes et les modes sont facultatifs. Consultez le constructeur [CFile](#cfile) pour une liste d’options de mode.

*Perror*<br/>
Un pointeur vers un objet existant d’exception de fichier qui recevra l’état d’une opération ratée.

*Ptm*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="return-value"></a>Valeur de retour

Nonzero si l’ouverture a été couronnée de succès; sinon 0. Le *paramètre pError n’est* significatif que si 0 est retourné.

### <a name="remarks"></a>Notes

Les `Open` deux fonctions sont des méthodes « sûres » pour l’ouverture d’un fichier, où une défaillance est une condition normale et prévue.

Alors `CFile` que le constructeur lance une exception `Open` dans un état d’erreur, retourne FALSE pour les conditions d’erreur. `Open`peut encore initialiser un objet [CFileException](../../mfc/reference/cfileexception-class.md) pour décrire l’erreur, cependant. Si vous ne fournissez pas le *paramètre pError,* ou si `Open` vous passez NULL pour `CFileException` *pError*, retourne FALSE et ne jette pas un . Si vous passez un pointeur à un existant, `CFileException`et `Open` rencontre une erreur, la fonction le remplit d’informations décrivant cette erreur. `Open`ne jette pas d’exception dans les deux cas.

Le tableau suivant décrit les `Open`résultats possibles de .

|`pError`|Erreur rencontrée|Valeur retournée|Contenu CFileException|
|--------------|------------------------|------------------|----------------------------|
|NULL|Non|TRUE|n/a|
|ptr à`CFileException`|Non|TRUE|inchangé|
|NULL|Oui|FALSE|n/a|
|ptr à`CFileException`|Oui|FALSE|initialisé pour décrire l’erreur|

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

## <a name="cfileoperator-handle"></a><a name="operator_handle"></a>CFile::opérateur HANDLE

Utilisez cet opérateur pour passer `CFile` une poignée à un objet à des fonctions telles `HANDLE`que [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) et [GetFileTime](/windows/win32/api/fileapi/nf-fileapi-getfiletime) qui s’attendent à un .

```
operator HANDLE() const;
```

## <a name="cfileread"></a><a name="read"></a>CFile::Lire

Lit les données dans un tampon `CFile` du fichier associé à l’objet.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Pointeur vers le tampon fourni par l’utilisateur qui doit recevoir les données lues à partir du fichier.

*nCompte*<br/>
Le nombre maximum d’octets à lire dans le fichier. Pour les fichiers en mode texte, les paires d’alimentation en ligne de retour de transport sont comptées comme des caractères simples.

### <a name="return-value"></a>Valeur de retour

Nombre d'octets transférés dans la mémoire tampon. Pour `CFile` toutes les classes, la valeur de retour peut être inférieure *à nCount* si la fin du fichier a été atteinte.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

Pour un autre exemple, voir [CFile::Open](#open).

## <a name="cfileremove"></a><a name="remove"></a>CFile::Supprimer

Cette fonction statique supprime le fichier spécifié par le chemin.

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszFileName*<br/>
Une chaîne qui est le chemin vers le fichier désiré. Le chemin peut être relatif ou absolu, et peut contenir un nom de réseau.

*Ptm*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="remarks"></a>Notes

`Remove`ne supprimera pas un répertoire.

La `Remove` fonction membre lance une exception si le fichier connecté est ouvert ou si le fichier ne peut pas être supprimé. Cette fonction est équivalente à la commande DEL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

## <a name="cfilerename"></a><a name="rename"></a>CFile::Rename

Cette fonction statique renomme le fichier spécifié.

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszOldName (en)*<br/>
Le vieux chemin.

*lpszNewName (en)*<br/>
La nouvelle voie.

*Ptm*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="remarks"></a>Notes

Les répertoires ne peuvent pas être renommés. Cette fonction est équivalente à la commande REN.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

## <a name="cfileseek"></a><a name="seek"></a>CFile::Chercher

Repositionne le pointeur de fichier dans un fichier ouvert.

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>Paramètres

*lOff*<br/>
Nombre d’octets pour déplacer le pointeur de fichier. Les valeurs positives déplacent le pointeur de fichier vers la fin du fichier; valeurs négatives déplacer le pointeur de fichier vers le début du fichier.

*nDe*<br/>
Position à chercher. Consultez la section Remarques pour les valeurs possibles.

### <a name="return-value"></a>Valeur de retour

La position du pointeur de fichier si la méthode a été réussie; autrement, la valeur de retour n’est `CFileException` pas définie et un pointeur à une exception est jeté.

### <a name="remarks"></a>Notes

Le tableau suivant répertorie les valeurs possibles pour le paramètre *nFrom.*

|Valeur|Description|
|-----------|-----------------|
|`CFile::begin`|Cherchez dès le début du fichier.|
|`CFile::current`|Cherchez à partir de l’emplacement actuel du pointeur de fichier.|
|`CFile::end`|Cherchez à partir de la fin du fichier.|

Lorsqu’un fichier est ouvert, le pointeur de fichier est positionné à 0, le début du fichier.

Vous pouvez définir le pointeur de fichiers à une position au-delà de la fin d’un fichier. Si vous le faites, la taille du fichier n’augmente pas jusqu’à ce que vous écriviez au fichier.

Le gestionnaire d’exception pour cette méthode doit supprimer l’objet d’exception après le traitement de l’exception.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

## <a name="cfileseektobegin"></a><a name="seektobegin"></a>CFile::SeekToBegin

Définit la valeur du pointeur de fichier au début du fichier.

```cpp
void SeekToBegin();
```

### <a name="remarks"></a>Notes

`SeekToBegin()` équivaut à `Seek( 0L, CFile::begin )`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

## <a name="cfileseektoend"></a><a name="seektoend"></a>CFile::SeekToEnd

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

## <a name="cfilesetfilepath"></a><a name="setfilepath"></a>CFile::SetFilePath

Appelez cette fonction pour spécifier le chemin du fichier. Par exemple, si le chemin d’un fichier n’est pas `SetFilePath` disponible lorsqu’un objet [CFile](../../mfc/reference/cfile-class.md) est construit, appelez pour le fournir.

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Paramètres

*lpszNewName (en)*<br/>
Pointeur à une chaîne spécifiant le nouveau chemin.

### <a name="remarks"></a>Notes

> [!NOTE]
> `SetFilePath`n’ouvre pas le fichier ni ne crée le fichier; il associe `CFile` simplement l’objet à un nom de chemin, qui peut ensuite être utilisé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

## <a name="cfilesetlength"></a><a name="setlength"></a>CFile::SetLength

Appelez cette fonction pour modifier la longueur du fichier.

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>Paramètres

*dwNewLen*<br/>
Longueur désirée du fichier dans les octets. Cette valeur peut être plus grande ou plus petite que la longueur actuelle du fichier. Le dossier sera prolongé ou tronqué, le cas échéant.

### <a name="remarks"></a>Notes

> [!NOTE]
> Avec `CMemFile`, cette fonction `CMemoryException` pourrait jeter un objet.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

## <a name="cfilesetstatus"></a><a name="setstatus"></a>CFile::SetStatus

Définit l’état du fichier associé à cet emplacement de fichier.

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszFileName*<br/>
Une chaîne qui est le chemin vers le fichier désiré. Le chemin peut être relatif ou absolu, et peut contenir un nom de réseau.

*statut*<br/>
Le tampon contenant les nouvelles informations sur l’état. Appelez `GetStatus` la fonction membre pour `CFileStatus` préfaire la structure avec les valeurs actuelles, puis apporter des modifications au besoin. Si une valeur est de 0, l’élément d’état correspondant n’est pas mis à jour. Consultez la fonction du membre [GetStatus](#getstatus) pour une description de la `CFileStatus` structure.

*Ptm*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="remarks"></a>Notes

Pour définir l’heure, modifiez le `m_mtime` champ de *statut*.

Lorsque vous passez `SetStatus` un appel à une tentative de changer uniquement `m_mtime` les attributs du fichier, et le membre de la structure de statut du fichier est nonzero, les attributs peuvent également être affectés (changer le timbre-temps peut avoir des effets secondaires sur les attributs). Si vous souhaitez seulement modifier les attributs du `m_mtime` fichier, définissez d’abord le membre `SetStatus`de la structure de statut du fichier à zéro, puis faites un appel à .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

## <a name="cfileunlockrange"></a><a name="unlockrange"></a>CFile::UnlockRange

Déverrouille une gamme d’octets dans un fichier ouvert.

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Paramètres

*dwPos dwPos*<br/>
Le décalage byte du début de la gamme byte à débloquer.

*dwCompte*<br/>
Le nombre d’octets dans la gamme à débloquer.

### <a name="remarks"></a>Notes

Voir la description de la fonction membre [LockRange](#lockrange) pour plus de détails.

> [!NOTE]
> Cette fonction n’est `CMemFile`pas disponible pour la classe dérivée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

## <a name="cfilewrite"></a><a name="write"></a>CFile::Ecrire

Écrit des données à partir d’un tampon au fichier associé à l’objet. `CFile`

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Paramètres

*lpBuf*<br/>
Un pointeur vers le tampon fourni par l’utilisateur qui contient les données à écrire au fichier.

*nCompte*<br/>
Le nombre d’octets à transférer à partir du tampon. Pour les fichiers en mode texte, les paires d’alimentation en ligne de retour de transport sont comptées comme des caractères simples.

### <a name="remarks"></a>Notes

`Write`jette une exception en réponse à plusieurs conditions, y compris l’état de disque-plein.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

Voir aussi les exemples de [CFile::CFile](#cfile) et [CFile::Open](#open).

## <a name="see-also"></a>Voir aussi

[Échantillon MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CStdioFile](../../mfc/reference/cstdiofile-class.md)<br/>
[Classe CMemFile](../../mfc/reference/cmemfile-class.md)
