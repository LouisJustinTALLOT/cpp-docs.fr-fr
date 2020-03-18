---
title: CFileException, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: a3514c76d4136fe2bc0b096cc382e6f7f4dd3392
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418649"
---
# <a name="cfileexception-class"></a>CFileException, classe

Représente une condition d'exception liée à un fichier.

## <a name="syntax"></a>Syntaxe

```
class CFileException : public CException
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CFileException :: CFileException](#cfileexception)|Construit un objet `CFileException`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CFileException :: ErrnoToException](#errnotoexception)|Retourne le code qui correspond à un numéro d’erreur au moment de l’exécution.|
|[CFileException :: GetErrorMessage](#geterrormessage)|Récupère le message décrivant une exception.|
|[CFileException :: OsErrorToException](#oserrortoexception)|Retourne un code de cause correspondant à un code d’erreur du système d’exploitation.|
|[CFileException :: ThrowErrno](#throwerrno)|Lève une exception de fichier en fonction d’un numéro d’erreur d’exécution.|
|[CFileException :: ThrowOsError](#throwoserror)|Lève une exception de fichier en fonction du numéro d’erreur du système d’exploitation.|

### <a name="public-data-members"></a>Membres de données publics

|Name|Description|
|----------|-----------------|
|[CFileException :: m_cause](#m_cause)|Contient le code portable correspondant à la cause de l’exception.|
|[CFileException :: m_lOsError](#m_loserror)|Contient le numéro d’erreur du système d’exploitation associé.|
|[CFileException :: m_strFileName](#m_strfilename)|Contient le nom du fichier pour cette exception.|

## <a name="remarks"></a>Notes

La classe `CFileException` comprend des membres de données publics qui contiennent le code de cause portable et le numéro d’erreur spécifique au système d’exploitation. La classe fournit également des fonctions membres statiques pour lever des exceptions de fichier et pour retourner des codes de cause à la fois pour les erreurs du système d’exploitation et les erreurs Runtime C.

les objets `CFileException` sont construits et levés dans `CFile` fonctions membres et dans les fonctions membres des classes dérivées. Vous pouvez accéder à ces objets dans l’étendue d’une expression **catch** . Pour la portabilité, utilisez uniquement le code de cause pour obtenir la raison d’une exception. Pour plus d’informations sur les exceptions, consultez l’article [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="cfileexception"></a>CFileException :: CFileException

Construit un objet `CFileException` qui stocke le code de cause et le code du système d’exploitation dans l’objet.

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Paramètres

*cause*<br/>
Variable de type énuméré qui indique la raison de l’exception. Pour obtenir la liste des valeurs possibles, consultez [CFileException :: m_cause](#m_cause) .

*lOsError*<br/>
Raison spécifique au système d’exploitation de l’exception, si elle est disponible. Le paramètre *lOsError* fournit plus d’informations que la *cause* .

*lpszArchiveName*<br/>
Pointe vers une chaîne contenant le nom de l’objet `CFile` à l’origine de l’exception.

### <a name="remarks"></a>Notes

N’utilisez pas ce constructeur directement, mais appelez plutôt la fonction globale [AfxThrowFileException](exception-processing.md#afxthrowfileexception).

> [!NOTE]
>  La variable *lOsError* s’applique uniquement aux objets `CFile` et `CStdioFile`. La classe `CMemFile` ne gère pas ce code d’erreur.

##  <a name="errnotoexception"></a>CFileException :: ErrnoToException

Convertit une valeur d’erreur de la bibliothèque Runtime donnée en `CFileException` valeur d’erreur énumérée.

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>Paramètres

*nErrno*<br/>
Un code d’erreur entier, tel que défini dans le fichier include au moment de l’exécution. Manutention.

### <a name="return-value"></a>Valeur de retour

Valeur énumérée qui correspond à une valeur d’erreur de la bibliothèque Runtime donnée.

### <a name="remarks"></a>Notes

Consultez [CFileException :: m_cause](#m_cause) pour obtenir la liste des valeurs énumérées possibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

##  <a name="geterrormessage"></a>CFileException :: GetErrorMessage

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
dans Nombre maximal de caractères que la mémoire tampon spécifiée peut contenir. Cela comprend le caractère null de fin.

*pnHelpContext*<br/>
[in, out] Pointeur vers un entier non signé qui reçoit l’ID de contexte d’aide. Si `NULL`, aucun ID n’est retourné.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode a réussi ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Si la mémoire tampon spécifiée est trop petite, le message d’erreur est tronqué.

### <a name="example"></a>Exemple

L'exemple suivant utilise `CFileException::GetErrorMessage`.

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

##  <a name="m_cause"></a>CFileException :: m_cause

Contient des valeurs définies par un type énuméré `CFileException`.

```
int m_cause;
```

### <a name="remarks"></a>Notes

Ce membre de données est une variable publique de type **int**. Les énumérateurs et leurs significations sont les suivants :

- `CFileException::none` 0 : aucune erreur ne s’est produite.

- `CFileException::genericException` 1 : une erreur non spécifiée s’est produite.

- `CFileException::fileNotFound` 2 : le fichier est introuvable.

- `CFileException::badPath` 3 : la totalité ou une partie du chemin d’accès n’est pas valide.

- `CFileException::tooManyOpenFiles` 4 : le nombre autorisé de fichiers ouverts a été dépassé.

- `CFileException::accessDenied` 5 : impossible d’accéder au fichier.

- `CFileException::invalidFile` 6 : une tentative d’utilisation d’un descripteur de fichier non valide a été tentée.

- `CFileException::removeCurrentDir` 7 : impossible de supprimer le répertoire de travail actuel.

- `CFileException::directoryFull` 8 : il n’y a plus d’entrées de répertoire.

- `CFileException::badSeek` 9 : une erreur s’est produite lors de la tentative de définition du pointeur de fichier.

- `CFileException::hardIO` 10 : une erreur matérielle s’est produite.

- `CFileException::sharingViolation` 11 : partage. EXE n’a pas été chargé, ou une région partagée a été verrouillée.

- `CFileException::lockViolation` 12 : tentative de verrouillage d’une région déjà verrouillée.

- `CFileException::diskFull` 14 : le disque est plein.

- `CFileException::endOfFile` 15 : la fin du fichier a été atteinte.

    > [!NOTE]
    >  Ces énumérateurs de cause `CFileException` sont distincts des énumérateurs de cause `CArchiveException`.

    > [!NOTE]
    > `CArchiveException::generic` est déconseillé. Utilisez `genericException` à la place. Si le **générique** est utilisé dans une application et généré avec/CLR, les erreurs de syntaxe qui en résultent ne sont pas faciles à déchiffrer.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

##  <a name="m_loserror"></a>CFileException :: m_lOsError

Contient le code d’erreur du système d’exploitation pour cette exception.

```
LONG m_lOsError;
```

### <a name="remarks"></a>Notes

Pour obtenir la liste des codes d’erreur, consultez le manuel technique de votre système d’exploitation. Ce membre de données est une variable publique de type LONG.

##  <a name="m_strfilename"></a>CFileException :: m_strFileName

Contient le nom du fichier pour cette condition d’exception.

```
CString m_strFileName;
```

##  <a name="oserrortoexception"></a>CFileException :: OsErrorToException

Retourne un énumérateur qui correspond à une valeur *lOsError* donnée. Si le code d’erreur est inconnu, la fonction retourne `CFileException::generic`.

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>Paramètres

*lOsError*<br/>
Code d’erreur spécifique au système d’exploitation.

### <a name="return-value"></a>Valeur de retour

Valeur énumérée qui correspond à une valeur d’erreur du système d’exploitation donnée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

##  <a name="throwerrno"></a>CFileException :: ThrowErrno

Construit un objet `CFileException` correspondant à une valeur *nErrno* donnée, puis lève l’exception.

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Paramètres

*nErrno*<br/>
Un code d’erreur entier, tel que défini dans le fichier include au moment de l’exécution. Manutention.

*lpszFileName*<br/>
Pointeur vers la chaîne contenant le nom du fichier qui a provoqué l’exception, s’il est disponible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

##  <a name="throwoserror"></a>CFileException :: ThrowOsError

Lève une `CFileException` correspondant à une valeur *lOsError* donnée. Si le code d’erreur est inconnu, la fonction lève une exception codée comme `CFileException::generic`.

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Paramètres

*lOsError*<br/>
Code d’erreur spécifique au système d’exploitation.

*lpszFileName*<br/>
Pointeur vers la chaîne contenant le nom du fichier qui a provoqué l’exception, s’il est disponible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>Voir aussi

[CException, classe](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Traitement des exceptions](../../mfc/reference/exception-processing.md)
