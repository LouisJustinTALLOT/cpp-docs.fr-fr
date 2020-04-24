---
title: Classe CException
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
ms.openlocfilehash: 93901f6f92ee79bd893b2ec0d1e341e77749d951
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753181"
---
# <a name="cexception-class"></a>Classe CException

Classe de base pour toutes les exceptions dans la bibliothèque MFC (Microsoft Foundation Class).

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CException : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CException::CException](#cexception)|Construit un objet `CException`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CException::Delete](#delete)|Supprime un `CException` objet.|
|[CException::ReportError](#reporterror)|Signale un message d’erreur dans une boîte de message à l’utilisateur.|

## <a name="remarks"></a>Notes

Parce `CException` que c’est une `CException` classe de base abstraite que vous ne pouvez pas créer des objets directement; vous devez créer des objets de classes dérivées. Si vous avez besoin `CException`de créer votre propre classe de style, utilisez l’une des classes dérivées énumérées ci-dessus comme un modèle. Assurez-vous que votre `IMPLEMENT_DYNAMIC`classe dérivée utilise également .

Les classes dérivées et leurs descriptions sont énumérées ci-dessous :

|||
|-|-|
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|Une classe de base pour les exceptions MFC critiques en matière de ressources|
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Condition d’exception d’argument invalide|
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Exception hors mémoire|
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Demande d’une opération non étayée|
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|Exception spécifique aux archives|
|[CFileException](../../mfc/reference/cfileexception-class.md)|Exception spécifique au fichier|
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|Ressource Windows non trouvée ou non crédable|
|[COleException](../../mfc/reference/coleexception-class.md)|Exception OLE|
|[CDBException](../../mfc/reference/cdbexception-class.md)|Exception de base de données (c’est-à-dire les conditions d’exception qui se présentent pour les classes de base de données MFC basées sur la connectivité open Database)|
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|Exception de répartition OLE (automatisation)|
|[CUserException](../../mfc/reference/cuserexception-class.md)|Exception qui indique qu’une ressource n’a pas pu être trouvée|
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|Exception d’objet d’accès aux données (c’est-à-dire les conditions d’exception qui se présentent pour les classes DAO)|
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|Exception Internet (c’est-à-dire les conditions d’exception qui se présentent pour les classes Internet).|

Ces exceptions sont destinées à être utilisées avec le [THROW](exception-processing.md#throw), [THROW_LAST](exception-processing.md#throw_last), [essayez,](exception-processing.md#try) [attraper](exception-processing.md#catch), [and_catch](exception-processing.md#and_catch), et [end_catch](exception-processing.md#end_catch) macros. Pour plus d’informations sur les exceptions, voir [Traitement d’exception](exception-processing.md), ou voir l’article [Exception Handling (MFC)](../exception-handling-in-mfc.md).

Pour obtenir une exception spécifique, utilisez la classe dérivée appropriée. Pour attraper tous les `CException`types d’exceptions, utilisez, puis utilisez [CObject::IsKindOf](cobject-class.md#iskindof) pour différencier entre les `CException`classes dérivées. Notez `CObject::IsKindOf` que fonctionne uniquement pour les classes déclarées avec le [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic) macro, afin de profiter de la vérification de type dynamique. Toute `CException`classe dérivée que vous `IMPLEMENT_DYNAMIC` créez devrait utiliser la macro, aussi.

Vous pouvez signaler des détails sur les exceptions à l’utilisateur en appelant [GetErrorMessage](cfileexception-class.md#geterrormessage) ou [ReportError](#reporterror), deux fonctions membres qui fonctionnent avec l’une des `CException`classes dérivées.

Si une exception est capturée par `CException` l’une des macros, l’objet est supprimé automatiquement ; ne le supprimez pas vous-même. Si une exception est détectée à l’aide d’un mot clé **de capture,** elle n’est pas automatiquement supprimée. Voir l’article [Exception Handling (MFC)](../exception-handling-in-mfc.md) pour plus d’informations sur le moment de supprimer un objet d’exeption.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](cobject-class.md)

`CException`

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="cexceptioncexception"></a><a name="cexception"></a>CException::CException

Cette fonction de `CException` membre construit un objet.

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Paramètres

*b_AutoDelete*<br/>
Spécifiez VRAI `CException` si la mémoire de l’objet a été allouée sur le tas. Cela entraînera `CException` la suppression de l’objet lorsque la fonction du `Delete` membre est appelée à supprimer l’exception. Spécifiez FALSE si l’objet `CException` est sur la pile ou est un objet global. Dans ce cas, l’objet `CException` ne `Delete` sera pas supprimé lorsque la fonction du membre est appelée.

### <a name="remarks"></a>Notes

Normalement, vous n’auriez jamais besoin d’appeler ce constructeur directement. Une fonction qui jette une exception devrait `CException`créer une instance d’une classe dérivée et appeler son constructeur, ou elle devrait utiliser l’une des fonctions de lancement MFC, telles que [AfxThrowFileException](exception-processing.md#afxthrowfileexception), pour lancer un type prédéfini. Cette documentation n’est fournie que pour l’exhaustivité.

## <a name="cexceptiondelete"></a><a name="delete"></a>CException::Delete

Cette fonction vérifie si `CException` l’objet a été créé sur le tas, et si oui, il appelle l’opérateur **de suppression** sur l’objet.

```cpp
void Delete();
```

### <a name="remarks"></a>Notes

Lors de la `CException` suppression d’un objet, utilisez la `Delete` fonction membre pour supprimer l’exception. N’utilisez pas directement l’opérateur **de suppression,** car l’objet `CException` peut être un objet global ou avoir été créé sur la pile.

Vous pouvez spécifier si l’objet doit être supprimé lorsque l’objet est construit. Pour plus d’informations, voir [CException:CException](#cexception).

Vous n’avez `Delete` qu’à appeler que si vous utilisez le mécanisme de**capture** **d’essai**- de C. Si vous utilisez les macros MFC **TRY** et **CATCH**, alors ces macros appelleront automatiquement cette fonction.

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

## <a name="cexceptionreporterror"></a><a name="reporterror"></a>CException::ReportError

Appelez cette fonction de membre pour signaler le texte d’erreur dans une boîte de message à l’utilisateur.

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>Paramètres

*nType*<br/>
Spécifie le style de la boîte à messages. Appliquez n’importe quelle combinaison des [styles de boîte de message](styles-used-by-mfc.md#message-box-styles) à la boîte. Si vous ne spécifiez pas ce paramètre, la valeur par défaut est MB_OK.

*nMessageID (en)*<br/>
Spécifie l’ID de ressource (entrée de table de chaîne) d’un message à afficher si l’objet d’exception n’a pas de message d’erreur. Si 0, le message "Aucun message d’erreur n’est disponible" est affiché.

### <a name="return-value"></a>Valeur de retour

Une `AfxMessageBox` valeur; sinon 0 s’il n’y a pas assez de mémoire pour afficher la boîte de message. Voir [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) pour les valeurs de retour possibles.

### <a name="example"></a>Exemple

Voici un exemple de `CException::ReportError`l’utilisation de . Pour un autre exemple, voir l’exemple pour [CATCH](exception-processing.md#catch).

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

[Classe CObject](cobject-class.md)<br/>
[Graphique hiérarchique](../hierarchy-chart.md)<br/>
[Traitement des exceptions](exception-processing.md)<br/>
[Comment puis-je : Créer mes propres classes d’exception personnalisées](https://go.microsoft.com/fwlink/p/?linkid=128045)
