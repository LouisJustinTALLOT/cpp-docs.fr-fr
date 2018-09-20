---
title: CStdioFile, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStdioFile
- AFX/CStdioFile
- AFX/CStdioFile::CStdioFile
- AFX/CStdioFile::Open
- AFX/CStdioFile::ReadString
- AFX/CStdioFile::Seek
- AFX/CStdioFile::WriteString
- AFX/CStdioFile::m_pStream
dev_langs:
- C++
helpviewer_keywords:
- CStdioFile [MFC], CStdioFile
- CStdioFile [MFC], Open
- CStdioFile [MFC], ReadString
- CStdioFile [MFC], Seek
- CStdioFile [MFC], WriteString
- CStdioFile [MFC], m_pStream
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bbe6d2bd5ea8d03a73fd7389da9eeb0e7ca32cdf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442420"
---
# <a name="cstdiofile-class"></a>CStdioFile, classe

Représente un fichier de flux de runtime C tel qu’il est ouvert par la fonction d’exécution [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

## <a name="syntax"></a>Syntaxe

```
class CStdioFile : public CFile
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CStdioFile::CStdioFile](#cstdiofile)|Construit un `CStdioFile` objet à partir d’un pointeur de fichier ou chemin d’accès.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CStdioFile::Open](#open)|Surchargé. Open est conçu pour une utilisation avec la valeur par défaut `CStdioFile` constructeur (remplace [CFile::Open](../../mfc/reference/cfile-class.md#open)).|
|[CStdioFile::ReadString](#readstring)|Lit une seule ligne de texte.|
|[CStdioFile::Seek](#seek)|Positionne le pointeur de fichier actuel.|
|[CStdioFile::WriteString](#writestring)|Écrit une seule ligne de texte.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|Contient un pointeur vers un fichier ouvert.|

## <a name="remarks"></a>Notes

Fichiers de Stream sont mis en mémoire tampon et peuvent être ouvert en mode texte (la valeur par défaut) ou en mode binaire.

Mode texte fournit un traitement spécial des paires de sauts de ligne de transport. Lorsque vous écrivez un saut de ligne (0x0A) de caractères à un mode texte `CStdioFile` object, la paire d’octets (0x0D, 0x0A) est envoyé dans le fichier. Lors de la lecture, la paire d’octets (0x0D, 0x0A) est converti en un seul octet 0x0A.

Le [CFile](../../mfc/reference/cfile-class.md) fonctions [dupliquer](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), et [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) ne sont pas pris en charge pour `CStdioFile`.

Si vous appelez ces fonctions sur un `CStdioFile`, vous obtiendrez un [exception CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Pour plus d’informations sur l’utilisation de `CStdioFile`, consultez les articles [fichiers dans MFC](../../mfc/files-in-mfc.md) et [gestion des fichiers](../../c-runtime-library/file-handling.md) dans le *Run-Time Library Reference*.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>Configuration requise

**En-tête :** afx.h

##  <a name="cstdiofile"></a>  CStdioFile::CStdioFile

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
Spécifie le pointeur de fichier retourné par un appel à la fonction d’exécution C [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

*lpszFileName*<br/>
Spécifie une chaîne qui est le chemin d’accès au fichier désiré. Le chemin d’accès peut être relatif ou absolu.

*nOpenFlags*<br/>
Spécifie les options pour la création de fichiers, de partage de fichiers et de modes d’accès de fichier. Vous pouvez spécifier plusieurs options à l’aide de l’opération OR au niveau du bit ( **|** ) opérateur.

Une option de mode d’accès fichier est obligatoire. autres modes sont facultatifs. Consultez [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) pour obtenir la liste des options du mode et d’autres indicateurs. Dans MFC version 3.0 et versions ultérieure, les indicateurs de partage sont autorisées.

*pTM*<br/>
Pointeur vers l’objet CAtlTransactionManager.

### <a name="remarks"></a>Notes

Le constructeur par défaut ne s’attache pas un fichier à la `CStdioFile` objet. Lorsque vous utilisez ce constructeur, vous devez utiliser le `CStdioFile::Open` méthode pour ouvrir un fichier et l’attacher à la `CStdioFile` objet.

Le constructeur unique paramètre attache un flux de fichier ouvert à la `CStdioFile` objet. Autorisé les valeurs de pointeur incluent les pointeurs de fichier d’entrée/sortie prédéfinis *stdin*, *stdout*, ou *stderr*.

Le constructeur de deux paramètres crée un `CStdioFile` de l’objet et ouvre le fichier correspondant avec le chemin d’accès donné.

Si vous passez la valeur NULL soit *pOpenStream* ou *lpszFileName*, le constructeur lève un `CInvalidArgException*`.

Si le fichier ne peut pas être ouvert ou créé, le constructeur lève un `CFileException*`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

##  <a name="m_pstream"></a>  CStdioFile::m_pStream

Le `m_pStream` membre de données est le pointeur vers un fichier ouvert, tel que retourné par la fonction d’exécution C `fopen`.

```
FILE* m_pStream;
```

### <a name="remarks"></a>Notes

Sa valeur est NULL si le fichier n’a jamais été ouvert ou a été fermé.

##  <a name="open"></a>  CStdioFile::Open

Surchargé. Open est conçu pour une utilisation avec la valeur par défaut `CStdioFile` constructeur.

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
Chaîne qui est le chemin d’accès au fichier désiré. Le chemin d’accès peut être relatif ou absolu.

*nOpenFlags*<br/>
Mode de partage et d’accès. Spécifie l’action à entreprendre lors de l’ouverture du fichier. Vous pouvez combiner les options à l’aide de l’opération de bits OR (&#124;) opérateur. Autorisation d’un accès et un partage sont requis ; les modes modeCreate et modeNoInherit sont facultatifs.

*pError*<br/>
Pointeur vers un objet d’exception de fichier existant qui doit recevoir l’état d’une opération ayant échouée.

*pTM*<br/>
Pointeur vers un `CAtlTransactionManager` objet.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

##  <a name="readstring"></a>  CStdioFile::ReadString

Lit les données de texte dans une mémoire tampon, jusqu'à une limite de *nMax*-1 caractères, à partir du fichier associé à la `CStdioFile` objet.

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>Paramètres

*lpsz*<br/>
Spécifie un pointeur vers une mémoire tampon fournie par l’utilisateur qui recevra une chaîne de texte se terminant par null.

*nombre maximal*<br/>
Spécifie le nombre maximal de caractères à lire, sans compter le caractère null de fin.

*rString*<br/>
Une référence à un `CString` objet qui contient la chaîne au retour de fonction.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la mémoire tampon contenant les données de texte. NULL si la fin du fichier a été atteinte sans lire toutes les données ; ou, si le booléen, FALSE si la fin du fichier a été atteinte sans lire toutes les données.

### <a name="remarks"></a>Notes

Lecture est arrêtée par le premier caractère de saut de ligne. Si, dans ce cas, moins de *nMax*-1 caractères ont été lus, un caractère de saut de ligne est stocké dans la mémoire tampon. Un caractère null ('\0') est ajouté dans les deux cas.

[CFile::Read](../../mfc/reference/cfile-class.md#read) est également disponible pour les entrées en mode texte, mais il ne se termine pas sur une paire de sauts de ligne de transport.

> [!NOTE]
>  Le `CString` version de cette fonction supprime le `'\n'` s’il est présent ; la version LPTSTR est pas le cas.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

##  <a name="seek"></a>  CStdioFile::Seek

Repositionne le pointeur dans un fichier ouvert précédemment.

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>Paramètres

*lOff*<br/>
Nombre d’octets pour déplacer le pointeur.

*Ndepuis*<br/>
Mode de déplacement du pointeur. Doit être une des valeurs suivantes :

- `CFile::begin`: Déplacer le pointeur de fichier *lOff* octets transférer à partir du début du fichier.

- `CFile::current`: Déplacer le pointeur de fichier *lOff* octets à partir de la position actuelle dans le fichier.

- `CFile::end`: Déplacer le pointeur de fichier *lOff* octets à partir de la fin du fichier. Notez que *lOff* doit être négatif à rechercher dans l’existant de fichiers ; positif valeurs cherchera au-delà de la fin du fichier.

### <a name="return-value"></a>Valeur de retour

Si la position demandée est légale, `Seek` retourne l’offset d’octet à partir du début du fichier. Sinon, la valeur de retour n’est pas définie et un `CFileException` objet est levé.

### <a name="remarks"></a>Notes

Le `Seek` fonction autorise l’accès aléatoire au contenu d’un fichier en déplaçant le pointeur une quantité spécifiée, relative ou absolue. Aucune donnée n’est lue pendant la recherche. Si la position demandée est supérieure à la taille du fichier, la longueur du fichier sera étendue à cette position, et aucune exception n’est levée.

Lorsqu’un fichier est ouvert, le pointeur de fichier est positionné à l’offset 0, le début du fichier.

Cette implémentation de `Seek` est basée sur la fonction de la bibliothèque Runtime (CRT) `fseek`. Il existe plusieurs limites sur l’utilisation de `Seek` sur les flux ouverts en mode texte. Pour plus d’informations, consultez [fseek, _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md).

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser `Seek` pour déplacer le pointeur de 1 000 octets à partir du début de la `cfile` fichier. Notez que `Seek` ne lit pas les données, vous devez appeler par la suite [CStdioFile::ReadString](#readstring) pour lire les données.

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

##  <a name="writestring"></a>  CStdioFile::WriteString

Écrit des données à partir d’une mémoire tampon dans le fichier associé à la `CStdioFile` objet.

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Paramètres

*lpsz*<br/>
Spécifie un pointeur vers une mémoire tampon qui contient une chaîne se terminant par null.

### <a name="remarks"></a>Notes

Le caractère null de fin ( `\0`) n’est pas écrite dans le fichier. Cette méthode écrit des caractères de saut de ligne *lpsz* vers le fichier comme une paire retour chariot de transport.

Si vous souhaitez écrire des données qui ne sont pas terminée dans un fichier, utilisez `CStdioFile::Write` ou [CFile::Write](../../mfc/reference/cfile-class.md#write).

Cette méthode lève un `CInvalidArgException*` si vous spécifiez NULL pour le *lpsz* paramètre.

Cette méthode lève un `CFileException*` en réponse aux erreurs de système de fichiers.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>Voir aussi

[CFile, classe](../../mfc/reference/cfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFile, classe](../../mfc/reference/cfile-class.md)<br/>
[CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)<br/>
[CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)<br/>
[CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[CNotSupportedException, classe](../../mfc/reference/cnotsupportedexception-class.md)
