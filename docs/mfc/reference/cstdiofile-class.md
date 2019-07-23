---
title: CStdioFile, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 068e59fdc19821487bc78141d10743363221518e
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375838"
---
# <a name="cstdiofile-class"></a>CStdioFile, classe

Représente un fichier de flux Runtime C tel qu’il est ouvert par la fonction runtime [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

## <a name="syntax"></a>Syntaxe

```
class CStdioFile : public CFile
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CStdioFile::CStdioFile](#cstdiofile)|Construit un `CStdioFile` objet à partir d’un chemin d’accès ou d’un pointeur de fichier.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CStdioFile::Open](#open)|Surchargé. Open est conçu pour être utilisé avec le `CStdioFile` constructeur par défaut (remplace [CFile:: Open](../../mfc/reference/cfile-class.md#open)).|
|[CStdioFile::ReadString](#readstring)|Lit une seule ligne de texte.|
|[CStdioFile::Seek](#seek)|Positionne le pointeur de fichier actuel.|
|[CStdioFile::WriteString](#writestring)|Écrit une seule ligne de texte.|

### <a name="public-data-members"></a>Membres de données publics

|Name|Description|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|Contient un pointeur vers un fichier ouvert.|

## <a name="remarks"></a>Notes

Les fichiers de flux sont mis en mémoire tampon et peuvent être ouverts en mode texte (par défaut) ou en mode binaire.

Le mode texte fournit un traitement spécial pour les paires retour chariot-saut de ligne. Lorsque vous écrivez un caractère de saut de ligne (nouvelle ligne) (0x0A) sur un `CStdioFile` objet en mode texte, la paire d’octets (0x0D, 0x0A) est envoyée au fichier. Lorsque vous lisez, la paire d’octets (0x0D, 0x0A) est traduite en un seul octet 0x0A.

Les fonctions [CFile](../../mfc/reference/cfile-class.md) [duplicate](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange)et [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) ne sont pas prises en `CStdioFile`charge pour.

Si vous appelez ces fonctions sur un `CStdioFile`, vous obtiendrez un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Pour plus d’informations sur `CStdioFile`l’utilisation de, consultez les articles [fichiers dans MFC](../../mfc/files-in-mfc.md) et [gestion des fichiers](../../c-runtime-library/file-handling.md) dans la référence de la *bibliothèque Runtime*.

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
Spécifie le pointeur de fichier retourné par un appel à la fonction Runtime C [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

*lpszFileName*<br/>
Spécifie une chaîne qui correspond au chemin d’accès au fichier souhaité. Le chemin d’accès peut être relatif ou absolu.

*nOpenFlags*<br/>
Spécifie des options pour la création de fichiers, le partage de fichiers et les modes d’accès aux fichiers. Vous pouvez spécifier plusieurs options à l’aide de l’opérateur **|** de bits or ().

Une option de mode d’accès aux fichiers est requise; d’autres modes sont facultatifs. Pour obtenir la liste des options de mode et d’autres indicateurs, consultez [CFile:: CFile](../../mfc/reference/cfile-class.md#cfile) . Dans MFC version 3,0 et versions ultérieures, les indicateurs de partage sont autorisés.

*pTM*<br/>
Pointeur vers l’objet CAtlTransactionManager.

### <a name="remarks"></a>Notes

Le constructeur par défaut n’attache pas de fichier à `CStdioFile` l’objet. Lorsque vous utilisez ce constructeur, vous devez utiliser `CStdioFile::Open` la méthode pour ouvrir un fichier et l’attacher à `CStdioFile` l’objet.

Le constructeur à un seul paramètre attache un flux de fichier ouvert à `CStdioFile` l’objet. Les valeurs de pointeur autorisées incluent les pointeurs de fichier d’entrée/sortie ( *stdin*, *stdout*ou *stderr*) prédéfinis.

Le constructeur à deux paramètres crée un `CStdioFile` objet et ouvre le fichier correspondant avec le chemin d’accès donné.

Si vous transmettez la valeur NULL pour *pOpenStream* ou *lpszFileName*, le constructeur lève `CInvalidArgException*`une exception.

Si le fichier ne peut pas être ouvert ou créé, le constructeur lève `CFileException*`une exception.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

##  <a name="m_pstream"></a>  CStdioFile::m_pStream

Le `m_pStream` membre de données est le pointeur vers un fichier ouvert tel qu’il est retourné par la fonction `fopen`Runtime C.

```
FILE* m_pStream;
```

### <a name="remarks"></a>Notes

La valeur est NULL si le fichier n’a jamais été ouvert ou a été fermé.

##  <a name="open"></a>  CStdioFile::Open

Surchargé. Open est conçu pour être utilisé avec le `CStdioFile` constructeur par défaut.

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
Chaîne qui correspond au chemin d’accès au fichier souhaité. Le chemin d’accès peut être relatif ou absolu.

*nOpenFlags*<br/>
Mode de partage et d’accès. Spécifie l’action à exécuter lors de l’ouverture du fichier. Vous pouvez combiner des options à l’aide de l’opérateur&#124;de bits or (). Une autorisation d’accès et une option de partage sont requises. les modes modeCreate et modeNoInherit sont facultatifs.

*pError*<br/>
Pointeur vers un objet d’exception de fichier existant qui recevra l’état d’une opération ayant échoué.

*pTM*<br/>
Pointeur vers un `CAtlTransactionManager` objet.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

##  <a name="readstring"></a>  CStdioFile::ReadString

Lit les données de texte dans une mémoire tampon, jusqu’à une limite de *nmax*-1 caractères, à partir du `CStdioFile` fichier associé à l’objet.

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>Paramètres

*lpsz*<br/>
Spécifie un pointeur vers une mémoire tampon fournie par l’utilisateur qui recevra une chaîne de texte se terminant par un caractère null.

*nMax*<br/>
Spécifie le nombre maximal de caractères à lire, sans compter le caractère null de fin.

*rString*<br/>
Référence à un `CString` objet qui contiendra la chaîne quand la fonction est retournée.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la mémoire tampon qui contient les données de texte. NULL si la fin du fichier a été atteinte sans lire de données; ou si la valeur booléenne est FALSe si la fin du fichier a été atteinte sans lire de données.

### <a name="remarks"></a>Notes

La lecture est arrêtée par le premier caractère de saut de ligne. Si, dans ce cas, moins de *nmax*-1 caractères ont été lus, un caractère de saut de ligne est stocké dans la mémoire tampon. Un caractère null (' \ 0 ') est ajouté dans les deux cas.

[CFile:: Read](../../mfc/reference/cfile-class.md#read) est également disponible pour l’entrée en mode texte, mais elle ne se termine pas sur une paire retour chariot-saut de ligne.

> [!NOTE]
>  La `CString` version de cette fonction supprime le `'\n'` si présent; la version LPTStr ne le fait pas.

### <a name="example"></a>Exemples

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

##  <a name="seek"></a>  CStdioFile::Seek

Repositionne le pointeur dans un fichier précédemment ouvert.

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>Paramètres

*lOff*<br/>
Nombre d’octets pour déplacer le pointeur.

*nFrom*<br/>
Mode de déplacement du pointeur. Il doit s’agir de l’une des valeurs suivantes:

- `CFile::begin`: Déplacez le pointeur de fichier *lOff* d’octets vers l’avant à partir du début du fichier.

- `CFile::current`: Déplacez le pointeur de fichier *lOff* octets à partir de la position actuelle dans le fichier.

- `CFile::end`: Déplacez le pointeur de fichier *lOff* octets à partir de la fin du fichier. Notez que *lOff* doit être négatif pour effectuer une recherche dans le fichier existant; les valeurs positives recherchent au-delà de la fin du fichier.

### <a name="return-value"></a>Valeur de retour

Si la position demandée est conforme, `Seek` retourne le nouvel offset d’octet à partir du début du fichier. Dans le cas contraire, la valeur de retour n’est `CFileException` pas définie et un objet est levé.

### <a name="remarks"></a>Notes

La `Seek` fonction autorise l’accès aléatoire au contenu d’un fichier en déplaçant le pointeur d’une quantité spécifiée, de manière absolue ou relativement. Aucune donnée n’est réellement lue pendant la recherche. Si la position demandée est supérieure à la taille du fichier, la longueur du fichier est étendue à cette position et aucune exception n’est levée.

Lorsqu’un fichier est ouvert, le pointeur de fichier est positionné au décalage 0, le début du fichier.

Cette implémentation de `Seek` est basée sur la fonction `fseek`de bibliothèque Runtime (CRT). Il existe plusieurs limites sur l’utilisation de `Seek` sur des flux ouverts en mode texte. Pour plus d’informations, consultez [fseek, _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md).

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser `Seek` pour déplacer le pointeur 1000 octets à partir du début `cfile` du fichier. Notez que `Seek` ne lit pas les données. vous devez donc appeler [CStdioFile:: ReadString](#readstring) pour lire les données.

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

##  <a name="writestring"></a>  CStdioFile::WriteString

Écrit des données à partir d’une mémoire tampon dans le `CStdioFile` fichier associé à l’objet.

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Paramètres

*lpsz*<br/>
Spécifie un pointeur vers une mémoire tampon qui contient une chaîne terminée par le caractère null.

### <a name="remarks"></a>Notes

Le caractère null de fin ( `\0`) n’est pas écrit dans le fichier. Cette méthode écrit les caractères de saut de ligne dans *lpsz* dans le fichier sous la forme d’une paire retour chariot-saut de ligne.

Si vous souhaitez écrire des données qui ne se terminent pas par un caractère NULL dans un `CStdioFile::Write` fichier, utilisez ou [CFile:: Write](../../mfc/reference/cfile-class.md#write).

Cette méthode lève une `CInvalidArgException*` exception si vous spécifiez NULL pour le paramètre *lpsz* .

Cette méthode lève une `CFileException*` exception en réponse à des erreurs du système de fichiers.

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
