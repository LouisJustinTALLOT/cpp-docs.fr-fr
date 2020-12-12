---
description: 'En savoir plus sur : classe CException'
title: CException (classe)
ms.date: 11/04/2016
f1_keywords:
- CException
- AFX/CException
- AFX/CException::CException
- AFX/CException::Delete
- AFX/CException::ReportError
helpviewer_keywords:
- CException [MFC], CException
- CException [MFC], Delete
- CException [MFC], ReportError
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
ms.openlocfilehash: 39d3266817ee1be20acde0b01c7c5d1aa90313cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184658"
---
# <a name="cexception-class"></a>CException (classe)

Classe de base pour toutes les exceptions dans la bibliothèque MFC (Microsoft Foundation Class).

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CException : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CException :: CException](#cexception)|Construit un objet `CException`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CException ::D supprim](#delete)|Supprime un `CException` objet.|
|[CException :: ReportError](#reporterror)|Signale un message d’erreur dans une boîte de message à l’utilisateur.|

## <a name="remarks"></a>Notes

Étant donné que `CException` est une classe de base abstraite, vous ne pouvez pas créer `CException` d’objets directement ; vous devez créer des objets de classes dérivées. Si vous avez besoin de créer votre propre `CException` classe de style, utilisez l’une des classes dérivées listées ci-dessus comme modèle. Assurez-vous que votre classe dérivée utilise également `IMPLEMENT_DYNAMIC` .

Les classes dérivées et leurs descriptions sont répertoriées ci-dessous :

|Nom|Description|
|-|-|
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|Classe de base pour les exceptions MFC critiques pour les ressources|
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Condition d’exception d’argument non valide|
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Exception de mémoire insuffisante|
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Demande d’une opération non prise en charge|
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|Exception spécifique à l’archive|
|[CFileException](../../mfc/reference/cfileexception-class.md)|Exception spécifique au fichier|
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|Ressource Windows introuvable ou non pouvant être créée|
|[COleException](../../mfc/reference/coleexception-class.md)|Exception OLE|
|[CDBException](../../mfc/reference/cdbexception-class.md)|Exception de base de données (autrement dit, les conditions d’exception générées pour les classes de base de données MFC basées sur Open Database Connectivity)|
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|Exception OLE Dispatch (Automation)|
|[CUserException](../../mfc/reference/cuserexception-class.md)|Exception qui indique qu’une ressource est introuvable|
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|Exception d’objet d’accès aux données (autrement dit, conditions d’exception générées pour les classes DAO)|
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|Exception Internet (c’est-à-dire, conditions d’exception générées pour les classes Internet).|

Ces exceptions sont destinées à être utilisées avec les macros [lève](exception-processing.md#throw), [THROW_LAST](exception-processing.md#throw_last), [try](exception-processing.md#try), [catch](exception-processing.md#catch), [AND_CATCH](exception-processing.md#and_catch)et [END_CATCH](exception-processing.md#end_catch) . Pour plus d’informations sur les exceptions, consultez [traitement des exceptions](exception-processing.md)ou consultez l’article [gestion des exceptions (MFC)](../exception-handling-in-mfc.md).

Pour intercepter une exception spécifique, utilisez la classe dérivée appropriée. Pour intercepter tous les types d’exceptions, utilisez `CException` , puis utilisez [CObject :: IsKindOf](cobject-class.md#iskindof) pour différencier les `CException` classes dérivées de. Notez que `CObject::IsKindOf` fonctionne uniquement pour les classes déclarées avec la macro [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic) , afin de tirer parti de la vérification de type dynamique. Toute `CException` classe dérivée que vous créez doit également utiliser la `IMPLEMENT_DYNAMIC` macro.

Vous pouvez signaler des détails sur les exceptions à l’utilisateur en appelant [GetErrorMessage](cfileexception-class.md#geterrormessage) ou [ReportError](#reporterror), deux fonctions membres qui fonctionnent avec l’une des `CException` classes dérivées de.

Si une exception est interceptée par l’une des macros, l' `CException` objet est supprimé automatiquement ; ne le supprimez pas vous-même. Si une exception est interceptée à l’aide d’un **`catch`** mot clé, elle n’est pas automatiquement supprimée. Pour plus d’informations sur la suppression d’un objet exception, consultez l’article [gestion des exceptions (MFC)](../exception-handling-in-mfc.md) .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](cobject-class.md)

`CException`

## <a name="requirements"></a>Spécifications

**En-tête :** AFX. h

## <a name="cexceptioncexception"></a><a name="cexception"></a> CException :: CException

Cette fonction membre construit un `CException` objet.

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Paramètres

*b_AutoDelete*<br/>
Spécifiez TRUE si la mémoire de l' `CException` objet a été allouée sur le tas. Cela entraîne la suppression de l' `CException` objet lorsque la `Delete` fonction membre est appelée pour supprimer l’exception. Spécifiez FALSe si l' `CException` objet se trouve sur la pile ou s’il s’agit d’un objet global. Dans ce cas, l' `CException` objet n’est pas supprimé lorsque la `Delete` fonction membre est appelée.

### <a name="remarks"></a>Notes

Normalement, vous n’avez jamais besoin d’appeler ce constructeur directement. Une fonction qui lève une exception doit créer une instance d’une `CException` classe dérivée de et appeler son constructeur, ou elle doit utiliser l’une des fonctions de levée MFC, telles que [AfxThrowFileException](exception-processing.md#afxthrowfileexception), pour lever un type prédéfini. Cette documentation n’est fournie qu’à des fins d’exhaustivité.

## <a name="cexceptiondelete"></a><a name="delete"></a> CException ::D supprim

Cette fonction vérifie si l' `CException` objet a été créé sur le tas et, si tel est le cas, il appelle l' **`delete`** opérateur sur l’objet.

```cpp
void Delete();
```

### <a name="remarks"></a>Notes

Lors de la suppression d’un `CException` objet, utilisez la `Delete` fonction membre pour supprimer l’exception. N’utilisez pas l' **`delete`** opérateur directement, car il `CException` peut s’agir d’un objet global ou créé sur la pile.

Vous pouvez spécifier si l’objet doit être supprimé lors de la construction de l’objet. Pour plus d’informations, consultez [CException :: CException](#cexception).

Vous devez appeler uniquement `Delete` si vous utilisez le **`try`** -  **`catch`** mécanisme C++. Si vous utilisez les macros MFC **try** et **catch**, ces macros appellent automatiquement cette fonction.

### <a name="example"></a>Exemple

```cpp
CFile* pFile = NULL;
// Constructing a CFile object with this override may throw
// a CFile exception, and won't throw any other exceptions.
// Calling CString::Format() may throw a CMemoryException,
// so we have a catch block for such exceptions, too. Any
// other exception types this function throws will be
// routed to the calling function.
// Note that this example performs the same actions as the
// example for CATCH, but uses C++ try/catch syntax instead
// of using the MFC TRY/CATCH macros. This sample must use
// CException::Delete() to delete the exception objects
// before closing the catch block, while the CATCH example
// implicitly performs the deletion via the macros.
try
{
   pFile = new CFile(_T("C:\\WINDOWS\\SYSTEM.INI"),
      CFile::modeRead | CFile::shareDenyNone);
   ULONGLONG ullLength = pFile->GetLength();
   CString str;
   str.Format(_T("Your SYSTEM.INI file is %u bytes long."), ullLength);
   AfxMessageBox(str);
}
catch(CFileException* pEx)
{
   // Simply show an error message to the user.
   pEx->ReportError();
   pEx->Delete();
}
catch(CMemoryException* pEx)
{
   // We can't recover from this memory exception, so we'll
   // just terminate the app without any cleanup. Normally, an
   // an application should do everything it possibly can to
   // clean up properly and _not_ call AfxAbort().
   pEx->Delete();
   AfxAbort();
}
// If an exception occurrs in the CFile constructor,
// the language will free the memory allocated by new
// and will not complete the assignment to pFile.
// Thus, our clean-up code needs to test for NULL.
if (pFile != NULL)
{
   pFile->Close();
   delete pFile;
}
```

## <a name="cexceptionreporterror"></a><a name="reporterror"></a> CException :: ReportError

Appelez cette fonction membre pour signaler à l’utilisateur le texte d’erreur dans une boîte de message.

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>Paramètres

*nType*<br/>
Spécifie le style de la boîte de message. Applique une combinaison de [styles de boîte de message](styles-used-by-mfc.md#message-box-styles) à la zone. Si vous ne spécifiez pas ce paramètre, la valeur par défaut est MB_OK.

*nMessageID*<br/>
Spécifie l’ID de ressource (entrée de table de chaînes) d’un message à afficher si l’objet exception n’a pas de message d’erreur. Si la valeur est 0, le message « aucun message d’erreur n’est disponible » s’affiche.

### <a name="return-value"></a>Valeur renvoyée

`AfxMessageBox`Valeur ; sinon, 0 s’il n’y a pas assez de mémoire pour afficher la boîte de message. Consultez [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) pour connaître les valeurs de retour possibles.

### <a name="example"></a>Exemple

Voici un exemple d’utilisation de `CException::ReportError` . Pour obtenir un autre exemple, consultez l’exemple pour [catch](exception-processing.md#catch).

```cpp
CFile fileInput;
CFileException ex;

// try to open a file for reading.
// The file will certainly not
// exist because there are too many explicit
// directories in the name.

// if the call to Open() fails, ex will be
// initialized with exception
// information.  the call to ex.ReportError() will
// display an appropriate
// error message to the user, such as
// "\Too\Many\Bad\Dirs.DAT contains an
// invalid path."  The error message text will be
// appropriate for the
// file name and error condition.

if (!fileInput.Open(_T("\\Too\\Many\\Bad\\Dirs.DAT"), CFile::modeRead, &ex))
{
  ex.ReportError();
}
else
{
  // the file was opened, so do whatever work
  // with fileInput we were planning...

  fileInput.Close();
}
```

## <a name="see-also"></a>Voir aussi

[CObject (classe)](cobject-class.md)<br/>
[Graphique hiérarchique](../hierarchy-chart.md)<br/>
[Traitement des exceptions](exception-processing.md)<br/>
[Comment faire : créer mes propres classes d’exceptions personnalisées](https://go.microsoft.com/fwlink/p/?linkid=128045)
