---
title: Traitement des exceptions
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], exception handling
- DAO (Data Access Objects), exceptions [MFC]
- OLE exceptions [MFC], MFC functions
- exceptions [MFC], processing
- exception macros [MFC]
- termination functions, MFC
- MFC, exceptions
- exceptions [MFC], MFC throwing functions
ms.assetid: 26d4457c-8350-48f5-916e-78f919787c30
ms.openlocfilehash: d33da7a9bc81f9733df840a87fbbbeca1e02cc04
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855291"
---
# <a name="exception-processing"></a>Traitement des exceptions

Lorsqu’un programme s’exécute, un certain nombre de conditions anormales et d’erreurs appelées « exceptions » peuvent se produire. Il peut s’agir d’une insuffisance de mémoire, d’erreurs d’allocation de ressources et de l’impossibilité de trouver des fichiers.

Le bibliothèque MFC (Microsoft Foundation Class) utilise un modèle de gestion des exceptions qui est modélisé en détail après celui proposé par le Comité des normes ANSI C++pour. Un gestionnaire d’exceptions doit être configuré avant d’appeler une fonction qui peut rencontrer une situation anormale. Si la fonction rencontre une condition anormale, elle lève une exception et le contrôle est passé au gestionnaire d’exceptions.

Plusieurs macros incluses dans le bibliothèque MFC (Microsoft Foundation Class) configurent des gestionnaires d’exceptions. Un certain nombre d’autres fonctions globales vous aident à lever des exceptions spécialisées et à arrêter des programmes, si nécessaire. Ces macros et fonctions globales sont classées dans les catégories suivantes :

- Les macros d’exception, qui structurent votre gestionnaire d’exceptions.

- Fonctions de levée d’exception), qui génèrent des exceptions de types spécifiques.

- Fonctions d’arrêt, qui provoquent l’arrêt du programme.

