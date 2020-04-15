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
ms.openlocfilehash: 2d1025ca33d5641982ba52f1ac539db85df3bfd5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373890"
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
|[CFileException::ErrnoToException](#errnotoexception)|Les retours causent du code correspondant à un numéro d’erreur de durée.|
|[CFileException::GetErrorMessage](#geterrormessage)|Récupère le message décrivant une exception.|
|[CFileException::OsErrorToException](#oserrortoexception)|Renvoie un code de cause correspondant à un code d’erreur du système d’exploitation.|
|[CFileException::ThrowErrno](#throwerrno)|Lance une exception de fichier basée sur un numéro d’erreur de temps d’exécution.|
|[CFileException::ThrowOsError](#throwoserror)|Jetez une exception de fichier basée sur un numéro d’erreur du système d’exploitation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CFileException::m_cause](#m_cause)|Contient du code portable correspondant à la cause d’exception.|
|[CFileException::m_lOsError](#m_loserror)|Contient le numéro d’erreur du système d’exploitation connexe.|
|[CFileException::m_strFileName](#m_strfilename)|Contient le nom du fichier pour cette exception.|

## <a name="remarks"></a>Notes

La `CFileException` classe comprend les membres de données publiques qui détiennent le code de cause portable et le numéro d’erreur spécifique au système d’exploitation. La classe fournit également des fonctions de membre statiques pour lancer des exceptions de fichier et pour retourner des codes de cause pour les erreurs de système d’exploitation et les erreurs de temps d’exécution C.

`CFileException`les objets sont `CFile` construits et jetés dans les fonctions des membres et dans les fonctions des membres des classes dérivées. Vous pouvez accéder à ces objets dans le cadre d’une expression **CATCH.** Pour la portabilité, n’utilisez que le code de cause pour obtenir la raison d’une exception. Pour plus d’informations sur les exceptions, voir l’article [Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="cfileexceptioncfileexception"></a><a name="cfileexception"></a>CFileException::CFileException

Construit un `CFileException` objet qui stocke le code de cause et le code du système d’exploitation dans l’objet.

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Paramètres

*cause*<br/>
Une variable de type énuméré qui indique la raison de l’exception. Voir [CFileException:m_cause](#m_cause) pour une liste des valeurs possibles.

*lOsError*<br/>
Une raison spécifique au système d’exploitation de l’exception, si disponible. Le paramètre *lOsError* fournit plus d’informations que *la cause.*

*lpszArchiveName (en)*<br/>
Indique une chaîne contenant le `CFile` nom de l’objet causant l’exception.

### <a name="remarks"></a>Notes

N’utilisez pas ce constructeur directement, mais appelez plutôt la fonction globale [AfxThrowFileException](exception-processing.md#afxthrowfileexception).

> [!NOTE]
> La variable *lOsError* `CFile` ne `CStdioFile` s’applique qu’aux objets et aux objets. La `CMemFile` classe ne gère pas ce code d’erreur.

## <a name="cfileexceptionerrnotoexception"></a><a name="errnotoexception"></a>CFileException::ErrnoToException

Convertit une valeur d’erreur de `CFileException` bibliothèque en temps de course donnée en valeur d’erreur énumérée.

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>Paramètres

*nErrno (en)*<br/>
Un code d’erreur d’intégrier tel que défini dans le délai d’exécution comprend le fichier ERRNO. H.

### <a name="return-value"></a>Valeur de retour

Valeur énumérée qui correspond à une valeur d’erreur de bibliothèque donnée en temps de course.

### <a name="remarks"></a>Notes

Voir [CFileException:m_cause](#m_cause) pour une liste des valeurs énumérées possibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

## <a name="cfileexceptiongeterrormessage"></a><a name="geterrormessage"></a>CFileException::GetErrorMessage

Récupère le texte qui décrit une exception.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>Paramètres

*lpszError*<br/>
[dans, dehors] Pointer vers un tampon qui reçoit un message d’erreur.

*nMaxError (en)*<br/>
[dans] Le nombre maximum de caractères que le tampon spécifié peut contenir. Cela comprend le caractère nul de fin.

*pnHelpContext*<br/>
[dans, dehors] Pointeur vers un integer non signé qui reçoit l’ID contexte d’aide. Si `NULL`, aucune pièce d’identité n’est retournée.

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode a été réussie; autrement FALSE.

### <a name="remarks"></a>Notes

Si le tampon spécifié est trop petit, le message d’erreur est tronqué.

### <a name="example"></a>Exemple

L'exemple suivant utilise `CFileException::GetErrorMessage`.

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

## <a name="cfileexceptionm_cause"></a><a name="m_cause"></a>CFileException::m_cause

Contient des valeurs définies par un type énuméré `CFileException`.

```
int m_cause;
```

### <a name="remarks"></a>Notes

Ce membre de données est une variable publique de type **int**. Les enumérateurs et leurs significations sont les suivants :

- `CFileException::none`0: Aucune erreur ne s’est produite.

- `CFileException::genericException`1 : Une erreur non spécifiée s’est produite.

- `CFileException::fileNotFound`2: Le fichier n’a pas pu être localisé.

- `CFileException::badPath`3: Tout ou partie du chemin est invalide.

- `CFileException::tooManyOpenFiles`4 : Le nombre autorisé de fichiers ouverts a été dépassé.

- `CFileException::accessDenied`5: Le fichier n’a pas pu être consulté.

- `CFileException::invalidFile`6: Il y a eu une tentative d’utiliser une poignée de fichier invalide.

- `CFileException::removeCurrentDir`7: Le répertoire de travail actuel ne peut pas être supprimé.

- `CFileException::directoryFull`8: Il n’y a plus d’entrées d’annuaire.

- `CFileException::badSeek`9: Il y avait une erreur essayant de définir le pointeur de fichier.

- `CFileException::hardIO`10: Il y a eu une erreur matérielle.

- `CFileException::sharingViolation`11: PARTAGER. EXE n’était pas chargée, ou une région partagée était verrouillée.

- `CFileException::lockViolation`12: Il y a eu une tentative de verrouiller une région qui était déjà verrouillée.

- `CFileException::diskFull`14: Le disque est plein.

- `CFileException::endOfFile`15: La fin du dossier a été atteinte.

    > [!NOTE]
    >  Ces énumérateurs de cause `CFileException` sont distincts des énumérateurs de cause `CArchiveException`.

    > [!NOTE]
    > `CArchiveException::generic` est déconseillé. Utilisez `genericException` à la place. Si **le générique** est utilisé dans une application et construit avec /clr, les erreurs de syntaxe résultantes ne sont pas faciles à déchiffrer.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

## <a name="cfileexceptionm_loserror"></a><a name="m_loserror"></a>CFileException::m_lOsError

Contient le code d’erreur du système d’exploitation pour cette exception.

```
LONG m_lOsError;
```

### <a name="remarks"></a>Notes

Consultez votre manuel technique du système d’exploitation pour une liste de codes d’erreur. Ce membre des données est une variable publique de type LONG.

## <a name="cfileexceptionm_strfilename"></a><a name="m_strfilename"></a>CFileException::m_strFileName

Contient le nom du fichier pour cette condition d’exception.

```
CString m_strFileName;
```

## <a name="cfileexceptionoserrortoexception"></a><a name="oserrortoexception"></a>CFileException::OsErrorToException

Retourne un enumérateur qui correspond à une valeur *lOsError* donnée. Si le code d’erreur est `CFileException::generic`inconnu, alors la fonction revient .

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>Paramètres

*lOsError*<br/>
Un code d’erreur spécifique au système d’exploitation.

### <a name="return-value"></a>Valeur de retour

Valeur énumérée qui correspond à une valeur d’erreur donnée du système d’exploitation.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

## <a name="cfileexceptionthrowerrno"></a><a name="throwerrno"></a>CFileException::ThrowErrno

Construit un `CFileException` objet correspondant à une valeur *nErrno* donnée, puis jette l’exception.

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Paramètres

*nErrno (en)*<br/>
Un code d’erreur d’intégrier tel que défini dans le délai d’exécution comprend le fichier ERRNO. H.

*lpszFileName*<br/>
Un pointeur à la chaîne contenant le nom du fichier qui a causé l’exception, si disponible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

## <a name="cfileexceptionthrowoserror"></a><a name="throwoserror"></a>CFileException::ThrowOsError

Jette un `CFileException` correspondant à une valeur *lOsError* donnée. Si le code d’erreur est inconnu, alors `CFileException::generic`la fonction jette une exception codée comme .

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Paramètres

*lOsError*<br/>
Un code d’erreur spécifique au système d’exploitation.

*lpszFileName*<br/>
Un pointeur à la chaîne contenant le nom du fichier qui a causé l’exception, si disponible.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>Voir aussi

[Classe CException](../../mfc/reference/cexception-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Traitement des exceptions](../../mfc/reference/exception-processing.md)
