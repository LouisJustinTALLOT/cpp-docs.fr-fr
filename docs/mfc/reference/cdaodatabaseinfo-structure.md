---
title: CDaoDatabaseInfo, structure
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabaseInfo
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
ms.openlocfilehash: 46d8056ee4ab478b65f3ef0bd59d88bd3af9b28c
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096156"
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo, structure

La `CDaoDatabaseInfo` structure contient des informations sur un objet de base de données défini pour les objets d’accès aux données (DAO).
DAO 3,6 est la version finale et est considérée comme obsolète.

## <a name="syntax"></a>Syntaxe

```
struct CDaoDatabaseInfo
{
    CString m_strName;       // Primary
    BOOL m_bUpdatable;       // Primary
    BOOL m_bTransactions;    // Primary
    CString m_strVersion;    // Secondary
    long m_lCollatingOrder;  // Secondary
    short m_nQueryTimeout;   // Secondary
    CString m_strConnect;    // All
};
```

#### <a name="parameters"></a>Paramètres

*m_strName*<br/>
Nomme l’objet de base de données de façon unique. Pour récupérer directement cette propriété, appelez [CDaoDatabase :: GetName](../../mfc/reference/cdaodatabase-class.md#getname). Pour plus d’informations, consultez la rubrique « propriété de nom » dans l’aide de DAO.

*m_bUpdatable*<br/>
Indique si les modifications peuvent être apportées à la base de données. Pour récupérer directement cette propriété, appelez [CDaoDatabase :: CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate). Pour plus d’informations, consultez la rubrique « propriété pouvant être mise à jour » dans l’aide de DAO.

*m_bTransactions*<br/>
Indique si une source de données prend en charge les transactions (enregistrement d’une série de modifications qui peuvent être annulées ultérieurement) ou validées (enregistrées). Si une base de données est basée sur le moteur de base de données Microsoft Jet, la propriété transactions est différente de zéro et vous pouvez utiliser des transactions. D’autres moteurs de base de données peuvent ne pas prendre en charge les transactions. Pour récupérer directement cette propriété, appelez [CDaoDatabase :: CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact). Pour plus d’informations, consultez la rubrique « propriété transactions » dans l’aide de DAO.

*m_strVersion*<br/>
Indique la version du moteur de base de données Microsoft Jet. Pour récupérer directement la valeur de cette propriété, appelez la fonction membre [GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion) de l’objet de base de données. Pour plus d’informations, consultez la rubrique « propriété de version » dans l’aide de DAO.

*m_lCollatingOrder*<br/>
Spécifie la séquence de l’ordre de tri dans le texte pour la comparaison ou le tri de chaînes. Les valeurs possibles sont les suivantes :

- `dbSortGeneral`Utilisez l’ordre de tri général (anglais, français, allemand, portugais, italien et espagnol moderne).

- `dbSortArabic`Utilisez l’ordre de tri arabe.

- `dbSortCyrillic`Utilisez l’ordre de tri russe.

- `dbSortCzech`Utilisez l’ordre de tri tchèque.

- `dbSortDutch`Utilisez l’ordre de tri néerlandais.

- `dbSortGreek`Utilisez l’ordre de tri grec.

- `dbSortHebrew`Utilisez l’ordre de tri hébreu.

- `dbSortHungarian`Utilisez l’ordre de tri hongrois.

- `dbSortIcelandic`Utilisez l’ordre de tri islandais.

- `dbSortNorwdan`Utilisez l’ordre de tri norvégien ou danois.

- `dbSortPDXIntl`Utilisez l’ordre de tri Paradox international.

- `dbSortPDXNor`Utilisez l’ordre de tri norvégien ou danois Paradox.

- `dbSortPDXSwe`Utilisez l’ordre de tri Paradox suédois ou finnois.

- `dbSortPolish`Utilisez l’ordre de tri polonais.

- `dbSortSpanish`Utilisez l’ordre de tri espagnol.

- `dbSortSwedFin`Utilisez l’ordre de tri suédois ou finnois.

- `dbSortTurkish`Utilisez l’ordre de tri turc.

- `dbSortUndefined`L’ordre de tri n’est pas défini ou est inconnu.

Pour plus d’informations, consultez la rubrique « Personnalisation des paramètres du Registre Windows pour l’accès aux données » dans l’aide de DAO.

*m_nQueryTimeout*<br/>
Nombre de secondes pendant lesquelles le moteur de base de données Microsoft Jet attend avant qu’une erreur de délai d’attente se produise lors de l’exécution d’une requête sur une base de données ODBC. La valeur du délai d’attente par défaut est de 60 secondes. Lorsque QueryTimeout a la valeur 0, aucun délai d’attente n’est atteint ; Cela peut entraîner le blocage du programme. Pour récupérer directement la valeur de cette propriété, appelez la fonction membre [GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout) de l’objet de base de données. Pour plus d’informations, consultez la rubrique « propriété QueryTimeout » dans l’aide de DAO.

*m_strConnect*<br/>
Fournit des informations sur la source d’une base de données ouverte. Pour plus d’informations sur les chaînes de connexion et pour plus d’informations sur la récupération directe de la valeur de cette propriété, consultez la fonction membre [CDaoDatabase :: GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) . Pour plus d’informations, consultez la rubrique « Connect Property » dans l’aide de DAO.

## <a name="remarks"></a>Notes

La base de données est un objet DAO sous-jacent à un objet MFC de la classe [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md). Les références à Primary, Secondary et All ci-dessus indiquent comment les informations sont retournées par la fonction membre [CDaoWorkspace :: GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) .

Les informations récupérées par la fonction membre [CDaoWorkspace :: GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) sont stockées `CDaoDatabaseInfo` dans une structure. Appelez `GetDatabaseInfo` pour l' `CDaoWorkspace` objet dans la collection de bases de données dans laquelle l’objet de base de données est stocké. `CDaoDatabaseInfo`définit également une `Dump` fonction membre dans les versions Debug. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoDatabaseInfo` objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdao. h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace, classe](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase, classe](../../mfc/reference/cdaodatabase-class.md)