Pour obtenir des exemples et des informations supplémentaires, consultez l’article [exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="exception-macros"></a>Macros d’exception

|||
|-|-|
|[Essayez](#try)|Désigne un bloc de code pour le traitement des exceptions.|
|[CEPTION](#catch)|Désigne un bloc de code pour intercepter une exception à partir du bloc **try** précédent.|
|[CATCH_ALL](#catch_all)|Désigne un bloc de code pour intercepter toutes les exceptions du bloc **try** précédent.|
|[AND_CATCH](#and_catch)|Désigne un bloc de code pour intercepter des types d’exception supplémentaires à partir du bloc **try** précédent.|
|[AND_CATCH_ALL](#and_catch_all)|Désigne un bloc de code pour intercepter tous les autres types d’exception supplémentaires levés dans un bloc **try** précédent.|
|[END_CATCH](#end_catch)|Termine le dernier bloc de code **catch** ou **AND_CATCH** .|
|[END_CATCH_ALL](#end_catch_all)|Met fin au dernier bloc de code **CATCH_ALL** .|
|[THROW](#throw)|Lève une exception spécifiée.|
|[THROW_LAST](#throw_last)|Lève l’exception actuellement gérée sur le gestionnaire externe suivant.|

### <a name="exception-throwing-functions"></a>Fonctions de levée d’exception

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|Lève une exception d’archive.|
|[AfxThrowFileException](#afxthrowfileexception)|Lève une exception de fichier.|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|Lève une exception d’argument non valide.|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|Lève une exception de mémoire.|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|Lève une exception non prise en charge.|
|[AfxThrowResourceException](#afxthrowresourceexception)|Lève une exception de ressource Windows introuvable.|
|[AfxThrowUserException](#afxthrowuserexception)|Lève une exception dans une action de programme initiée par l’utilisateur.|

MFC fournit deux fonctions de levée d’exception spécifiquement pour les exceptions OLE :

### <a name="ole-exception-functions"></a>Fonctions d’exception OLE

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|Lève une exception dans une fonction OLE Automation.|
|[AfxThrowOleException](#afxthrowoleexception)|Lève une exception OLE.|

Pour prendre en charge les exceptions de base de données, les classes de base de données fournissent deux classes d’exception, `CDBException` et `CDaoException`, ainsi que des fonctions globales pour prendre en charge les types d’exception :

### <a name="dao-exception-functions"></a>Fonctions d’exception DAO

|||
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|Lève une [CDaoException](../../mfc/reference/cdaoexception-class.md) à partir de votre propre code.|
|[AfxThrowDBException](#afxthrowdbexception)|Lève une [CDBException](../../mfc/reference/cdbexception-class.md) à partir de votre propre code.|

MFC fournit la fonction d’arrêt suivante :

### <a name="termination-functions"></a>Fonctions d’arrêt

|||
|-|-|
|[AfxAbort](#afxabort)|Appelé pour terminer une application lorsqu’une erreur irrécupérable se produit.|

##  <a name="try"></a>Essayez

Configure un bloc **try** .

```
TRY
```

### <a name="remarks"></a>Notes

Un bloc **try** identifie un bloc de code qui peut lever des exceptions. Ces exceptions sont gérées dans les blocs **catch** et **AND_CATCH** suivants. La récursivité est autorisée : les exceptions peuvent être passées à un bloc **try** externe, soit en les ignorant ou en utilisant la macro THROW_LAST. Mettez fin au bloc **try** avec une macro END_CATCH ou END_CATCH_ALL.

Pour plus d’informations, consultez l’article [exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Exemple

Consultez l’exemple pour [catch](#catch).

### <a name="requirements"></a>Spécifications

En-tête : afx.h

##  <a name="catch"></a>CEPTION

Définit un bloc de code qui intercepte le premier type d’exception levée dans le bloc **try** précédent.

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Paramètres

*exception_class*<br/>
Spécifie le type d’exception à tester. Pour obtenir la liste des classes d’exceptions standard, consultez la classe [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Spécifie un nom pour un pointeur d’objet exception qui sera créé par la macro. Vous pouvez utiliser le nom du pointeur pour accéder à l’objet exception dans le bloc **catch** . Cette variable est déclarée pour vous.

### <a name="remarks"></a>Notes

Le code de traitement des exceptions peut interroger l’objet exception, le cas échéant, pour obtenir plus d’informations sur la cause spécifique de l’exception. Appelez la macro THROW_LAST pour déplacer le traitement vers le frame d’exception externe suivant. Mettez fin au bloc **try** avec une macro END_CATCH.

Si *exception_class* est la classe `CException`, tous les types d’exception seront interceptés. Vous pouvez utiliser la fonction membre [CObject :: IsKindOf](../../mfc/reference/cobject-class.md#iskindof) pour déterminer l’exception spécifique qui a été levée. Une meilleure façon d’intercepter plusieurs genres d’exceptions consiste à utiliser des instructions **AND_CATCH** séquentielles, chacune avec un type d’exception différent.

Le pointeur d’objet exception est créé par la macro. Vous n’avez pas besoin de le déclarer vous-même.

> [!NOTE]
>  Le bloc **catch** est défini en tant C++ que portée délimitée par des accolades. Si vous déclarez des variables dans cette portée, elles sont accessibles uniquement au sein de cette portée. Cela s’applique également à *exception_object_pointer_name*.

Pour plus d’informations sur les exceptions et la macro CATCH, consultez l’article [exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

##  <a name="catch_all"></a>CATCH_ALL

Définit un bloc de code qui intercepte tous les types d’exception levées dans le bloc **try** précédent.

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Paramètres

*exception_object_pointer_name*<br/>
Spécifie un nom pour un pointeur d’objet exception qui sera créé par la macro. Vous pouvez utiliser le nom du pointeur pour accéder à l’objet exception dans le bloc `CATCH_ALL`. Cette variable est déclarée pour vous.

### <a name="remarks"></a>Notes

Le code de traitement des exceptions peut interroger l’objet exception, le cas échéant, pour obtenir plus d’informations sur la cause spécifique de l’exception. Appelez la macro `THROW_LAST` pour déplacer le traitement vers le frame d’exception externe suivant. Si vous utilisez **CATCH_ALL**, mettez fin au bloc **try** avec une macro END_CATCH_ALL.

> [!NOTE]
>  Le bloc **CATCH_ALL** est défini en tant C++ que portée délimité par des accolades. Si vous déclarez des variables dans cette portée, elles sont accessibles uniquement au sein de cette portée.

Pour plus d’informations sur les exceptions, consultez l’article [exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Exemple

Consultez l’exemple pour [CFile :: Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Spécifications

  **En-tête** AFX. h

##  <a name="and_catch"></a>AND_CATCH

Définit un bloc de code pour intercepter les types d’exception supplémentaires levés dans un bloc **try** précédent.

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Paramètres

*exception_class*<br/>
Spécifie le type d’exception à tester. Pour obtenir la liste des classes d’exceptions standard, consultez la classe [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Nom d’un pointeur d’objet exception qui sera créé par la macro. Vous pouvez utiliser le nom du pointeur pour accéder à l’objet exception dans le bloc **AND_CATCH** . Cette variable est déclarée pour vous.

### <a name="remarks"></a>Notes

Utilisez la macro CATCH pour intercepter un type d’exception, puis la macro AND_CATCH pour intercepter chaque type suivant. Mettez fin au bloc **try** avec une macro END_CATCH.

Le code de traitement des exceptions peut interroger l’objet exception, le cas échéant, pour obtenir plus d’informations sur la cause spécifique de l’exception. Appelez la macro THROW_LAST dans le bloc **AND_CATCH** pour déplacer le traitement vers la trame d’exception externe suivante. **AND_CATCH** marque la fin du bloc **catch** ou **AND_CATCH** précédent.

> [!NOTE]
>  Le bloc **AND_CATCH** est défini en tant C++ qu’étendue (délimitée par des accolades). Si vous déclarez des variables dans cette portée, n’oubliez pas qu’elles sont accessibles uniquement au sein de cette étendue. Cela s’applique également à la variable *exception_object_pointer_name* .

### <a name="example"></a>Exemple

Consultez l’exemple pour [catch](#catch).

### <a name="requirements"></a>Spécifications

  **En-tête** AFX. h
##  <a name="and_catch_all"></a>AND_CATCH_ALL

Définit un bloc de code pour intercepter les types d’exception supplémentaires levés dans un bloc **try** précédent.

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Paramètres

*exception_object_pointer_name*<br/>
Nom d’un pointeur d’objet exception qui sera créé par la macro. Vous pouvez utiliser le nom du pointeur pour accéder à l’objet exception dans le bloc **AND_CATCH_ALL** . Cette variable est déclarée pour vous.

### <a name="remarks"></a>Notes

Utilisez la macro **catch** pour intercepter un type d’exception, puis la macro AND_CATCH_ALL pour intercepter tous les autres types suivants. Si vous utilisez AND_CATCH_ALL, mettez fin au bloc **try** avec une macro END_CATCH_ALL.

Le code de traitement des exceptions peut interroger l’objet exception, le cas échéant, pour obtenir plus d’informations sur la cause spécifique de l’exception. Appelez la macro THROW_LAST dans le bloc **AND_CATCH_ALL** pour déplacer le traitement vers la trame d’exception externe suivante. **AND_CATCH_ALL** marque la fin du bloc **catch** ou **AND_CATCH_ALL** précédent.

> [!NOTE]
>  Le bloc **AND_CATCH_ALL** est défini en tant C++ qu’étendue (délimitée par des accolades). Si vous déclarez des variables dans cette portée, n’oubliez pas qu’elles sont accessibles uniquement au sein de cette étendue.

### <a name="requirements"></a>Spécifications

  **En-tête** AFX. h

##  <a name="end_catch"></a>END_CATCH

Marque la fin du dernier bloc **catch** ou **AND_CATCH** .

```
END_CATCH
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur la macro END_CATCH, consultez l’article [exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Spécifications

  **En-tête** AFX. h

##  <a name="end_catch_all"></a>END_CATCH_ALL

Marque la fin du dernier bloc **CATCH_ALL88** ou **AND_CATCH_ALL** .

```
END_CATCH_ALL
```

### <a name="requirements"></a>Spécifications

  **En-tête** AFX. h

##  <a name="throw"></a>THROW (MFC)

Lève l’exception spécifiée.

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>Paramètres

*exception_object_pointer*<br/>
Pointe vers un objet d’exception dérivé de `CException`.

### <a name="remarks"></a>Notes

**Throw** interrompt l’exécution du programme, en passant le contrôle au bloc **catch** associé dans votre programme. Si vous n’avez pas fourni le bloc **catch** , le contrôle est passé à un module bibliothèque MFC (Microsoft Foundation Class) qui imprime un message d’erreur et se termine.

Pour plus d’informations, consultez l’article [exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Spécifications

  **En-tête** AFX. h

##  <a name="throw_last"></a>THROW_LAST

Renvoie l’exception au bloc **catch** externe suivant.

```
THROW_LAST()
```

### <a name="remarks"></a>Notes

Cette macro vous permet de lever une exception créée localement. Si vous essayez de lever une exception que vous venez de intercepter, elle sera normalement hors de portée et sera supprimée. Avec **THROW_LAST**, l’exception est passée correctement au gestionnaire **catch** suivant.

Pour plus d’informations, consultez l’article [exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Exemple

Consultez l’exemple pour [CFile :: Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Spécifications

  **En-tête** AFX. h

##  <a name="afxthrowarchiveexception"></a>AfxThrowArchiveException

Lève une exception d’archive.

```
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>Paramètres

*cause*<br/>
Spécifie un entier qui indique la raison de l’exception. Pour obtenir la liste des valeurs possibles, consultez [CArchiveException :: m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).

*lpszArchiveName*<br/>
Pointe vers une chaîne contenant le nom de l’objet `CArchive` à l’origine de l’exception (le cas échéant).

### <a name="requirements"></a>Spécifications

  **En-tête** AFX. h

##  <a name="afxthrowfileexception"></a>AfxThrowFileException

Lève une exception de fichier.

```
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Paramètres

*cause*<br/>
Spécifie un entier qui indique la raison de l’exception. Pour obtenir la liste des valeurs possibles, consultez [CFileException :: m_cause](../../mfc/reference/cfileexception-class.md#m_cause).

*lOsError*<br/>
Contient le numéro d’erreur du système d’exploitation (s’il est disponible) qui indique la raison de l’exception. Pour obtenir la liste des codes d’erreur, consultez le manuel de votre système d’exploitation.

*lpszFileName*<br/>
Pointe vers une chaîne contenant le nom du fichier qui a provoqué l’exception (le cas échéant).

### <a name="remarks"></a>Notes

Vous êtes responsable de la détermination de la cause en fonction du code d’erreur du système d’exploitation.

### <a name="requirements"></a>Spécifications

  **En-tête** AFX. h

## <a name="afxthrowinvalidargexception"></a>AfxThrowInvalidArgException

Lève une exception d’argument non valide.

### <a name="syntax"></a>Syntaxe

```
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>Notes

Cette fonction est appelée lorsque des arguments non valides sont utilisés.

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="afxthrowmemoryexception"></a>AfxThrowMemoryException

Lève une exception de mémoire.

```
void AfxThrowMemoryException();
```

### <a name="remarks"></a>Notes

Appelez cette fonction si les appels aux allocateurs de mémoire système sous-jacents (tels que **malloc** et la fonction Windows [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) ) échouent. Vous n’avez pas besoin de l’appeler pour **New** , car **New** lève une exception de mémoire automatiquement en cas d’échec de l’allocation de mémoire.

### <a name="requirements"></a>Spécifications

  **En-tête** AFX. h

##  <a name="afxthrownotsupportedexception"></a>AfxThrowNotSupportedException

Lève une exception qui est le résultat d’une demande d’une fonctionnalité non prise en charge.

```
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>Spécifications

  **En-tête** AFX. h

##  <a name="afxthrowresourceexception"></a>AfxThrowResourceException

Lève une exception de ressource.

```
void  AfxThrowResourceException();
```

### <a name="remarks"></a>Notes

Cette fonction est normalement appelée lorsqu’une ressource Windows ne peut pas être chargée.

### <a name="requirements"></a>Spécifications

  **En-tête** AFX. h

##  <a name="afxthrowuserexception"></a>AfxThrowUserException

Lève une exception pour arrêter une opération de l’utilisateur final.

```
void AfxThrowUserException();
```

### <a name="remarks"></a>Notes

Cette fonction est normalement appelée juste après `AfxMessageBox` a signalé une erreur à l’utilisateur.

### <a name="requirements"></a>Spécifications

  **En-tête** AFX. h

##  <a name="afxthrowoledispatchexception"></a>AfxThrowOleDispatchException

Utilisez cette fonction pour lever une exception dans une fonction OLE Automation.

```
void AFXAPI AfxThrowOleDispatchException(
    WORD wCode ,
    LPCSTR lpszDescription,
    UINT nHelpID = 0);

void AFXAPI AfxThrowOleDispatchException(
    WORD wCode,
    UINT nDescriptionID,
    UINT nHelpID = -1);
```

### <a name="parameters"></a>Paramètres

*wCode*<br/>
Code d’erreur spécifique à votre application.

*lpszDescription*<br/>
Description verbale de l’erreur.

*nDescriptionID*<br/>
ID de ressource pour la description de l’erreur verbale.

*nHelpID*<br/>
Un contexte d’aide pour l’aide de votre application (. HLP).

### <a name="remarks"></a>Notes

Les informations fournies à cette fonction peuvent être affichées par l’application pilote (Microsoft Visual Basic ou une autre application cliente OLE Automation).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** AFX. h

##  <a name="afxthrowoleexception"></a>AfxThrowOleException

Crée un objet de type `COleException` et lève une exception.

```
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>Paramètres

*SC*<br/>
Code d’État OLE qui indique la raison de l’exception.

*h*<br/>
Handle d’un code de résultat qui indique la raison de l’exception.

### <a name="remarks"></a>Notes

La version qui accepte un HRESULT comme argument convertit ce code de résultat en SCODE correspondant. Pour plus d’informations sur HRESULT et SCODE, consultez [structure of com Error Codes](/windows/win32/com/structure-of-com-error-codes) in the SDK Windows.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao. h

##  <a name="afxthrowdaoexception"></a>AfxThrowDaoException

Appelez cette fonction pour lever une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md) à partir de votre propre code.

```
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>Paramètres

*nAfxDaoError*<br/>
Valeur entière représentant un code d’erreur étendu DAO, qui peut être l’une des valeurs listées sous [CDaoException :: m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror).

*SCODE*<br/>
Code d’erreur OLE de DAO, de type SCODE. Pour plus d’informations, consultez la section [CDaoException :: m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).

### <a name="remarks"></a>Notes

Le Framework appelle également `AfxThrowDaoException`. Dans votre appel, vous pouvez passer l’un des paramètres ou les deux. Par exemple, si vous souhaitez déclencher l’une des erreurs définies dans **CDaoException :: nAfxDaoError** , mais que vous ne vous souciez pas du paramètre *SCODE* , transmettez un code valide dans le paramètre *nAfxDaoError* et acceptez la valeur par défaut de *SCODE*.

Pour plus d’informations sur les exceptions liées aux classes DAO MFC, consultez Class `CDaoException` dans ce livre et l’article [exceptions : Database exceptions](../../mfc/exceptions-database-exceptions.md).

### <a name="requirements"></a>Spécifications

  **En-tête** AFXDB. h

##  <a name="afxthrowdbexception"></a>AfxThrowDBException

Appelez cette fonction pour lever une exception de type `CDBException` à partir de votre propre code.

```
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>Paramètres

*nRetCode*<br/>
Valeur de type RETCODE, qui définit le type d’erreur qui a provoqué la levée de l’exception.

*pdbonly*<br/>
Pointeur vers l’objet `CDatabase` qui représente la connexion à la source de données à laquelle l’exception est associée.

*risquent*<br/>
Handle HSTMT ODBC qui spécifie le descripteur d’instruction auquel l’exception est associée.

### <a name="remarks"></a>Notes

Le Framework appelle `AfxThrowDBException` lorsqu’il reçoit un RETCODE ODBC d’un appel à une fonction API ODBC et interprète le RETCODE comme une condition exceptionnelle plutôt qu’une erreur pouvant être attendue. Par exemple, une opération d’accès aux données peut échouer en raison d’une erreur de lecture sur le disque.

Pour plus d’informations sur les valeurs RETCODE définies par ODBC, consultez le chapitre 8, « récupération des informations d’État et d’erreur », dans le SDK Windows. Pour plus d’informations sur les extensions MFC à ces codes, consultez la classe [CDBException](../../mfc/reference/cdbexception-class.md).

### <a name="requirements"></a>Spécifications

  **En-tête** AFX. h

##  <a name="afxabort"></a>AfxAbort

Fonction d’arrêt par défaut fournie par MFC.

```
void  AfxAbort();
```

### <a name="remarks"></a>Notes

`AfxAbort` est appelée en interne par les fonctions membres MFC lorsqu’il y a une erreur irrécupérable, telle qu’une exception non interceptée qui ne peut pas être gérée. Vous pouvez appeler `AfxAbort` dans les rares cas où vous rencontrez une erreur catastrophique à partir de laquelle vous ne pouvez pas effectuer de récupération.

### <a name="example"></a>Exemple

Consultez l’exemple pour [catch](#catch).

### <a name="requirements"></a>Spécifications

  **En-tête** AFX. h

## <a name="see-also"></a>Voir aussi

[Macros et globales](mfc-macros-and-globals.md)<br/>
[CException, classe](cexception-class.md)<br/>
[CInvalidArgException, classe](cinvalidargexception-class.md)
