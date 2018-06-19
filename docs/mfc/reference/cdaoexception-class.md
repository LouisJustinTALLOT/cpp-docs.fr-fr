---
title: Classe de CDaoException | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoException
- AFXDAO/CDaoException
- AFXDAO/CDaoException::CDaoException
- AFXDAO/CDaoException::GetErrorCount
- AFXDAO/CDaoException::GetErrorInfo
- AFXDAO/CDaoException::m_nAfxDaoError
- AFXDAO/CDaoException::m_pErrorInfo
- AFXDAO/CDaoException::m_scode
dev_langs:
- C++
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4531d63ff7047881f20368cbeaf8e5de4136bb9f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369214"
---
# <a name="cdaoexception-class"></a>Classe de CDaoException
Représente une condition d'exception résultant des classes de base de données MFC basées sur des objets d'accès aux données (DAO).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDaoException : public CException  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDaoException::CDaoException](#cdaoexception)|Construit un objet `CDaoException`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CDaoException::GetErrorCount](#geterrorcount)|Retourne le nombre d’erreurs dans la collection d’erreurs du moteur de base de données.|  
|[CDaoException::GetErrorInfo](#geterrorinfo)|Retourne des informations d’erreur sur un objet d’erreur particulier dans la collection d’erreurs.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|Contient un code d’erreur étendues pour les erreurs dans les classes DAO MFC.|  
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|Un pointeur vers un [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) objet qui contient des informations sur un objet d’erreur DAO.|  
|[CDaoException::m_scode](#m_scode)|Le [SCODE](#m_scode) valeur associée à l’erreur.|  
  
## <a name="remarks"></a>Notes  
 La classe inclut des membres de données publics que vous pouvez utiliser pour déterminer la cause de l’exception. `CDaoException` objets sont créés et levées par les fonctions membres des classes de base de données DAO.  
  
> [!NOTE]
>  Les classes de base de données DAO sont distincts des classes de base de données MFC basées sur ODBC Open Database Connectivity (). Tous les noms de classe de base de données DAO ont le préfixe « CDao ». Vous pouvez toujours accès aux sources de données ODBC avec les classes DAO. En général, les classes MFC basées sur DAO sont plus efficaces que les classes MFC basées sur ODBC ; les classes DAO peuvent accéder aux données, y compris par le biais des pilotes ODBC, via leur propre moteur de base de données. Les classes DAO prennent également en charge les opérations de langage de définition de données (DDL), telles que l’ajout de tables via les classes, sans avoir à appeler DAO directement. Pour plus d’informations sur les exceptions levées par les classes ODBC, consultez [CDBException](../../mfc/reference/cdbexception-class.md).  
  
 Vous pouvez accéder à des objets d’exception dans l’étendue d’un [CATCH](../../mfc/reference/exception-processing.md#catch) expression. Vous pouvez également lever `CDaoException` objets à partir de votre propre code avec la [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception) fonction globale.  
  
 Dans MFC, toutes les erreurs DAO sont exprimées en tant qu’exceptions, de type `CDaoException`. Lorsque vous interceptez une exception de ce type, vous pouvez utiliser `CDaoException` des fonctions membres pour récupérer les informations de tous les objets d’erreur DAO stockées dans la collection d’erreurs du moteur de base de données. Lorsqu’une erreur survient, un ou plusieurs objets d’erreur sont placés dans la collection d’erreurs. (Normalement la collection contient un seul objet erreur ; si vous utilisez une source de données ODBC, vous êtes plus susceptible de faire de plusieurs objets d’erreur.) Lorsqu’une autre opération DAO génère une erreur, la collection d’erreurs est désactivée, et l’objet d’erreur est placé dans la collection d’erreurs. Les opérations DAO qui ne génèrent pas d’une erreur n’ont aucun effet sur la collection d’erreurs.  
  
 Pour les codes d’erreur DAO, consultez le fichier DAOERR. H. Pour plus d’informations, consultez la rubrique « Erreurs d’accès aux données récupérable » dans l’aide de DAO.  
  
 Pour plus d’informations sur la gestion des exceptions dans générales, ou sur `CDaoException` , consultez les articles [la gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md) et [Exceptions : Exceptions de base de données](../../mfc/exceptions-database-exceptions.md). Le deuxième article contient un exemple de code qui illustre la gestion des exceptions dans DAO.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDaoException`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdao.h  
  
##  <a name="cdaoexception"></a>  CDaoException::CDaoException  
 Construit un objet `CDaoException`.  
  
```  
CDaoException();
```  
  
### <a name="remarks"></a>Notes  
 En règle générale, l’infrastructure crée les objets d’exception lors de son code lève une exception. Vous devez rarement construire un objet d’exception explicitement. Si vous souhaitez lever un `CDaoException` à partir de votre propre code, appelez la fonction globale [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception).  
  
 Toutefois, vous souhaiterez créer explicitement un objet d’exception si vous effectuez des appels directs vers DAO via les pointeurs d’interface DAO qui encapsulent les classes MFC. Dans ce cas, vous devrez peut-être extraire des informations d’erreur DAO. Supposons qu’une erreur se produit dans DAO lorsque vous appelez une méthode DAO via l’interface DAODatabases à la collection de bases de données d’un espace de travail.  
  
##### <a name="to-retrieve-the-dao-error-information"></a>Pour récupérer les informations d’erreur DAO  
  
1.  Construire un `CDaoException` objet.  
  
2.  Appelez l’objet d’exception [GetErrorCount](#geterrorcount) fonction membre pour déterminer le nombre d’objets erreur dans la collection d’erreurs du moteur de base de données. (Normalement une seule, sauf si vous utilisez une source de données ODBC.)  
  
3.  Appelez l’objet d’exception [GetErrorInfo](#geterrorinfo) fonction membre pour récupérer un objet d’erreur spécifique à la fois, par index dans la collection, via l’objet exception. Considérez l’objet exception en tant que proxy pour un objet d’erreur DAO.  
  
4.  Examinez actuel [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) structure `GetErrorInfo` retourne dans le [m_pErrorInfo](#m_perrorinfo) membre de données. Ses membres fournissent des informations sur l’erreur DAO.  
  
5.  Dans le cas d’une source de données ODBC, répétez les étapes 3 et 4 si nécessaire, pour plus d’objets d’erreur.  
  
6.  Si vous avez construit l’objet exception sur le tas, le supprimer avec la **supprimer** opérateur lorsque vous avez terminé.  
  
 Pour plus d’informations sur la gestion des erreurs dans les classes DAO MFC, consultez l’article [Exceptions : Exceptions de base de données](../../mfc/exceptions-database-exceptions.md).  
  
##  <a name="geterrorcount"></a>  CDaoException::GetErrorCount  
 Appelez cette fonction membre pour récupérer le nombre d’objets d’erreur DAO dans la collection d’erreurs du moteur de base de données.  
  
```  
short GetErrorCount();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’objets d’erreur DAO dans la collection d’erreurs du moteur de base de données.  
  
### <a name="remarks"></a>Notes  
 Ces informations sont utiles pour exécuter une boucle dans la collection d’erreurs pour récupérer de chacun des objets d’erreur DAO moins dans la collection. Pour récupérer un objet d’erreur par index ou par numéro d’erreur DAO, appelez le [GetErrorInfo](#geterrorinfo) fonction membre.  
  
> [!NOTE]
>  Normalement, il existe un seul objet d’erreur dans la collection d’erreurs. Si vous travaillez avec une source de données ODBC, toutefois, il peut exister plusieurs.  
  
##  <a name="geterrorinfo"></a>  CDaoException::GetErrorInfo  
 Retourne des informations d’erreur sur un objet d’erreur particulier dans la collection d’erreurs.  
  
```  
void GetErrorInfo(int nIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIndex`  
 Index des informations d’erreur dans la collection d’erreurs du moteur de base de données, pour la recherche par index.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre pour obtenir les types suivants d’informations sur l’exception :  
  
-   Code d'erreur  
  
-   Source  
  
-   Description  
  
-   Fichier d'aide  
  
-   Contexte d’aide  
  
 `GetErrorInfo` stocke les informations dans l’objet exception `m_pErrorInfo` membre de données. Pour obtenir une brève description des informations retournées, consultez [m_pErrorInfo](#m_perrorinfo). Si vous interceptez une exception de type `CDaoException` levée par MFC, la `m_pErrorInfo` membre est déjà renseigné. Si vous choisissez d’appeler DAO directement, vous devez appeler l’objet exception `GetErrorInfo` fonction membre vous-même pour remplir `m_pErrorInfo`. Pour obtenir une description plus détaillée, consultez la [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) structure.  
  
 Pour plus d’informations sur les exceptions DAO et exemple de code, consultez l’article [Exceptions : Exceptions de base de données](../../mfc/exceptions-database-exceptions.md).  
  
##  <a name="m_nafxdaoerror"></a>  CDaoException::m_nAfxDaoError  
 Contient une code d’erreur étendu de MFC.  
  
### <a name="remarks"></a>Notes  
 Ce code est fourni dans les cas où un composant spécifique des classes DAO MFC a visés.  
  
 Les valeurs possibles sont :  
  
- **NO_AFX_DAO_ERROR** opération la plus récente n’ont pas généré une erreur étendue de MFC. Toutefois, l’opération pourrait qui ont généré autres erreurs de DAO ou OLE, vérifiez donc [m_pErrorInfo](#m_perrorinfo) et éventuellement [m_scode](#m_scode).  
  
- **AFX_DAO_ERROR_ENGINE_INITIALIZATION** MFC n’a pas pu initialiser le moteur de base de données Microsoft Jet. OLE peut avoir échoué à initialiser, ou peut avoir été impossible de créer une instance de l’objet de moteur de base de données DAO. Généralement, ces problèmes suggèrent une installation incorrecte de DAO ou OLE.  
  
- **AFX_DAO_ERROR_DFX_BIND** une adresse utilisée dans un appel de fonction exchange (DFX) champs d’enregistrements DAO n’existe pas ou n’est pas valide (l’adresse n’a été pas utilisée pour lier des données). Vous avez passé une adresse incorrecte dans un appel DFX, ou l’adresse peut devenir non valide entre les opérations de DFX.  
  
- **AFX_DAO_ERROR_OBJECT_NOT_OPEN** vous avez tenté d’ouvrir un jeu d’enregistrements basé sur un objet querydef ou un objet tabledef qui n’était pas dans un état ouvert.  
  
##  <a name="m_perrorinfo"></a>  CDaoException::m_pErrorInfo  
 Contient un pointeur vers un `CDaoErrorInfo` structure qui fournit des informations sur l’objet d’erreur DAO que vous avez récupéré en dernier en appelant [GetErrorInfo](#geterrorinfo).  
  
### <a name="remarks"></a>Notes  
 Cet objet contient les informations suivantes :  
  
|CDaoErrorInfo membre|Information|Signification|  
|--------------------------|-----------------|-------------|  
|**m_lErrorCode**|Code d'erreur|Le code d’erreur DAO|  
|`m_strSource`|Source|Le nom de l’objet ou l’application qui a généré l’erreur|  
|`m_strDescription`|Description|Une chaîne descriptive associée à l’erreur|  
|`m_strHelpFile`|Fichier d’aide|Un chemin d’accès à un fichier d’aide Windows dans lequel l’utilisateur peut obtenir des informations sur le problème|  
|**m_lHelpContext**|Contexte d’aide|L’ID de contexte pour une rubrique dans le fichier d’aide de DAO|  
  
 Pour plus d’informations sur les informations contenues dans le `CDaoErrorInfo` d’objets, consultez la [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) structure.  
  
##  <a name="m_scode"></a>  CDaoException::m_scode  
 Contient une valeur de type `SCODE` qui décrit l’erreur.  
  
### <a name="remarks"></a>Notes  
 Il s’agit d’un code d’OLE. Vous devrez rarement utiliser cette valeur car, dans presque tous les cas, les informations d’erreur plus spécifiques MFC ou DAO sont disponibles dans les autres `CDaoException` membres de données.  
  
 Pour plus d’informations sur `SCODE`, consultez la rubrique [Structure of OLE Error Codes](http://msdn.microsoft.com/library/windows/desktop/ms690088) dans le Kit de développement logiciel Windows. Le `SCODE` type de données correspond à la `HRESULT` type de données.  
  
## <a name="see-also"></a>Voir aussi  
 [CException (classe)](../../mfc/reference/cexception-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CException, classe](../../mfc/reference/cexception-class.md)
