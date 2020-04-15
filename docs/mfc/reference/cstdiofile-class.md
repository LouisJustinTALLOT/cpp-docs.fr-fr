---
title: Classe CStdioFile
ms.date: 08/29/2019
f1_keywords:
- CStdioFile
- AFX/CStdioFile
- AFX/CStdioFile::CStdioFile
- AFX/CStdioFile::Open
- AFX/CStdioFile::ReadString
- AFX/CStdioFile::Seek
- AFX/CStdioFile::WriteString
- AFX/CStdioFile::m_pStream
helpviewer_keywords:
- CStdioFile [MFC], CStdioFile
- CStdioFile [MFC], Open
- CStdioFile [MFC], ReadString
- CStdioFile [MFC], Seek
- CStdioFile [MFC], WriteString
- CStdioFile [MFC], m_pStream
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
ms.openlocfilehash: 80ee65aa339a38b3d8434bc4c7cb977e263f037b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366017"
---
# <a name="cstdiofile-class"></a>Classe CStdioFile

Représente un fichier de flux C run-time tel qu’ouvert par le [fopen](../../c-runtime-library/reference/fopen-wfopen.md)fonction run-time .

## <a name="syntax"></a>Syntaxe

```
class CStdioFile : public CFile
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CStdioFile::CStdioFile](#cstdiofile)|Construit un `CStdioFile` objet à partir d’un path ou d’un pointeur de fichier.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CStdioFile::Ouvert](#open)|Surchargé. Open est conçu pour `CStdioFile` une utilisation avec le constructeur par défaut (Overrides [CFile::Open](../../mfc/reference/cfile-class.md#open)).|
|[CStdioFile::LireString](#readstring)|Lit une seule ligne de texte.|
|[CStdioFile::Chercher](#seek)|Positionne le pointeur de fichier actuel.|
|[CStdioFile::WriteString](#writestring)|Écrit une seule ligne de texte.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|Contient un pointeur à un fichier ouvert.|

## <a name="remarks"></a>Notes

Les fichiers stream sont tamponnés et peuvent être ouverts en mode texte (par défaut) ou en mode binaire.

Le mode texte fournit un traitement spécial pour les paires d’alimentation de retour de chariot. Lorsque vous écrivez un flux de ligne (newline) caractère (0x0A) à un objet en mode `CStdioFile` texte, la paire byte (0x0D, 0x0A) est envoyée au fichier. Lorsque vous lisez, la paire byte (0x0D, 0x0A) est traduite en un seul byte 0x0A.

Les fonctions [CFile](../../mfc/reference/cfile-class.md) [Duplicate](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), `CStdioFile`et [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) ne sont pas pris en charge pour .

Si vous appelez ces `CStdioFile`fonctions sur un , vous obtiendrez un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Pour `CStdioFile`plus d’informations sur l’utilisation , voir les articles Fichiers dans [MFC](../../mfc/files-in-mfc.md) et Traitement des [fichiers](../../c-runtime-library/file-handling.md) dans la référence de bibliothèque *Run-Time*.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="cstdiofilecstdiofile"></a><a name="cstdiofile"></a>CStdioFile::CStdioFile

Construit et initialise un objet `CStdioFile`.

```
CStdioFile();
CStdioFile(CAtlTransactionManager* pTM);
CStdioFile(FILE* pOpenStream);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Paramètres

