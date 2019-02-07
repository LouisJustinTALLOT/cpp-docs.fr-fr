---
title: Traitement des exceptions
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.exceptions
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
ms.openlocfilehash: 8b40afbfcc453a4908b434dc53b7b86959673453
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55851680"
---
# <a name="exception-processing"></a>Traitement des exceptions

Lorsqu’un programme s’exécute, un certain nombre de conditions anormales erreurs appelées « exceptions » peut se produire. Il peut s’agir de manquer de mémoire, erreurs d’allocation de ressources et l’impossibilité pour rechercher des fichiers.

La bibliothèque Microsoft Foundation Class utilise un schéma de gestion des exceptions qui s’inspire celui proposé par le comité de normes ANSI pour C++. Un gestionnaire d’exceptions doit être configuré avant d’appeler une fonction qui peut rencontrer une situation anormale. Si la fonction rencontre une condition anormale, elle lève une exception et le contrôle est passé au gestionnaire d’exceptions.

Plusieurs macros inclus avec la bibliothèque Microsoft Foundation Class configurera les gestionnaires d’exceptions. Un nombre d’autres fonctions globales permet de lever des exceptions spécialisées et arrêter les programmes, si nécessaire. Ces macros et fonctions globales se répartissent dans les catégories suivantes :

- Macros d’exception, dont la structure de votre gestionnaire d’exceptions.

- Exception-Throwing fonctions), qui génèrent des exceptions de types spécifiques.

- Fonctions d’arrêt, ce qui provoquent l’arrêt du programme.

Pour plus d’informations et des exemples, consultez l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="exception-macros"></a>Macros d’exception

