---
title: Cdaodatabaseinfo, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoDatabaseInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7121915671f6e0ab52ae66c53e5ca31fa1faec1c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352738"
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
 `m_strName`  
 Identifie l’objet de base de données. Pour extraire directement cette propriété, appelez [CDaoDatabase::GetName](../../mfc/reference/cdaodatabase-class.md#getname). Pour plus d’informations, consultez la rubrique « Nom de propriété » dans l’aide de DAO.  
  
 `m_bUpdatable`  
 Indique si les modifications peuvent être apportées à la base de données. Pour extraire directement cette propriété, appelez [CDaoDatabase::CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate). Pour plus d’informations, consultez la rubrique « Propriété actualisable » dans l’aide de DAO.  
  
 *m_bTransactions*  
 Indique si une source de données prend en charge les transactions, l’enregistrement d’une série de modifications qui peuvent être suite (annulée) ou validée (enregistré). Si une base de données est basé sur le moteur de base de données Microsoft Jet, la propriété Transactions est différente de zéro et vous pouvez utiliser des transactions. Autres moteurs de base de données ne peuvent pas en charge les transactions. Pour extraire directement cette propriété, appelez [CDaoDatabase::CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact). Pour plus d’informations, consultez la rubrique « Propriété de Transactions » dans l’aide de DAO.  
  
 *m_strVersion*  
 Indique la version du moteur de base de données Microsoft Jet. Pour récupérer la valeur de cette propriété directement, appelez l’objet de base de données [GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion) fonction membre. Pour plus d’informations, consultez la rubrique « Propriété de Version » dans l’aide de DAO.  
  
 `m_lCollatingOrder`  
 Spécifie la séquence de l’ordre de tri du texte pour la comparaison de chaînes ou de tri. Les valeurs possibles sont les suivantes :  
  
- **dbSortGeneral** utiliser l’ordre de tri Général (anglais, Français, allemand, portugais, italien et Espagnol moderne).  
  
- **dbSortArabic** utiliser l’ordre de tri arabe.  
  
- **dbSortCyrillic** utiliser l’ordre de tri russe.  
  
- **dbSortCzech** utiliser l’ordre de tri tchèque.  
  
- **dbSortDutch** utiliser l’ordre de tri néerlandais.  
  
- **dbSortGreek** utiliser l’ordre de tri grec.  
  
- **dbSortHebrew** utiliser l’ordre de tri de l’hébreu.  
  
- **dbSortHungarian** utiliser l’ordre de tri hongrois.  
  
- **dbSortIcelandic** utiliser l’ordre de tri islandais.  
  
- **dbSortNorwdan** utiliser l’ordre de tri norvégien ou danois.  
  
- **dbSortPDXIntl** utiliser l’ordre de tri Paradox International.  
  
- **dbSortPDXNor** utiliser le norvégien Paradox ou ordre de tri danois.  
  
- **dbSortPDXSwe** utiliser le suédois Paradox ou ordre de tri finnois.  
  
- **dbSortPolish** utiliser l’ordre de tri polonais.  
  
- **dbSortSpanish** utiliser l’ordre de tri espagnole.  
  
- **dbSortSwedFin** utiliser l’ordre de tri suédois ou finnois.  
  
- **dbSortTurkish** utiliser l’ordre de tri turc.  
  
- **dbSortUndefined** l’ordre de tri est inconnue ou non définie.  
  
 Pour plus d’informations, consultez la rubrique « Personnalisation de Windows Registre paramètres pour accès aux données » dans l’aide de DAO.  
  
 *m_nQueryTimeout*  
 Le nombre de secondes pendant lesquelles que le moteur de base de données Microsoft Jet patiente avant une erreur de délai d’attente se produit lorsqu’une requête est exécutée sur une base de données ODBC. La valeur de délai d’attente par défaut est 60 secondes. Lorsque la valeur QueryTimeout est 0, aucun délai d’expiration se produit ; Cela peut provoquer le blocage du programme. Pour récupérer la valeur de cette propriété directement, appelez l’objet de base de données [GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout) fonction membre. Pour plus d’informations, consultez la rubrique « Propriété QueryTimeout » dans l’aide de DAO.  
  
 `m_strConnect`  
 Fournit des informations sur la source d’une base de données ouverte. Pour plus d’informations sur les chaînes de connexion et pour plus d’informations sur la récupération de la valeur de cette propriété directement, consultez le [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) fonction membre. Pour plus d’informations, consultez la rubrique « Propriété Connect » dans l’aide de DAO.  
  
## <a name="remarks"></a>Notes  
 La base de données est un objet DAO sous-jacent d’un objet MFC de classe [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md). Les références au principal, secondaire et tous les ci-dessus indiquent comment les informations sont retournées par la [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) fonction membre.  
  
 Les informations extraites par le [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) fonction membre est stockée dans un `CDaoDatabaseInfo` structure. Appelez `GetDatabaseInfo` pour la `CDaoWorkspace` objet dans dont la collection de bases de données, l’objet de base de données est stocké. `CDaoDatabaseInfo` définit également un `Dump` builds de la fonction membre en mode débogage. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoDatabaseInfo` objet.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdao.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace (classe)](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase, classe](../../mfc/reference/cdaodatabase-class.md)