*pOpenStream*<br/>
Spécifie le pointeur de fichier retourné par un appel à la fonction C run-time [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

*lpszFileName*<br/>
Spécifie une chaîne qui est le chemin vers le fichier désiré. Le chemin peut être relatif ou absolu.

*nOpenFlags*<br/>
Spécifie les options de création de fichiers, de partage de fichiers et de modes d’accès aux fichiers. Vous pouvez spécifier plusieurs options **|** en utilisant l’opérateur bitwise OU () .

Une option de mode d’accès aux fichiers est requise; d’autres modes sont facultatifs. Voir [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) pour une liste d’options de mode et d’autres drapeaux. Dans la version MFC 3.0 et plus tard, les drapeaux de partage sont autorisés.

*Ptm*<br/>
Pointeur à l’objet CAtlTransactionManager.

### <a name="remarks"></a>Notes

Le constructeur par défaut n’attache `CStdioFile` pas de fichier à l’objet. Lors de l’utilisation de `CStdioFile::Open` ce constructeur, vous devez utiliser `CStdioFile` la méthode pour ouvrir un fichier et l’attacher à l’objet.

Le constructeur à paramètres uniques attache un `CStdioFile` flux de fichiers ouvert à l’objet. Les valeurs de pointeur autorisées incluent les pointeurs prédéfinis de fichier d’entrée/sortie *stdin*, *stdout,* ou *stderr.*

Le constructeur à deux `CStdioFile` paramètres crée un objet et ouvre le fichier correspondant avec le chemin donné.

Si vous passez NULL pour *pOpenStream* ou *lpszFileName*, `CInvalidArgException*`le constructeur jette un .

Si le fichier ne peut pas être ouvert `CFileException*`ou créé, le constructeur jette un .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

## <a name="cstdiofilem_pstream"></a><a name="m_pstream"></a>CStdioFile::m_pStream

Le `m_pStream` membre des données est le pointeur d’un `fopen`fichier ouvert tel que retourné par la fonction C run-time .

```
FILE* m_pStream;
```

### <a name="remarks"></a>Notes

C’est NULL si le dossier n’a jamais été ouvert ou a été fermé.

## <a name="cstdiofileopen"></a><a name="open"></a>CStdioFile::Ouvert

Surchargé. Open est conçu pour `CStdioFile` une utilisation avec le constructeur par défaut.

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
Une chaîne qui est le chemin vers le fichier désiré. Le chemin peut être relatif ou absolu.

*nOpenFlags*<br/>
Mode de partage et d’accès. Spécifie les mesures à prendre lors de l’ouverture du fichier. Vous pouvez combiner les options en utilisant l’opérateur bitwise-OR (&#124;). Une autorisation d’accès et une option d’action sont requises; les modes modeCreate et modeNoInherit sont facultatifs.

*Perror*<br/>
Un pointeur vers un objet existant d’exception de fichier qui recevra l’état d’une opération ratée.

*Ptm*<br/>
Pointeur `CAtlTransactionManager` vers un objet.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

## <a name="cstdiofilereadstring"></a><a name="readstring"></a>CStdioFile::LireString

Lit les données de texte dans un tampon, jusqu’à une limite `CStdioFile` de *nMax*-1 caractères, à partir du fichier associé à l’objet.

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>Paramètres

*lpsz lpsz*<br/>
Spécifie un pointeur vers un tampon fourni par l’utilisateur qui recevra une chaîne de texte non terminée.

*Nmax*<br/>
Spécifie le nombre maximum de caractères à lire, sans compter le caractère nul de fin.

*rString (en)*<br/>
Une référence `CString` à un objet qui contiendra la chaîne lorsque la fonction revient.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le tampon contenant les données du texte. NULL si la fin du fichier a été atteinte sans lire de données; ou si boolean, FALSE si la fin du fichier a été atteint sans lire de données.

### <a name="remarks"></a>Notes

La lecture est arrêtée par le premier personnage newline. Si, dans ce cas, moins de *caractères nMax*-1 ont été lus, un caractère newline est stocké dans le tampon. Un caractère nul ('0') est joint dans les deux cas.

[CFile::Read](../../mfc/reference/cfile-class.md#read) est également disponible pour l’entrée en mode texte, mais il ne se termine pas sur une paire d’alimentation de retour de transport.

> [!NOTE]
> La `CString` version de cette `'\n'` fonction supprime le si présent; la version LPTSTR ne le fait pas.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

## <a name="cstdiofileseek"></a><a name="seek"></a>CStdioFile::Chercher

Repositionne le pointeur dans un fichier précédemment ouvert.

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>Paramètres

*lOff*<br/>
Nombre d’octets pour déplacer le pointeur.

*nDe*<br/>
Mode de mouvement pointeur. Il doit s’agir de l’une des valeurs suivantes : 

- `CFile::begin`: Déplacez les octets *lOff de* pointeur de fichier vers l’avant dès le début du fichier.

- `CFile::current`: Déplacez les octets *lOff* de pointeur de fichier de la position actuelle dans le fichier.

- `CFile::end`: Déplacez les octets *lOff* de pointeur de fichier de la fin du fichier. Notez que *lOff* doit être négatif pour chercher dans le fichier existant; valeurs positives chercheront au-delà de la fin du fichier.

### <a name="return-value"></a>Valeur de retour

Si la position demandée est légale, `Seek` renvoie le nouvel byte compensé dès le début du dossier. Dans le cas contraire, la valeur `CFileException` de retour n’est pas définie et un objet est lancé.

### <a name="remarks"></a>Notes

La `Seek` fonction permet un accès aléatoire au contenu d’un fichier en déplaçant le pointeur d’un montant spécifié, absolument ou relativement. Aucune donnée n’est réellement lue pendant la recherche. Si la position demandée est plus grande que la taille du fichier, la longueur du fichier sera étendue à cette position, et aucune exception ne sera lancée.

Lorsqu’un fichier est ouvert, le pointeur de fichier est positionné à 0, le début du fichier.

Cette mise `Seek` en œuvre est basée sur `fseek`la fonction Bibliothèque Run-Time (CRT). Il y a plusieurs `Seek` limites à l’utilisation des flux ouverts en mode texte. Pour plus d’informations, voir [fseek, _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md).

### <a name="example"></a>Exemple

L’exemple suivant montre `Seek` comment utiliser pour déplacer le pointeur 1000 octets depuis le début du `cfile` fichier. Notez `Seek` que ne lisez pas les données, de sorte que vous devez par la suite appeler [CStdioFile::ReadString](#readstring) pour lire les données.

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

## <a name="cstdiofilewritestring"></a><a name="writestring"></a>CStdioFile::WriteString

Écrit des données à partir d’un tampon au fichier associé à l’objet. `CStdioFile`

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Paramètres

*lpsz lpsz*<br/>
Spécifie un pointeur à un tampon qui contient une corde non terminée.

### <a name="remarks"></a>Notes

Le caractère nul de `\0`fin () n’est pas écrit au dossier. Cette méthode écrit des caractères newline dans *lpsz* au fichier comme une paire d’alimentation de retour de voiture.

Si vous souhaitez écrire des données qui ne sont `CStdioFile::Write` pas non résiliées à un fichier, utilisez ou [CFile::Écrire](../../mfc/reference/cfile-class.md#write).

Cette méthode lance `CInvalidArgException*` un si vous spécifiez NULL pour le paramètre *lpsz.*

Cette méthode lance `CFileException*` une réponse aux erreurs du système de fichiers.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>Voir aussi

[CFile, classe](../../mfc/reference/cfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFile, classe](../../mfc/reference/cfile-class.md)<br/>
[CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)<br/>
[CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)<br/>
[CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[Classe D’origine CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)