|||
|-|-|
|[ESSAYEZ](#try)|Désigne un bloc de code pour le traitement des exceptions.|
|[CATCH](#catch)|Désigne un bloc de code pour intercepter d’exception de l’exemple précédent **essayez** bloc.|
|[CATCH_ALL](#catch_all)|Désigne un bloc de code pour intercepter toutes les exceptions à partir de l’exemple précédent **essayez** bloc.|
|[AND_CATCH](#and_catch)|Désigne un bloc de code pour intercepter des types d’exception supplémentaires à partir de l’exemple précédent **essayez** bloc.|
|[AND_CATCH_ALL](#and_catch_all)|Désigne un bloc de code pour intercepter tous les autres types supplémentaires d’exception levées dans un précédent **essayez** bloc.|
|[END_CATCH](#end_catch)|Met fin à la dernière **CATCH** ou **AND_CATCH** bloc de code.|
|[END_CATCH_ALL](#end_catch_all)|Met fin à la dernière **CATCH_ALL** bloc de code.|
|[THROW](#throw)|Lève une exception spécifiée.|
|[THROW_LAST](#throw_last)|Lève l’exception actuellement gérée au gestionnaire externe suivante.|

### <a name="exception-throwing-functions"></a>Levée d’exceptions de fonctions

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|Lève une exception de l’archive.|
|[AfxThrowFileException](#afxthrowfileexception)|Lève une exception de fichier.|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|Lève une exception d’argument non valide.|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|Lève une exception de mémoire.|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|Lève une exception non prise en charge.|
|[AfxThrowResourceException](#afxthrowresourceexception)|Lève une exception de ressource introuvable Windows.|
|[AfxThrowUserException](#afxthrowuserexception)|Lève une exception dans une action initiée par l’utilisateur d’un programme.|

MFC propose deux fonctions de levée d’exceptions en particulier pour les exceptions OLE :

### <a name="ole-exception-functions"></a>Fonctions d’Exception OLE

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|Lève une exception au sein d’une fonction d’automatisation OLE.|
|[AfxThrowOleException](#afxthrowoleexception)|Lève une exception OLE.|

Pour prendre en charge des exceptions de base de données, les classes de base de données fournissent deux classes d’exceptions, `CDBException` et `CDaoException`et les fonctions globales pour prendre en charge les types d’exception :

### <a name="dao-exception-functions"></a>Fonctions d’Exception DAO

|||
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|Lève une [CDaoException](../../mfc/reference/cdaoexception-class.md) à partir de votre propre code.|
|[AfxThrowDBException](#afxthrowdbexception)|Lève une [CDBException](../../mfc/reference/cdbexception-class.md) à partir de votre propre code.|

MFC fournit la fonction d’arrêt suivant :

### <a name="termination-functions"></a>Fonctions d’arrêt

|||
|-|-|
|[AfxAbort](#afxabort)|Appelée pour mettre fin à une application lorsqu’une erreur irrécupérable se produit.|

##  <a name="try"></a>  TRY

Configure un **essayez** bloc.

```
TRY
```

### <a name="remarks"></a>Notes

Un **essayez** bloc identifie un bloc de code qui peut-être lever des exceptions. Ces exceptions sont gérées dans l’exemple suivant **CATCH** et **AND_CATCH** blocs. La récursivité est autorisée : exceptions peuvent être passées à externe **essayez** bloc, en ignorant les ou à l’aide de la macro THROW_LAST. Fin le **essayez** bloc avec une macro END_CATCH ou END_CATCH_ALL.

Pour plus d’informations, consultez l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Exemple

Consultez l’exemple de [CATCH](#catch).

### <a name="requirements"></a>Spécifications

En-tête : afx.h

##  <a name="catch"></a>  CATCH

Définit un bloc de code qui intercepte le premier type d’exception levé dans l’exemple précédent **essayez** bloc.

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Paramètres

*exception_class*<br/>
Spécifie le type d’exception à tester. Pour obtenir la liste des classes d’exception standard, consultez la classe [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Spécifie un nom pour un pointeur d’objet d’exception qui sera créé par la macro. Vous pouvez utiliser le nom de pointeur pour accéder à l’objet d’exception dans le **CATCH** bloc. Cette variable est déclarée pour vous.

### <a name="remarks"></a>Notes

Le code de traitement des exceptions peut interroger l’objet d’exception, le cas échéant, pour obtenir plus d’informations sur la cause spécifique de l’exception. Appeler la macro THROW_LAST pour décaler le traitement à la prochaine trame exception externe. Fin le **essayez** bloc avec un END_CATCH (macro).

Si *classe_exception* est la classe `CException`, puis tous les types d’exception seront interceptées. Vous pouvez utiliser la [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) fonction membre pour déterminer quelle exception a été levée. Une meilleure façon d’intercepter plusieurs types d’exceptions consiste à utiliser séquentiel **AND_CATCH** instructions, chacun avec un autre type d’exception.

Le pointeur d’objet exception est créé par la macro. Vous n’avez pas besoin de déclarer vous-même.

> [!NOTE]
>  Le **CATCH** bloc est défini comme une portée C++ délimitée par des accolades. Si vous déclarez des variables dans cette portée, ils sont accessibles uniquement dans cette étendue. Cela s’applique également aux *nom_pointeur_objet_exception*.

Pour plus d’informations sur les exceptions et la macro CATCH, consultez l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

##  <a name="catch_all"></a>  CATCH_ALL

Définit un bloc de code qui intercepte tous les types d’exceptions levées dans l’exemple précédent **essayez** bloc.

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Paramètres

*exception_object_pointer_name*<br/>
Spécifie un nom pour un pointeur d’objet d’exception qui sera créé par la macro. Vous pouvez utiliser le nom de pointeur pour accéder à l’objet d’exception dans le `CATCH_ALL` bloc. Cette variable est déclarée pour vous.

### <a name="remarks"></a>Notes

Le code de traitement des exceptions peut interroger l’objet d’exception, le cas échéant, pour obtenir plus d’informations sur la cause spécifique de l’exception. Appeler le `THROW_LAST` macro de décalage de traitement dans le bloc d’exception externe suivant. Si vous utilisez **CATCH_ALL**, fin le **essayez** bloc avec un end_catch_all (macro).

> [!NOTE]
>  Le **CATCH_ALL** bloc est défini comme une portée C++ délimitée par des accolades. Si vous déclarez des variables dans cette portée, ils sont accessibles uniquement dans cette étendue.

Pour plus d’informations sur les exceptions, consultez l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Exemple

Consultez l’exemple de [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

##  <a name="and_catch"></a>  AND_CATCH

Définit un bloc de code pour intercepter des types supplémentaires d’exception levées dans un précédent **essayez** bloc.

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Paramètres

*exception_class*<br/>
Spécifie le type d’exception à tester. Pour obtenir la liste des classes d’exception standard, consultez la classe [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Un nom pour un pointeur d’objet d’exception qui sera créé par la macro. Vous pouvez utiliser le nom de pointeur pour accéder à l’objet d’exception dans le **AND_CATCH** bloc. Cette variable est déclarée pour vous.

### <a name="remarks"></a>Notes

Utilisez la macro CATCH pour intercepter un type d’exception, puis la macro AND_CATCH pour intercepter chaque type suivants. Fin le **essayez** bloc avec un END_CATCH (macro).

Le code de traitement des exceptions peut interroger l’objet d’exception, le cas échéant, pour obtenir plus d’informations sur la cause spécifique de l’exception. Appeler la macro THROW_LAST au sein de la **AND_CATCH** bloquer pour déplacer le traitement à la prochaine trame exception externe. **AND_CATCH** marque la fin de l’exemple précédent **CATCH** ou **AND_CATCH** bloc.

> [!NOTE]
>  Le **AND_CATCH** bloc est défini comme une portée C++ (délimitée par des accolades). Si vous déclarez des variables dans cette portée, n’oubliez pas de qu’ils sont accessibles uniquement dans cette étendue. Cela vaut également pour le *nom_pointeur_objet_exception* variable.

### <a name="example"></a>Exemple

Consultez l’exemple de [CATCH](#catch).

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h
##  <a name="and_catch_all"></a>  AND_CATCH_ALL

Définit un bloc de code pour intercepter des types supplémentaires d’exception levées dans un précédent **essayez** bloc.

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Paramètres

*exception_object_pointer_name*<br/>
Un nom pour un pointeur d’objet d’exception qui sera créé par la macro. Vous pouvez utiliser le nom de pointeur pour accéder à l’objet d’exception dans le **AND_CATCH_ALL** bloc. Cette variable est déclarée pour vous.

### <a name="remarks"></a>Notes

Utilisez le **CATCH** macro pour intercepter un type d’exception, puis l’and_catch_all (macro) pour intercepter tous les autres types suivants. Si vous utilisez AND_CATCH_ALL, se terminer par le **essayez** bloc avec un end_catch_all (macro).

Le code de traitement des exceptions peut interroger l’objet d’exception, le cas échéant, pour obtenir plus d’informations sur la cause spécifique de l’exception. Appeler la macro THROW_LAST au sein de la **AND_CATCH_ALL** bloquer pour déplacer le traitement à la prochaine trame exception externe. **AND_CATCH_ALL** marque la fin de l’exemple précédent **CATCH** ou **AND_CATCH_ALL** bloc.

> [!NOTE]
>  Le **AND_CATCH_ALL** bloc est défini comme une portée C++ (délimitée par des accolades). Si vous déclarez des variables dans cette portée, n’oubliez pas de qu’ils sont accessibles uniquement dans cette étendue.

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

##  <a name="end_catch"></a>  END_CATCH

Marque la fin de la dernière **CATCH** ou **AND_CATCH** bloc.

```
END_CATCH
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur la macro END_CATCH, consultez l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

##  <a name="end_catch_all"></a>  END_CATCH_ALL

Marque la fin de la dernière <strong>CATCH_ALL88 ou ** AND_CATCH_ALL</strong> bloc.

```
END_CATCH_ALL
```

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

##  <a name="throw"></a>  THROW (MFC)

Lève l’exception spécifiée.

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>Paramètres

*exception_object_pointer*<br/>
Pointe vers un objet d’exception dérivé `CException`.

### <a name="remarks"></a>Notes

**LEVER** interrompt l’exécution, en transmettant le contrôle à associé du programme **CATCH** bloquer dans votre programme. Si vous n’avez pas fourni la **CATCH** bloquer, puis le contrôle est passé à un module de bibliothèque Microsoft Foundation Class qui imprime une erreur de message et s’arrête.

Pour plus d’informations, consultez l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

##  <a name="throw_last"></a>  THROW_LAST

Renvoie l’exception à l’autre externe **CATCH** bloc.

```
THROW_LAST()
```

### <a name="remarks"></a>Notes

Cette macro vous permet de lever une exception créée localement. Si vous essayez de lever une exception que vous avez simplement interceptée, il passera normalement hors de portée et être supprimé. Avec **THROW_LAST**, l’exception est passée correctement à la suivante **CATCH** gestionnaire.

Pour plus d’informations, consultez l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Exemple

Consultez l’exemple de [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

##  <a name="afxthrowarchiveexception"></a>  AfxThrowArchiveException

Lève une exception de l’archive.

```
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>Paramètres

*cause*<br/>
Spécifie un entier qui indique la raison de l’exception. Pour obtenir la liste des valeurs possibles, consultez [CArchiveException::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).

*lpszArchiveName*<br/>
Pointe vers une chaîne contenant le nom de la `CArchive` objet qui a provoqué l’exception (si disponible).

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

##  <a name="afxthrowfileexception"></a>  AfxThrowFileException

Lève une exception de fichier.

```
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Paramètres

*cause*<br/>
Spécifie un entier qui indique la raison de l’exception. Pour obtenir la liste des valeurs possibles, consultez [CFileException::m_cause](../../mfc/reference/cfileexception-class.md#m_cause).

*lOsError*<br/>
Contient le numéro d’erreur de système d’exploitation (si disponible) qui indique la raison de l’exception. Consultez le manuel de votre système d’exploitation pour obtenir la liste des codes d’erreur.

*lpszFileName*<br/>
Pointe vers une chaîne contenant le nom du fichier qui a provoqué l’exception (si disponible).

### <a name="remarks"></a>Notes

Vous êtes chargé de déterminer la cause en fonction du code d’erreur de système d’exploitation.

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="afxthrowinvalidargexception"></a>  AfxThrowInvalidArgException

Lève une exception d’argument non valide.

### <a name="syntax"></a>Syntaxe

```
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>Notes

Cette fonction est appelée lorsque les arguments non valides sont utilisés.

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="afxthrowmemoryexception"></a>  AfxThrowMemoryException

Lève une exception de mémoire.

```
void AfxThrowMemoryException();
```

### <a name="remarks"></a>Notes

Appeler cette fonction si les appels à des allocateurs de mémoire système sous-jacent (tel que **malloc** et le [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) fonction de Windows) échouent. Vous n’avez pas besoin d’appeler pour **nouveau** car **nouveau** lève une exception de mémoire automatiquement si l’allocation de mémoire échoue.

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

##  <a name="afxthrownotsupportedexception"></a>  AfxThrowNotSupportedException

Lève une exception qui est le résultat d’une demande pour une fonctionnalité non prise en charge.

```
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

##  <a name="afxthrowresourceexception"></a>  AfxThrowResourceException

Lève une exception de la ressource.

```
void  AfxThrowResourceException();
```

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée lorsqu’une ressource de Windows ne peut pas être chargée.

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

##  <a name="afxthrowuserexception"></a>  AfxThrowUserException

Lève une exception pour arrêter une opération de l’utilisateur final.

```
void AfxThrowUserException();
```

### <a name="remarks"></a>Notes

Cette fonction est habituellement appelée immédiatement après `AfxMessageBox` a signalé une erreur à l’utilisateur.

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

##  <a name="afxthrowoledispatchexception"></a>  AfxThrowOleDispatchException

Utilisez cette fonction pour lever une exception au sein d’une fonction d’automatisation OLE.

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
Un code d’erreur spécifique à votre application.

*lpszDescription*<br/>
Description verbale de l’erreur.

*nDescriptionID*<br/>
ID de ressource pour la description d’erreur.

*nHelpID*<br/>
Un contexte d’aide pour l’aide de votre application (. Fichier HLP).

### <a name="remarks"></a>Notes

Les informations fournies à cette fonction peuvent être affichées par l’application de conduite (Microsoft Visual Basic ou une autre application de client OLE automation).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

##  <a name="afxthrowoleexception"></a>  AfxThrowOleException

Crée un objet de type `COleException` et lève une exception.

```
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>Paramètres

*sc*<br/>
Un code d’état OLE qui indique la raison de l’exception.

*hr*<br/>
Handle vers un code de résultat qui indique la raison de l’exception.

### <a name="remarks"></a>Notes

La version qui accepte une valeur HRESULT en tant qu’argument convertit ce code de résultat le SCODE correspondante. Pour plus d’informations sur la valeur HRESULT et SCODE, consultez [Structure of COM Error Codes](/windows/desktop/com/structure-of-com-error-codes) dans le SDK Windows.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao.h

##  <a name="afxthrowdaoexception"></a>  AfxThrowDaoException

Appelez cette fonction pour lever une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md) à partir de votre propre code.

```
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>Paramètres

*nAfxDaoError*<br/>
Une valeur entière qui représente un code d’erreur étendu de DAO, qui peut prendre l’une des valeurs répertoriées sous [CDaoException::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror).

*scode*<br/>
Un code d’erreur OLE de DAO, de type SCODE. Pour plus d’informations, consultez [CDaoException::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).

### <a name="remarks"></a>Notes

Le framework appelle également `AfxThrowDaoException`. Dans l’appel, vous pouvez passer de l’un des paramètres ou les deux. Par exemple, si vous souhaitez déclencher une des erreurs défini dans **CDaoException::nAfxDaoError** , mais vous ne vous souciez pas le *scode* paramètre, passez un code valid dans le *nAfxDaoError* paramètre et acceptez la valeur par défaut *scode*.

Pour plus d’informations sur les exceptions liées aux classes DAO MFC, consultez la classe `CDaoException` dans ce livre et l’article [Exceptions : Exceptions de base de données](../../mfc/exceptions-database-exceptions.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdb.h

##  <a name="afxthrowdbexception"></a>  AfxThrowDBException

Appelez cette fonction pour lever une exception de type `CDBException` à partir de votre propre code.

```
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>Paramètres

*nRetCode*<br/>
Une valeur de type et RETCODE contient, la définition du type d’erreur qui a provoqué l’exception levée.

*pdb*<br/>
Un pointeur vers le `CDatabase` objet qui représente la connexion de source de données à laquelle l’exception est associée.

*hstmt*<br/>
Un handle ODBC HSTMT qui spécifie le descripteur d’instruction à laquelle l’exception est associée.

### <a name="remarks"></a>Notes

Le framework appelle `AfxThrowDBException` lorsqu’il reçoit un RETCODE ODBC à partir d’un appel à une fonction API ODBC et les interprète le RETCODE comme une condition exceptionnelle, plutôt qu’une erreur prévisibles. Par exemple, une opération d’accès aux données peut échouer en raison d’une erreur de lecture du disque.

Pour plus d’informations sur les valeurs et RETCODE contient définies par ODBC, consultez le chapitre 8, « Récupération état et informations d’erreur, » dans le SDK Windows. Pour plus d’informations sur les extensions MFC pour ces codes, consultez la classe [CDBException](../../mfc/reference/cdbexception-class.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

##  <a name="afxabort"></a>  AfxAbort

La fonction d’arrêt par défaut fournie par MFC.

```
void  AfxAbort();
```

### <a name="remarks"></a>Notes

`AfxAbort` est appelée en interne par les fonctions membres MFC lorsqu’il existe une erreur irrécupérable, par exemple une exception non interceptée qui ne peut pas être gérée. Vous pouvez appeler `AfxAbort` dans les rares cas où vous rencontrez une erreur grave, à partir de laquelle vous ne pouvez pas récupérer.

### <a name="example"></a>Exemple

Consultez l’exemple de [CATCH](#catch).

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[CException, classe](cexception-class.md)<br/>
[CInvalidArgException, classe](cinvalidargexception-class.md)
