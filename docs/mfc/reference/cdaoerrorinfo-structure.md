---
title: CDaoErrorInfo, structure
ms.date: 09/17/2019
f1_keywords:
- CDaoErrorInfo
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
ms.openlocfilehash: 8d731c8e8bea1adc850ab3c00c7688b9f8c9b819
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304223"
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo, structure

La structure `CDaoErrorInfo` contient des informations sur un objet d’erreur défini pour les objets d’accès aux données (DAO). DAO 3,6 est la version finale et est considéré comme obsolète.

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

*m_lErrorCode*<br/>
Code d’erreur DAO numérique. Consultez la rubrique « Erreurs d’accès aux données récupérables » dans l’aide de DAO.

*m_strSource*<br/>
Nom de l’objet ou de l’application qui a généré l’erreur à l’origine. La propriété source spécifie une expression de chaîne représentant l’objet qui a généré l’erreur à l’origine. l’expression est généralement le nom de la classe de l’objet. Pour plus d’informations, consultez la rubrique « propriété source » dans l’aide de DAO.

*m_strDescription*<br/>
Chaîne descriptive associée à une erreur. Pour plus d’informations, consultez la rubrique « propriété Description » dans l’aide de DAO.

*m_strHelpFile*<br/>
Chemin d’accès complet à un fichier d’aide Microsoft Windows. Pour plus d’informations, consultez la rubrique « Propriétés HelpContext, HelpFile » dans l’aide de DAO.

*m_lHelpContext*<br/>
ID de contexte pour une rubrique dans un fichier d’aide Microsoft Windows. Pour plus d’informations, consultez la rubrique « Propriétés HelpContext, HelpFile » dans l’aide de DAO.

## <a name="remarks"></a>Notes

MFC n’encapsule pas les objets d’erreur DAO dans une classe. Au lieu de cela, la classe [CDaoException](../../mfc/reference/cdaoexception-class.md) fournit une interface pour accéder à la collection Errors contenue dans l’objet DAO `DBEngine`, l’objet qui contient également tous les espaces de travail. Quand une opération DAO MFC lève un objet `CDaoException` que vous interceptez, MFC remplit une structure `CDaoErrorInfo` et la stocke dans le membre [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) de l’objet exception. (Si vous choisissez d’appeler DAO directement, vous devez appeler la fonction membre [GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) de l’objet exception vous-même pour remplir `m_pErrorInfo`.)

Pour plus d’informations sur la gestion des erreurs DAO, consultez l’article [exceptions : exceptions de base de données](../../mfc/exceptions-database-exceptions.md). Pour obtenir des informations connexes, consultez la rubrique « objet d’erreur » dans l’aide de DAO.

Les informations récupérées par la fonction membre [CDaoException :: GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) sont stockées dans une structure `CDaoErrorInfo`. Examinez le membre de données [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) à partir d’un objet `CDaoException` que vous interceptez dans un gestionnaire d'exceptions, ou appelez `GetErrorInfo` à partir d’un objet `CDaoException` que vous créez explicitement afin de vérifier les erreurs qui se sont produites pendant un appel direct aux interfaces DAO. `CDaoErrorInfo` définit également une fonction membre `Dump` dans les versions Debug. Vous pouvez utiliser `Dump` pour vider le contenu d’un objet `CDaoErrorInfo`.

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdao. h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoException, classe](../../mfc/reference/cdaoexception-class.md)
