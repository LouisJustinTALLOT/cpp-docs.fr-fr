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
ms.openlocfilehash: bdf9dee88c29621bdc77c83d2633d93b4b9d10a7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751615"
---
# <a name="exception-processing"></a>Traitement des exceptions

Lorsqu’un programme s’exécute, un certain nombre de conditions anormales et d’erreurs appelées « exceptions » peuvent se produire. Il peut s’agir de manquer de mémoire, d’erreurs d’allocation de ressources et de non-trouver des fichiers.

La Microsoft Foundation Class Library utilise un système de gestion des exceptions qui s’inspire étroitement de celui proposé par le comité des normes de l’ANSI pour le C. Un gestionnaire d’exception doit être mis en place avant d’appeler une fonction qui peut rencontrer une situation anormale. Si la fonction rencontre une condition anormale, elle jette une exception et le contrôle est passé au gestionnaire d’exception.

Plusieurs macros incluses dans la Bibliothèque de classe microsoft Foundation viendront mettre en place des gestionnaires d’exception. Un certain nombre d’autres fonctions mondiales aident à établir des exceptions spécialisées et à mettre fin aux programmes, si nécessaire. Ces macros et fonctions globales entrent dans les catégories suivantes :

- Macros d’exception, qui structurent votre gestionnaire d’exception.

- Fonctions de lancement d’exception), qui génèrent des exceptions de types spécifiques.

- Fonctions de résiliation, qui causent la résiliation du programme.

Pour des exemples et plus de détails, voir l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="exception-macros"></a>Macros d’exception

