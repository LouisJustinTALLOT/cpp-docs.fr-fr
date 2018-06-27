---
title: Classe d’exception CArchiveException | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
dev_langs:
- C++
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2763335a9165c1667160864a40200dcfd44b7f34
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953098"
---
# <a name="carchiveexception-class"></a>Classe d’exception CArchiveException
Représente une condition d’exception de sérialisation  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CArchiveException : public CException  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CArchiveException::CArchiveException](#carchiveexception)|Construit un objet `CArchiveException`.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CArchiveException::m_cause](#m_cause)|Indique la cause de l’exception.|  
|[CArchiveException::m_strFileName](#m_strfilename)|Spécifie le nom du fichier pour cette condition d’exception.|  
  
## <a name="remarks"></a>Notes  
 La `CArchiveException` classe inclut une donnée membre publique qui indique la cause de l’exception.  
  
 `CArchiveException` les objets sont construits et levées à l’intérieur de [CArchive](../../mfc/reference/carchive-class.md) fonctions membres. Vous pouvez accéder à ces objets dans l’étendue d’un **CATCH** expression. Le code d’origine est indépendant du système d’exploitation. Pour plus d’informations sur le traitement des exceptions, consultez [la gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CArchiveException`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h  
  
##  <a name="carchiveexception"></a>  CArchiveException::CArchiveException  
 Construit un `CArchiveException` objet, le stockage de la valeur *provoquer* dans l’objet.  
  
```  
CArchiveException(
    int cause = CArchiveException::none,  
    LPCTSTR lpszArchiveName = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *cause*  
 Une variable de type énuméré qui indique la raison de l’exception. Pour obtenir la liste des énumérateurs, consultez la [m_cause](#m_cause) membre de données.  
  
 *lpszArchiveName*  
 Pointe vers une chaîne contenant le nom de la `CArchive` objet qui a provoqué l’exception.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez créer un `CArchiveException` de l’objet sur le tas et lever vous-même ou laisser la fonction globale [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) gérer pour vous.  
  
 N’utilisez pas ce constructeur directement. au lieu de cela, appelez la fonction globale `AfxThrowArchiveException`.  
  
##  <a name="m_cause"></a>  CArchiveException::m_cause  
 Spécifie la cause de l’exception.  
  
```  
int m_cause;  
```  
  
### <a name="remarks"></a>Notes  
 Ce membre est une variable publique de type **int**. Ses valeurs sont définies par un `CArchiveException` type énuméré. Voici les énumérateurs et leurs significations :  
  
- **CArchiveException::none** aucune erreur ne s’est produite.  
  
- **CArchiveException::genericException** erreur non spécifiée.  
  
- **CArchiveException::readOnly** a tenté d’écrire dans une archive ouverte pour le chargement.  
  
- **CArchiveException::endOfFile** atteint fin du fichier lors de la lecture d’un objet.  
  
- **CArchiveException::writeOnly** a essayé de lire à partir d’une archive ouverte pour le stockage.  
  
- **CArchiveException::badIndex** format de fichier non valide.  
  
- **CArchiveException::badClass** a essayé de lire un objet dans un objet de type incorrect.  
  
- **CArchiveException::badSchema** a essayé de lire un objet avec une version différente de la classe.  
  
    > [!NOTE]
    >  Ces énumérateurs de cause `CArchiveException` sont distincts des énumérateurs de cause `CFileException`.  
  
    > [!NOTE]
    > **CArchiveException::generic** est déconseillée. Utilisez **genericException** à la place. Si **générique** est utilisée dans une application et généré avec/CLR, il y aura des erreurs de syntaxe qui ne sont pas faciles à déchiffrer.  
  
##  <a name="m_strfilename"></a>  CArchiveException::m_strFileName  
 Spécifie le nom du fichier pour cette condition d’exception.  
  
```  
CString m_strFileName;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CException (classe)](../../mfc/reference/cexception-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CArchive (classe)](../../mfc/reference/carchive-class.md)   
 [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)   
 [Traitement des exceptions](../../mfc/reference/exception-processing.md)

