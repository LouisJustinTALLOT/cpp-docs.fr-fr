---
title: CDaoErrorInfo, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 787e9d5ac860e283d6eacc0f22b790a6196485f4
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335566"
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo, structure
Le `CDaoErrorInfo` structure contient des informations sur un objet d’erreur défini pour les objets d’accès aux données (DAO).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CDaoErrorInfo  
{  
    long m_lErrorCode;  
    CString m_strSource;  
    CString m_strDescription;  
    CString m_strHelpFile;  
    long m_lHelpContext;  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 *m_lErrorCode*  
 Un code d’erreur numérique DAO. Consultez la rubrique « Erreurs d’accès données récupérables » dans l’aide de DAO.  
  
 *m_strSource*  
 Le nom de l’objet ou l’application qui a généré l’erreur. La propriété Source spécifie une expression de chaîne représentant l’objet qui a généré l’erreur ; l’expression est généralement nom de classe. l’objet Pour plus d’informations, consultez la rubrique « Propriété de la Source » dans l’aide de DAO.  
  
 *m_strDescription*  
 Une chaîne descriptive associée à une erreur. Pour plus d’informations, consultez la rubrique « Propriété Description » dans l’aide de DAO.  
  
 *m_strHelpFile*  
 Un chemin d’accès qualifié complet à un fichier d’aide de Microsoft Windows. Pour plus d’informations, consultez la rubrique « HelpContext, HelpFile, propriétés » dans l’aide de DAO.  
  
 *m_lHelpContext*  
 Un ID de contexte pour une rubrique dans un fichier d’aide de Microsoft Windows. Pour plus d’informations, consultez la rubrique « HelpContext, HelpFile, propriétés » dans l’aide de DAO.  
  
## <a name="remarks"></a>Notes  
 MFC n’encapsule pas les objets d’erreur DAO dans une classe. Au lieu de cela, le [CDaoException](../../mfc/reference/cdaoexception-class.md) classe fournit une interface pour accéder à la collection d’erreurs contenue dans le DAO `DBEngine` objet, l’objet qui contient également tous les espaces de travail. Lorsqu’une opération DAO MFC lève une `CDaoException` de l’objet que vous interceptez, MFC remplit un `CDaoErrorInfo` structure et le stocke dans l’objet exception [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) membre. (Si vous choisissez d’appeler DAO directement, vous devez appeler l’objet exception [GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) fonction membre vous-même pour remplir `m_pErrorInfo`.)  
  
 Pour plus d’informations sur la gestion des erreurs DAO, consultez l’article [Exceptions : Exceptions de base de données](../../mfc/exceptions-database-exceptions.md). Pour plus d’informations, consultez la rubrique « Objet d’erreur » dans l’aide de DAO.  
  
 Les informations récupérées par le [CDaoException::GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) fonction membre est stockée dans un `CDaoErrorInfo` structure. Examiner le [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) membre de données à partir d’un `CDaoException` objet que vous interceptez dans un gestionnaire d’exceptions, ou un appel `GetErrorInfo` à partir d’un `CDaoException` objet que vous créez explicitement afin de vérifier les erreurs qui peuvent avoir s’est produite lors d’un appel direct aux interfaces DAO. `CDaoErrorInfo` définit également un `Dump` génère de la fonction membre en mode de débogage. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoErrorInfo` objet.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdao.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoException, classe](../../mfc/reference/cdaoexception-class.md)