|||
|-|-|
|[TRY](#try)|Désigne un bloc de code pour le traitement des exceptions.|
|[catch](#catch)|Désigne un bloc de code pour attraper une exception du bloc **TRY** précédent.|
|[CATCH_ALL](#catch_all)|Désigne un bloc de code pour attraper toutes les exceptions du bloc **TRY** précédent.|
|[AND_CATCH](#and_catch)|Désigne un bloc de code pour attraper des types d’exception supplémentaires du bloc **TRY** précédent.|
|[AND_CATCH_ALL](#and_catch_all)|Désigne un bloc de code pour attraper tous les autres types d’exception supplémentaires jetés dans un bloc **TRY** précédent.|
|[END_CATCH](#end_catch)|Termine le dernier **bloc de** code CATCH ou **AND_CATCH.**|
|[END_CATCH_ALL](#end_catch_all)|Termine le dernier bloc de code **CATCH_ALL.**|
|[THROW](#throw)|Jette une exception spécifiée.|
|[THROW_LAST](#throw_last)|Jetez l’exception actuellement manipulée au prochain gestionnaire extérieur.|

### <a name="exception-throwing-functions"></a>Fonctions de lancement d’exception

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|Jette une exception d’archive.|
|[AfxThrowFileException](#afxthrowfileexception)|Jette une exception de fichier.|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|Jette une exception d’argument invalide.|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|Jette une exception de mémoire.|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|Jette une exception non soutenue.|
|[AfxThrowResourceException](#afxthrowresourceexception)|Lance une exception Windows sans découverte de ressources.|
|[AfxThrowUserException](#afxthrowuserexception)|Lance une exception dans une action de programme initiée par l’utilisateur.|

MFC fournit deux fonctions de lancement d’exception spécifiquement pour les exceptions OLE:

### <a name="ole-exception-functions"></a>Fonctions d’exception OLE

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|Jetez une exception dans une fonction d’automatisation OLE.|
|[AfxThrowOleException](#afxthrowoleexception)|Jette une exception OLE.|

Pour tenir compte des exceptions dans les `CDBException` `CDaoException`bases de données, les classes de base de données offrent deux classes d’exception et, et des fonctions globales à l’appui des types d’exception :

### <a name="dao-exception-functions"></a>Fonctions d’exception DAO

|||
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|Jetez un [CDaoException](../../mfc/reference/cdaoexception-class.md) à partir de votre propre code.|
|[AfxThrowDBException](#afxthrowdbexception)|Jetez un [CDBException](../../mfc/reference/cdbexception-class.md) à partir de votre propre code.|

MFC fournit la fonction de résiliation suivante :

### <a name="termination-functions"></a>Fonctions de terminaison

|||
|-|-|
|[AfxAbort](#afxabort)|Appelé à mettre fin à une demande lorsqu’une erreur fatale se produit.|

## <a name="try"></a><a name="try"></a>Essayer

Installe un bloc **TRY.**

```
TRY
```

### <a name="remarks"></a>Notes

Un bloc **TRY** identifie un bloc de code qui pourrait jeter des exceptions. Ces exceptions sont traitées dans les blocs **catch** et **AND_CATCH** suivants. La récursion est permise : les exceptions peuvent être passées à un bloc **TRY** externe, soit en les ignorant ou en utilisant la macro THROW_LAST. Terminez le bloc **TRY** avec un END_CATCH ou END_CATCH_ALL macro.

Pour plus d’informations, voir l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Exemple

Voir l’exemple pour [CATCH](#catch).

### <a name="requirements"></a>Spécifications

En-tête : afx.h

## <a name="catch"></a><a name="catch"></a>catch

Définit un bloc de code qui attrape le premier type d’exception jeté dans le bloc **TRY** précédent.

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Paramètres

*exception_class*<br/>
Spécifie le type d’exception à tester. Pour une liste de classes d’exception standard, voir classe [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Spécifie un nom pour un pointeur d’exception qui sera créé par la macro. Vous pouvez utiliser le nom de pointeur pour accéder à l’objet d’exception dans le bloc **CATCH.** Cette variable est déclarée pour vous.

### <a name="remarks"></a>Notes

Le code de traitement des exceptions peut interroger l’objet d’exception, le cas échéant, pour obtenir plus d’informations sur la cause spécifique de l’exception. Invoquez la macro THROW_LAST pour passer au cadre d’exception externe suivant. Terminez le bloc **TRY** avec une macro END_CATCH.

Si *exception_class* est la `CException`classe, alors tous les types d’exception seront capturés. Vous pouvez utiliser le [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) fonction membre pour déterminer quelle exception spécifique a été jeté. Une meilleure façon d’attraper plusieurs types d’exceptions est d’utiliser des déclarations séquentielles **AND_CATCH,** chacune avec un type d’exception différent.

Le pointeur d’objet d’exception est créé par la macro. Vous n’avez pas besoin de le déclarer vous-même.

> [!NOTE]
> Le bloc **CATCH** est défini comme une portée CMD délimitée par des accolades. Si vous déclarez des variables dans cette portée, elles ne sont accessibles que dans ce champ d’application. Cela s’applique également aux *exception_object_pointer_name*.

Pour plus d’informations sur les exceptions et la macro CATCH, voir l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

## <a name="catch_all"></a><a name="catch_all"></a>CATCH_ALL

Définit un bloc de code qui capture tous les types d’exception jetés dans le bloc **TRY** précédent.

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Paramètres

*exception_object_pointer_name*<br/>
Spécifie un nom pour un pointeur d’exception qui sera créé par la macro. Vous pouvez utiliser le nom de pointeur pour accéder à l’objet d’exception dans le `CATCH_ALL` bloc. Cette variable est déclarée pour vous.

### <a name="remarks"></a>Notes

Le code de traitement des exceptions peut interroger l’objet d’exception, le cas échéant, pour obtenir plus d’informations sur la cause spécifique de l’exception. Invoquez la `THROW_LAST` macro pour passer au cadre d’exception externe suivant. Si vous utilisez **CATCH_ALL**, terminez le bloc **TRY** avec une macro END_CATCH_ALL.

> [!NOTE]
> Le bloc **CATCH_ALL** est défini comme une portée Cmd délimitée par des accolades. Si vous déclarez des variables dans cette portée, elles ne sont accessibles que dans ce champ d’application.

Pour plus d’informations sur les exceptions, voir l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Exemple

Voir l’exemple pour [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="and_catch"></a><a name="and_catch"></a>AND_CATCH

Définit un bloc de code pour attraper les types d’exception supplémentaires jetés dans un bloc **TRY** précédent.

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Paramètres

*exception_class*<br/>
Spécifie le type d’exception à tester. Pour une liste de classes d’exception standard, voir classe [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Un nom pour un pointeur d’exception qui sera créé par la macro. Vous pouvez utiliser le nom de pointeur pour accéder à l’objet d’exception dans le **bloc AND_CATCH.** Cette variable est déclarée pour vous.

### <a name="remarks"></a>Notes

Utilisez la macro CATCH pour attraper un type d’exception, puis le AND_CATCH macro pour attraper chaque type ultérieur. Terminez le bloc **TRY** avec une macro END_CATCH.

Le code de traitement des exceptions peut interroger l’objet d’exception, le cas échéant, pour obtenir plus d’informations sur la cause spécifique de l’exception. Appelez la macro THROW_LAST dans le bloc **AND_CATCH** pour passer au cadre d’exception externe suivant. **AND_CATCH** marque la fin du **bloc catch** ou **AND_CATCH** précédent.

> [!NOTE]
> Le bloc **AND_CATCH** est défini comme une portée CMD (délimitée par des accolades bouclées). Si vous déclarez des variables dans cette portée, n’oubliez pas qu’elles ne sont accessibles que dans ce champ d’application. Cela s’applique également à la variable *exception_object_pointer_name.*

### <a name="example"></a>Exemple

Voir l’exemple pour [CATCH](#catch).

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="and_catch_all"></a><a name="and_catch_all"></a>AND_CATCH_ALL

Définit un bloc de code pour attraper les types d’exception supplémentaires jetés dans un bloc **TRY** précédent.

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Paramètres

*exception_object_pointer_name*<br/>
Un nom pour un pointeur d’exception qui sera créé par la macro. Vous pouvez utiliser le nom de pointeur pour accéder à l’objet d’exception dans le **bloc AND_CATCH_ALL.** Cette variable est déclarée pour vous.

### <a name="remarks"></a>Notes

Utilisez la macro **CATCH** pour attraper un type d’exception, puis le AND_CATCH_ALL macro pour attraper tous les autres types suivants. Si vous utilisez AND_CATCH_ALL, terminez le bloc **TRY** avec une macro END_CATCH_ALL.

Le code de traitement des exceptions peut interroger l’objet d’exception, le cas échéant, pour obtenir plus d’informations sur la cause spécifique de l’exception. Appelez la macro THROW_LAST dans le bloc **AND_CATCH_ALL** pour passer au cadre d’exception externe suivant. **AND_CATCH_ALL** marque la fin du **bloc catch** ou **AND_CATCH_ALL** précédent.

> [!NOTE]
> Le bloc **AND_CATCH_ALL** est défini comme une portée CMD (délimitée par des accolades). Si vous déclarez des variables dans cette portée, n’oubliez pas qu’elles ne sont accessibles que dans ce champ d’application.

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="end_catch"></a><a name="end_catch"></a>END_CATCH

Marque la fin du dernier **bloc CATCH** ou **AND_CATCH.**

```
END_CATCH
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur le END_CATCH macro, voir l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="end_catch_all"></a><a name="end_catch_all"></a>END_CATCH_ALL

Marque la fin du dernier **bloc CATCH_ALL88** ou **AND_CATCH_ALL.**

```
END_CATCH_ALL
```

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="throw-mfc"></a><a name="throw"></a>LANCER (MFC)

Jetez l’exception spécifiée.

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>Paramètres

*exception_object_pointer*<br/>
Points à un objet `CException`d’exception dérivé de .

### <a name="remarks"></a>Notes

**THROW** interrompt l’exécution du programme, passant le contrôle au bloc **CATCH** associé dans votre programme. Si vous n’avez pas fourni le bloc **CATCH,** alors le contrôle est passé à un module Microsoft Foundation Class Library qui imprime un message d’erreur et sort.

Pour plus d’informations, voir l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="throw_last"></a><a name="throw_last"></a>THROW_LAST

Jetez l’exception vers le bloc **CATCH** externe suivant.

```
THROW_LAST()
```

### <a name="remarks"></a>Notes

Cette macro vous permet de jeter une exception créée localement. Si vous essayez de lancer une exception que vous venez de prendre, il sera normalement hors de portée et être supprimé. Avec **THROW_LAST,** l’exception est transmise correctement au prochain gestionnaire **CATCH.**

Pour plus d’informations, voir l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Exemple

Voir l’exemple pour [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="afxthrowarchiveexception"></a><a name="afxthrowarchiveexception"></a>AfxThrowArchiveException

Jette une exception d’archive.

```cpp
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>Paramètres

*cause*<br/>
Spécifie un intégrant qui indique la raison de l’exception. Pour une liste des valeurs possibles, voir [CArchiveException:m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).

*lpszArchiveName (en)*<br/>
Indique une chaîne contenant le `CArchive` nom de l’objet qui a causé l’exception (si disponible).

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="afxthrowfileexception"></a><a name="afxthrowfileexception"></a>AfxThrowFileException

Jette une exception de fichier.

```cpp
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Paramètres

*cause*<br/>
Spécifie un intégrant qui indique la raison de l’exception. Pour une liste des valeurs possibles, voir [CFileException:m_cause](../../mfc/reference/cfileexception-class.md#m_cause).

*lOsError*<br/>
Contient le numéro d’erreur du système d’exploitation (si disponible) qui indique la raison de l’exception. Consultez votre manuel de système d’exploitation pour une liste de codes d’erreur.

*lpszFileName*<br/>
Indique une chaîne contenant le nom du fichier qui a causé l’exception (si disponible).

### <a name="remarks"></a>Notes

Vous êtes responsable de déterminer la cause en fonction du code d’erreur du système d’exploitation.

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="afxthrowinvalidargexception"></a><a name="afxthrowinvalidargexception"></a>AfxThrowInvalidArgException

Jette une exception d’argument invalide.

### <a name="syntax"></a>Syntaxe

```cpp
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>Notes

Cette fonction est appelée lorsque des arguments non valides sont utilisés.

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="afxthrowmemoryexception"></a><a name="afxthrowmemoryexception"></a>AfxThrowMemoryException

Jette une exception de mémoire.

```cpp
void AfxThrowMemoryException();
```

### <a name="remarks"></a>Notes

Appelez cette fonction si les appels vers des allocateurs de mémoire système sous-jacents (tels que **malloc** et la fonction [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows) échouent. Vous n’avez pas besoin de l’appeler pour **de nouvelles** parce que **nouveau** jettera une exception de mémoire automatiquement si l’allocation de mémoire échoue.

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="afxthrownotsupportedexception"></a><a name="afxthrownotsupportedexception"></a>AfxThrowNotSupportedException

Jette une exception qui est le résultat d’une demande pour une fonctionnalité non supportée.

```cpp
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="afxthrowresourceexception"></a><a name="afxthrowresourceexception"></a>AfxThrowResourceException

Jette une exception de ressources.

```cpp
void  AfxThrowResourceException();
```

### <a name="remarks"></a>Notes

Cette fonction est normalement appelée lorsqu’une ressource Windows ne peut pas être chargée.

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="afxthrowuserexception"></a><a name="afxthrowuserexception"></a>AfxThrowUserException

Jetez une exception pour arrêter une opération utilisateur final.

```cpp
void AfxThrowUserException();
```

### <a name="remarks"></a>Notes

Cette fonction est normalement `AfxMessageBox` appelée immédiatement après a signalé une erreur à l’utilisateur.

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="afxthrowoledispatchexception"></a><a name="afxthrowoledispatchexception"></a>AfxThrowOleDispatchException

Utilisez cette fonction pour jeter une exception dans une fonction d’automatisation OLE.

```cpp
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

*wCode (en)*<br/>
Un code d’erreur spécifique à votre application.

*lpszDescription*<br/>
Description verbale de l’erreur.

*nDescriptionID (en)*<br/>
Id de ressources pour la description d’erreur verbale.

*nHelpID (en)*<br/>
Un contexte d’aide pour l’aide de votre application (. HLP) fichier.

### <a name="remarks"></a>Notes

Les informations fournies à cette fonction peuvent être affichées par l’application de conduite (Microsoft Visual Basic ou une autre application client d’automatisation OLE).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="afxthrowoleexception"></a><a name="afxthrowoleexception"></a>AfxThrowOleException

Crée un objet `COleException` de type et lance une exception.

```cpp
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>Paramètres

*Sc*<br/>
Un code de statut OLE qui indique la raison de l’exception.

*Hr*<br/>
Portez-le à un code de résultat qui indique la raison de l’exception.

### <a name="remarks"></a>Notes

La version qui prend un HRESULT comme argument convertit ce code de résultat en SCODE correspondant. Pour plus d’informations sur HRESULT et SCODE, voir [Structure of COM Error Codes](/windows/win32/com/structure-of-com-error-codes) in the Windows SDK.

### <a name="requirements"></a>Spécifications

  **En-tête** afxdao.h

## <a name="afxthrowdaoexception"></a><a name="afxthrowdaoexception"></a>AfxThrowDaoException

Appelez cette fonction pour jeter une exception de type [CDaoException](../../mfc/reference/cdaoexception-class.md) à partir de votre propre code.

```cpp
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>Paramètres

*nAfxDaoError*<br/>
Une valeur d’intégration représentant un code d’erreur étendu DAO, qui peut être l’une des valeurs énumérées sous [CDaoException::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror).

*scode*<br/>
Un code d’erreur OLE de DAO, de type SCODE. Pour plus d’informations, voir [CDaoException:m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).

### <a name="remarks"></a>Notes

Le cadre `AfxThrowDaoException`appelle également . Dans votre appel, vous pouvez passer l’un des paramètres ou les deux. Par exemple, si vous souhaitez soulever l’une des erreurs définies dans **CDaoException::nAfxDaoError** mais vous ne vous souciez pas du paramètre *de scode,* passez un code valide dans le paramètre *nAfxDaoError* et acceptez la valeur par défaut pour *le scode*.

Pour plus d’informations sur les exceptions liées `CDaoException` aux classes MFC DAO, voir la classe dans ce livre et l’article [Exceptions: Database Exceptions](../../mfc/exceptions-database-exceptions.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxdb.h

## <a name="afxthrowdbexception"></a><a name="afxthrowdbexception"></a>AfxThrowDBException

Appelez cette fonction pour jeter `CDBException` une exception de type de votre propre code.

```cpp
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>Paramètres

*nRetCode (nRetCode)*<br/>
Une valeur de type RETCODE, définissant le type d’erreur qui a causé l’exception d’être jeté.

*Apb*<br/>
Un pointeur `CDatabase` sur l’objet qui représente la connexion source de données avec laquelle l’exception est associée.

*hstmt*<br/>
Une poignée ODBC HSTMT qui spécifie la poignée de déclaration à laquelle l’exception est associée.

### <a name="remarks"></a>Notes

Le cadre `AfxThrowDBException` appelle lorsqu’il reçoit un RETCODE ODBC d’un appel à une fonction API ODBC et interprète le RETCODE comme une condition exceptionnelle plutôt qu’une erreur prévisible. Par exemple, une opération d’accès aux données peut échouer en raison d’une erreur de lecture de disque.

Pour plus d’informations sur les valeurs RETCODE définies par ODBC, voir le chapitre 8, « Récupérer l’état et les informations d’erreur », dans le SDK Windows. Pour plus d’informations sur les extensions MFC à ces codes, voir classe [CDBException](../../mfc/reference/cdbexception-class.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="afxabort"></a><a name="afxabort"></a>AfxAbort

La fonction de terminaison par défaut fournie par MFC.

```cpp
void  AfxAbort();
```

### <a name="remarks"></a>Notes

`AfxAbort`est appelé à l’interne par les fonctions membres de MFC lorsqu’il y a une erreur fatale, comme une exception non-vue qui ne peut pas être traitée. Vous pouvez `AfxAbort` appeler dans le cas rare lorsque vous rencontrez une erreur catastrophique à partir de laquelle vous ne pouvez pas récupérer.

### <a name="example"></a>Exemple

Voir l’exemple pour [CATCH](#catch).

### <a name="requirements"></a>Spécifications

  **En-tête** afx.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[Classe CException](cexception-class.md)<br/>
[Classe CInvalidArgException](cinvalidargexception-class.md)
