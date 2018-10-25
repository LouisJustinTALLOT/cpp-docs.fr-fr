---
title: CFileException, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFileException
- AFX/CFileException
- AFX/CFileException::CFileException
- AFX/CFileException::ErrnoToException
- AFX/CFileException::GetErrorMessage
- AFX/CFileException::OsErrorToException
- AFX/CFileException::ThrowErrno
- AFX/CFileException::ThrowOsError
- AFX/CFileException::m_cause
- AFX/CFileException::m_lOsError
- AFX/CFileException::m_strFileName
dev_langs:
- C++
helpviewer_keywords:
- CFileException [MFC], CFileException
- CFileException [MFC], ErrnoToException
- CFileException [MFC], GetErrorMessage
- CFileException [MFC], OsErrorToException
- CFileException [MFC], ThrowErrno
- CFileException [MFC], ThrowOsError
- CFileException [MFC], m_cause
- CFileException [MFC], m_lOsError
- CFileException [MFC], m_strFileName
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8db7d3f59ae226eff00c2c3c0f286db996669ce1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072640"
---
# <a name="cfileexception-class"></a>CFileException, classe

Représente une condition d'exception liée à un fichier.

## <a name="syntax"></a>Syntaxe

```
class CFileException : public CException
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CFileException::CFileException](#cfileexception)|Construit un objet `CFileException`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CFileException::ErrnoToException](#errnotoexception)|Retourne une erreur correspondant à un numéro d’erreur d’exécution de code.|
|[CFileException::GetErrorMessage](#geterrormessage)|Récupère le message qui décrit une exception.|
|[CFileException::OsErrorToException](#oserrortoexception)|Retourne un code de cause correspondant à un code d’erreur de système d’exploitation.|
|[CFileException::ThrowErrno](#throwerrno)|Lève une exception de fichier basée sur un numéro d’erreur de runtime.|
|[CFileException::ThrowOsError](#throwoserror)|Lève une exception de fichier basée sur un numéro d’erreur de système d’exploitation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CFileException::m_cause](#m_cause)|Contient le code portable correspondant à la cause de l’exception.|
|[CFileException::m_lOsError](#m_loserror)|Contient le numéro d’erreur de système d’exploitation associés.|
|[CFileException::m_strFileName](#m_strfilename)|Contient le nom du fichier pour cette exception.|

## <a name="remarks"></a>Notes

Le `CFileException` classe inclut des données membres publiques qui contiennent le code portable cause et le numéro d’erreur spécifique du système d’exploitation. La classe fournit également des fonctions membres statiques pour lever des exceptions de fichier et pour retourner des codes de cause pour les erreurs de système d’exploitation et les erreurs d’exécution C.

`CFileException` les objets sont construits et levées `CFile` fonctions membres et dans les fonctions membres des classes dérivées. Vous pouvez accéder à ces objets dans l’étendue d’un **CATCH** expression. Pour une portabilité, utilisez uniquement le code de cause pour obtenir la raison d’une exception. Pour plus d’informations sur les exceptions, consultez l’article [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>Configuration requise

**En-tête :** afx.h

##  <a name="cfileexception"></a>  CFileException::CFileException

Construit un `CFileException` objet qui stocke le code de la cause et le code du système d’exploitation dans l’objet.

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Paramètres

*cause*<br/>
Une variable de type énuméré qui indique la raison de l’exception. Consultez [CFileException::m_cause](#m_cause) pour obtenir la liste des valeurs possibles.

*lOsError*<br/>
Une raison spécifique de système d’exploitation pour l’exception, s’il est disponible. Le *lOsError* paramètre fournit plus d’informations que *provoquer* est.

*lpszArchiveName*<br/>
Pointe vers une chaîne contenant le nom de la `CFile` objet qui provoque l’exception.

### <a name="remarks"></a>Notes

N’utilisez pas ce constructeur directement, mais plutôt appeler la fonction globale [AfxThrowFileException](exception-processing.md#afxthrowfileexception).

> [!NOTE]
>  La variable *lOsError* s’applique uniquement aux `CFile` et `CStdioFile` objets. Le `CMemFile` classe ne gère pas ce code d’erreur.

##  <a name="errnotoexception"></a>  CFileException::ErrnoToException

Convertit une valeur d’erreur de bibliothèque du run-time donné en un `CFileException` erreur valeur énumérée.

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>Paramètres

*nErrno*<br/>
Un code d’erreur entier tel que défini dans le fichier include de l’exécution ERRNO. H.

### <a name="return-value"></a>Valeur de retour

Valeur énumérée qui correspond à une valeur d’erreur de bibliothèque du run-time donné.

### <a name="remarks"></a>Notes

Consultez [CFileException::m_cause](#m_cause) pour obtenir la liste de ces valeurs énumérées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

##  <a name="geterrormessage"></a>  CFileException::GetErrorMessage

Récupère le texte qui décrit une exception.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>Paramètres

*lpszError*<br/>
[in, out] Pointeur vers une mémoire tampon qui reçoit un message d’erreur.

*nMaxError*<br/>
[in] Le nombre maximal de caractères de que la mémoire tampon spécifiée peut contenir. Cela inclut le caractère null de fin.

*pnHelpContext*<br/>
[in, out] Pointeur vers un entier non signé qui reçoit l’ID de contexte d’aide. Si `NULL`, aucun ID n’est retourné.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode a réussi ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Si la mémoire tampon spécifiée est trop petite, le message d’erreur est tronqué.

### <a name="example"></a>Exemple

L’exemple suivant utilise `CFileException::GetErrorMessage`.

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

##  <a name="m_cause"></a>  CFileException::m_cause

Contient des valeurs définies par un type énuméré `CFileException`.

```
int m_cause;
```

### <a name="remarks"></a>Notes

Ce membre de données est une variable publique de type **int**. Voici les énumérateurs et leurs significations :

- `CFileException::none` 0 : aucune erreur ne s’est produite.

- `CFileException::genericException` 1 : une erreur non spécifiée s’est produite.

- `CFileException::fileNotFound` 2 : le fichier n’a pas pu être localisé.

- `CFileException::badPath` 3 : tout ou partie du chemin d’accès n’est pas valide.

- `CFileException::tooManyOpenFiles` 4 : le nombre autorisé de fichiers ouverts a été dépassé.

- `CFileException::accessDenied` 5 : le fichier n’est pas accessible.

- `CFileException::invalidFile` 6 : la tentative d’utilisation d’un handle de fichier non valide a été effectuée.

- `CFileException::removeCurrentDir` 7 : Impossible de supprimer le répertoire de travail actuel.

- `CFileException::directoryFull` 8 : il n’y a aucune autre entrée de répertoire.

- `CFileException::badSeek` 9 : erreur, essayez de définir le pointeur de fichier.

- `CFileException::hardIO` 10 : une erreur matérielle s’est produite.

- `CFileException::sharingViolation` 11 : PARTAGE. EXE n’a pas été chargé, ou une région partagée a été verrouillée.

- `CFileException::lockViolation` 12 : tentative de verrouillage d’une région déjà verrouillée.

- `CFileException::diskFull` 14 : le disque est plein.

- `CFileException::endOfFile` 15 : la fin du fichier a été atteinte.

    > [!NOTE]
    >  Ces énumérateurs de cause `CFileException` sont distincts des énumérateurs de cause `CArchiveException`.

    > [!NOTE]
    > `CArchiveException::generic` est déconseillé. Utilisez plutôt `genericException`. Si **générique** est utilisé dans une application et généré avec/CLR, la syntaxe qui en résulte que les erreurs ne sont pas faciles à déchiffrer.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

##  <a name="m_loserror"></a>  CFileException::m_lOsError

Contient le code d’erreur de système d’exploitation pour cette exception.

```
LONG m_lOsError;
```

### <a name="remarks"></a>Notes

Consultez le manuel technique de votre système d’exploitation pour obtenir la liste des codes d’erreur. Ce membre de données est une variable publique de type LONG.

##  <a name="m_strfilename"></a>  CFileException::m_strFileName

Contient le nom du fichier pour cette condition d’exception.

```
CString m_strFileName;
```

##  <a name="oserrortoexception"></a>  CFileException::OsErrorToException

Retourne un énumérateur qui correspond à une donnée *lOsError* valeur. Si le code d’erreur est inconnu, la fonction retourne `CFileException::generic`.

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>Paramètres

*lOsError*<br/>
Code d’erreur spécifique du système d’exploitation.

### <a name="return-value"></a>Valeur de retour

Valeur énumérée qui correspond à une valeur d’erreur de système d’exploitation donné.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

##  <a name="throwerrno"></a>  CFileException::ThrowErrno

Construit un `CFileException` objet correspondant à une donnée *nErrno* valeur, puis lève l’exception.

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Paramètres

*nErrno*<br/>
Un code d’erreur entier tel que défini dans le fichier include de l’exécution ERRNO. H.

*lpszFileName*<br/>
Un pointeur vers la chaîne contenant le nom du fichier qui a provoqué l’exception, s’il est disponible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

##  <a name="throwoserror"></a>  CFileException::ThrowOsError

Lève une `CFileException` correspondant à une donnée *lOsError* valeur. Si le code d’erreur est inconnu, la fonction lève une exception codée en tant que `CFileException::generic`.

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Paramètres

*lOsError*<br/>
Code d’erreur spécifique du système d’exploitation.

*lpszFileName*<br/>
Un pointeur vers la chaîne contenant le nom du fichier qui a provoqué l’exception, s’il est disponible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>Voir aussi

[CException, classe](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Traitement des exceptions](../../mfc/reference/exception-processing.md)

