---
title: CException (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CException
- AFX/CException
- AFX/CException::CException
- AFX/CException::Delete
- AFX/CException::ReportError
dev_langs:
- C++
helpviewer_keywords:
- CException [MFC], CException
- CException [MFC], Delete
- CException [MFC], ReportError
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a152c55944fca5fa858c148c009ef6301ff0f762
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368031"
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
|[CException::CException](#cexception)|Construit un objet `CException`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CException::Delete](#delete)|Supprime un `CException` objet.|  
|[CException::ReportError](#reporterror)|Signale un message d’erreur dans une boîte de message à l’utilisateur.|  
  
## <a name="remarks"></a>Notes  
 Étant donné que `CException` est une classe de base abstraite, vous ne pouvez pas créer `CException` objets directement ; vous devez créer les objets des classes dérivées. Si vous avez besoin créer vos propres `CException`-classe de style, utilisez une des classes dérivées répertoriées ci-dessus en tant que modèle. Assurez-vous que votre classe dérivée utilise également `IMPLEMENT_DYNAMIC`.  
  
 Les classes dérivées et leurs descriptions sont répertoriées ci-dessous :  
  
|||  
|-|-|  
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|Classe de base pour les exceptions MFC critiques de ressources|  
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Condition d’exception d’argument non valide|  
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Exception de mémoire insuffisante|  
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Demande d’une opération non prise en charge|  
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|Exception spécifiques à l’archive|  
|[CFileException](../../mfc/reference/cfileexception-class.md)|Exception de fichier spécifiques|  
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|Ressource Windows introuvable ou ne peut pas être créé|  
|[COleException](../../mfc/reference/coleexception-class.md)|Exception OLE|  
|[CDBException](../../mfc/reference/cdbexception-class.md)|Exception de base de données (autrement dit, conditions d’exception résultant pour les classes de base de données MFC basées sur Open Database Connectivity)|  
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|Exception de distribution (automation) OLE|  
|[CUserException](../../mfc/reference/cuserexception-class.md)|Exception qui indique qu’une ressource est introuvable|  
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|Exception d’objet (autrement dit, conditions d’exception résultant pour les classes DAO) d’accès aux données|  
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|Exception d’Internet (autrement dit, conditions d’exception résultant pour les classes Internet).|  
  
 Ces exceptions sont destinées à être utilisés avec la [lever](exception-processing.md#throw), [THROW_LAST](exception-processing.md#throw_last), [essayez](exception-processing.md#try), [catch](exception-processing.md#catch), [and_catch](exception-processing.md#and_catch), et [end_catch](exception-processing.md#end_catch) macros. Pour plus d’informations sur les exceptions, consultez [Exception traitement](exception-processing.md), ou consultez l’article [la gestion des exceptions (MFC)](../exception-handling-in-mfc.md).  
  
 Pour intercepter une exception spécifique, utilisez la classe dérivée appropriée. Pour intercepter tous les types d’exceptions, utilisez `CException`, puis utilisez [CObject::IsKindOf](cobject-class.md#iskindof) pour différencier les `CException`-classes dérivées. Notez que `CObject::IsKindOf` s’applique uniquement aux classes déclarées avec le [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic) macro, pour tirer parti de la vérification de type dynamique. N’importe quel `CException`-classe dérivée que vous créez doit utiliser le `IMPLEMENT_DYNAMIC` macro, trop.  
  
 Vous pouvez signaler des informations sur les exceptions à l’utilisateur en appelant [GetErrorMessage](cfileexception-class.md#geterrormessage) ou [ReportError](#reporterror), deux qui fonctionnent avec les fonctions de membres `CException`de classes dérivées.  
  
 Si une exception est interceptée par une des macros, le `CException` objet est automatiquement supprimé ; ne le supprimez pas vous-même. Si une exception est interceptée à l’aide un **catch** (mot clé), il n’est pas supprimé automatiquement. Consultez l’article [la gestion des exceptions (MFC)](../exception-handling-in-mfc.md) pour plus d’informations sur la façon de supprimer un objet d’exception.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](cobject-class.md)  
  
 `CException`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afx.h  
  
##  <a name="cexception"></a>  CException::CException  
 Cette fonction membre construit un `CException` objet.  
  
```  
explicit CException(BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Paramètres  
 *b_AutoDelete*  
 Spécifiez **TRUE** si la mémoire pour le `CException` objet a été alloué sur le tas. Cela entraîne le `CException` objet doit être supprimé quand le **supprimer** fonction membre est appelée pour supprimer l’exception. Spécifiez **FALSE** si le `CException` objet est sur la pile ou est un objet global. Dans ce cas, le `CException` objet ne sera pas supprimé lorsque la **supprimer** fonction membre est appelée.  
  
### <a name="remarks"></a>Notes  
 Vous devez normalement jamais appeler ce constructeur directement. Une fonction qui lève une exception doit créer une instance d’un `CException`-classe dérivée et appeler son constructeur, ou il doit utiliser un des MFC lever les fonctions, telles que [AfxThrowFileException](exception-processing.md#afxthrowfileexception), lever un type prédéfini. Cette documentation est fournie uniquement par souci d’exhaustivité.  
  
##  <a name="delete"></a>  CException::Delete  
 Cette fonction vérifie si le **CException** objet a été créé sur le tas, et si tel est le cas, il appelle la **supprimer** opérateur sur l’objet.  
  
```  
void Delete();
```  
  
### <a name="remarks"></a>Notes  
 Lorsque vous supprimez un **CException** de l’objet, utilisez le **supprimer** fonction membre à supprimer de l’exception. N’utilisez pas le **supprimer** opérateur directement, car le `CException` objet peut être un objet global ou ont été créées sur la pile.  
  
 Vous pouvez spécifier si l’objet doit être supprimé lorsque l’objet est construit. Pour plus d’informations, consultez [CException::CException](#cexception).  
  
 Vous devez uniquement appeler **supprimer** si vous utilisez C++ **essayez**- **catch** mécanisme. Si vous utilisez les macros MFC **essayez** et **CATCH**, alors ces macros appelle automatiquement cette fonction.  
  
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
  
##  <a name="reporterror"></a>  CException::ReportError  
 Appelez cette fonction membre pour le texte d’erreur de rapport dans un message à l’utilisateur.  
  
```  
virtual int ReportError(
    UINT nType = MB_OK,  
    UINT nMessageID = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 `nType`  
 Spécifie le style de la boîte de message. Appliquer n’importe quelle combinaison de la [styles de zone de message](styles-used-by-mfc.md#message-box-styles) à la zone. Si vous ne spécifiez pas ce paramètre, la valeur par défaut est **MB_OK**.  
  
 *nMessageID*  
 Spécifie l’ID de ressource (entrée de table chaîne) d’un message à afficher si l’objet exception n’a pas d’un message d’erreur. Si 0, le message « aucun message d’erreur n’est disponible » s’affiche.  
  
### <a name="return-value"></a>Valeur de retour  
 Un `AfxMessageBox` valeur ; sinon 0 n’est pas suffisamment de mémoire pour afficher la boîte de message. Consultez [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) les valeurs de retour possibles.  
  
### <a name="example"></a>Exemple  
 Voici un exemple de l’utilisation de `CException::ReportError`. Pour un autre exemple, consultez l’exemple de [CATCH](exception-processing.md#catch).  
  
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
 [CObject (classe)](cobject-class.md)   
 [Graphique hiérarchique](../hierarchy-chart.md)   
 [Traitement des exceptions](exception-processing.md)   
 [Comment faire : créer mes propres Classes d’Exception personnalisées](http://go.microsoft.com/fwlink/p/?linkid=128045)


