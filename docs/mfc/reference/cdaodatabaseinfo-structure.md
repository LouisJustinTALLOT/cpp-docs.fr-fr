---
title: CDaoDatabaseInfo, structure
ms.date: 11/04/2016
f1_keywords:
- CDaoDatabaseInfo
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
ms.openlocfilehash: 920301af6f660aeac010ecbf844b80ea628bbfd7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285631"
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo, structure

Le `CDaoDatabaseInfo` structure contient des informations sur un objet de base de données défini pour les objets d’accès aux données (DAO).

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
Identifiant de manière unique l’objet de base de données. Pour récupérer directement cette propriété, appelez [CDaoDatabase::GetName](../../mfc/reference/cdaodatabase-class.md#getname). Pour plus d’informations, consultez la rubrique « Propriété de nom » dans l’aide de DAO.

*m_bUpdatable*<br/>
Indique si les modifications peuvent être apportées à la base de données. Pour récupérer directement cette propriété, appelez [CDaoDatabase::CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate). Pour plus d’informations, consultez la rubrique « Propriété actualisable » dans l’aide de DAO.

*m_bTransactions*<br/>
Indique si une source de données prend en charge les transactions, l’enregistrement d’une série de modifications qui peuvent être restauration ultérieure (annulé) ou validé (enregistré). Si une base de données est basé sur le moteur de base de données Microsoft Jet, la propriété de Transactions est différent de zéro, et vous pouvez utiliser des transactions. Autres moteurs de base de données ne peuvent pas en charge les transactions. Pour récupérer directement cette propriété, appelez [CDaoDatabase::CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact). Pour plus d’informations, consultez la rubrique « Propriété de Transactions » dans l’aide de DAO.

*m_strVersion*<br/>
Indique la version du moteur de base de données Microsoft Jet. Pour récupérer la valeur de cette propriété directement, appelez l’objet de base de données [GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion) fonction membre. Pour plus d’informations, consultez la rubrique « Propriété de Version » dans l’aide de DAO.

*m_lCollatingOrder*<br/>
Spécifie la séquence de l’ordre de tri du texte pour la comparaison de chaînes ou de tri. Les valeurs possibles sont les suivantes :

- `dbSortGeneral` Utiliser l’ordre de tri Général (anglais, Français, allemand, portugais, italien et Espagnol moderne).

- `dbSortArabic` Utiliser l’ordre de tri de l’arabe.

- `dbSortCyrillic` Utiliser l’ordre de tri russe.

- `dbSortCzech` Utiliser l’ordre de tri tchèque.

- `dbSortDutch` Utiliser l’ordre de tri néerlandais.

- `dbSortGreek` Utiliser l’ordre de tri grec.

- `dbSortHebrew` Utiliser l’ordre de tri de l’hébreu.

- `dbSortHungarian` Utiliser l’ordre de tri hongrois.

- `dbSortIcelandic` Utiliser l’ordre de tri islandais.

- `dbSortNorwdan` Utiliser l’ordre de tri norvégien ou danois.

- `dbSortPDXIntl` Utiliser l’ordre de tri Paradox International.

- `dbSortPDXNor` Utilisez la couronne Paradox ou ordre de tri danoise.

- `dbSortPDXSwe` Utiliser le suédois Paradox ou ordre de tri finnois.

- `dbSortPolish` Utiliser l’ordre de tri polonais.

- `dbSortSpanish` Utiliser l’ordre de tri espagnol.

- `dbSortSwedFin` Utiliser l’ordre de tri suédois ou finnois.

- `dbSortTurkish` Utiliser l’ordre de tri turc.

- `dbSortUndefined` L’ordre de tri est inconnue ou non définie.

Pour plus d’informations, consultez la rubrique « Personnalisation de Windows Registre paramètres pour accès aux données » dans l’aide de DAO.

*m_nQueryTimeout*<br/>
Le nombre de secondes pendant lesquelles que le moteur de base de données Microsoft Jet patiente avant une erreur de délai d’expiration se produit lorsqu’une requête est exécutée sur une base de données ODBC. La valeur de délai d’expiration par défaut est de 60 secondes. Lorsque QueryTimeout est définie sur 0, aucun délai d’expiration se produit ; Cela peut provoquer le blocage du programme. Pour récupérer la valeur de cette propriété directement, appelez l’objet de base de données [GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout) fonction membre. Pour plus d’informations, consultez la rubrique « Propriété QueryTimeout » dans l’aide de DAO.

*m_strConnect*<br/>
Fournit des informations sur la source d’une base de données ouverte. Pour plus d’informations sur les chaînes de connexion et pour plus d’informations sur la récupération de la valeur de cette propriété directement, consultez le [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) fonction membre. Pour plus d’informations, consultez la rubrique « Se connecter, propriété » dans l’aide de DAO.

## <a name="remarks"></a>Notes

La base de données est un objet DAO sous-jacent d’un objet MFC de classe [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md). Les références à principal, secondaire et tous les ci-dessus indiquent comment les informations sont retournées par la [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) fonction membre.

Les informations récupérées par le [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) fonction membre est stockée dans un `CDaoDatabaseInfo` structure. Appelez `GetDatabaseInfo` pour le `CDaoWorkspace` objet dans dont la collection de bases de données est stocké l’objet de base de données. `CDaoDatabaseInfo` définit également un `Dump` génère de la fonction membre en mode de débogage. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoDatabaseInfo` objet.

## <a name="requirements"></a>Spécifications

**En-tête :** afxdao.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace, classe](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase, classe](../../mfc/reference/cdaodatabase-class.md)
