---
title: CDaoTableDefInfo, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoTableDefInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoTableDefInfo structure [MFC]
- DAO (Data Access Objects), TableDefs collection
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 80c1422c4d0e45599ca8bc2e9c86a4263b8ac9b6
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955607"
---
# <a name="cdaotabledefinfo-structure"></a>CDaoTableDefInfo, structure
Le `CDaoTableDefInfo` structure contient des informations sur un objet tabledef défini pour les objets d’accès aux données (DAO).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CDaoTableDefInfo  
{  
    CString m_strName;               // Primary  
    BOOL m_bUpdatable;               // Primary  
    long m_lAttributes;              // Primary  
    COleDateTime m_dateCreated;      // Secondary  
    COleDateTime m_dateLastUpdated;  // Secondary  
    CString m_strSrcTableName;       // Secondary  
    CString m_strConnect;            // Secondary  
    CString m_strValidationRule;     // All  
    CString m_strValidationText;     // All  
    long m_lRecordCount;             // All  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 *m_strName*  
 Identifiant de manière unique l’objet tabledef. Pour récupérer la valeur de cette propriété directement, appelez l’objet tabledef [GetName](../../mfc/reference/cdaotabledef-class.md#getname) fonction membre. Pour plus d’informations, consultez la rubrique « Nom de propriété » dans l’aide de DAO.  
  
 *m_bUpdatable*  
 Indique si les modifications peuvent être apportées à la table. La méthode rapide pour déterminer si une table est modifiable consiste à ouvrir un `CDaoTableDef` pour la table et appeler l’objet [CanUpdate](../../mfc/reference/cdaotabledef-class.md#canupdate) fonction membre. `CanUpdate` Retourne toujours la valeur différente de zéro (**TRUE**) pour un objet tabledef nouvellement créé et la valeur 0 (**FALSE**) pour un objet tabledef attaché. Un nouvel objet tabledef peut être ajouté uniquement à une base de données pour laquelle l’utilisateur actuel a l’autorisation d’écriture. Si la table contient uniquement des champs assimilables, `CanUpdate` retourne 0. Lorsqu’un ou plusieurs champs sont modifiables, `CanUpdate` retourne différente de zéro. Vous pouvez modifier que les champs modifiables. Pour plus d’informations, consultez la rubrique « Propriété actualisable » dans l’aide de DAO.  
  
 *m_lAttributes*  
 Spécifie les caractéristiques de la table représentée par l’objet tabledef. Pour récupérer les attributs en cours d’un objet tabledef, appelez sa [GetAttributes](../../mfc/reference/cdaotabledef-class.md#getattributes) fonction membre. La valeur retournée peut être une combinaison de ces constantes long (à l’aide de l’opération de bits OR (**&#124;**) (opérateur)) :  
  
- **dbAttachExclusive** pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique la table est une table attachée ouverte pour une utilisation exclusive.  
  
- **dbAttachSavePWD** pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que l’ID utilisateur et un mot de passe pour la table jointe sont enregistrés avec les informations de connexion.  
  
- **dbSystemObject** indique que la table est une table système fournie par le moteur de base de données Microsoft Jet. (En lecture seule.)  
  
- **dbHiddenObject** indique la table est une table masquée fournie par le moteur de base de données Microsoft Jet (pour une utilisation temporaire). (En lecture seule.)  
  
- **dbAttachedTable** indique la table est une table attachée à partir d’une base de données non-ODBC, par exemple une base de données de Corel.  
  
- **dbAttachedODBC** indique que la table est une table attachée à partir d’une base de données ODBC, telles que Microsoft SQL Server.  
  
 *m_dateCreated*  
 Date et heure de que création de la table. Pour récupérer directement la date de création de la table, appelez le [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) fonction membre de la `CDaoTableDef` objet associé à la table. Pour plus d’informations, consultez les commentaires ci-dessous. Pour plus d’informations, consultez la rubrique « DateCreated, LastUpdated propriétés » dans l’aide de DAO.  
  
 *m_dateLastUpdated*  
 La date et l’heure de la dernière modification apportée à la conception de la table. Pour récupérer directement la date de dernière mise à jour de la table, appelez le [GetDateLastUpdated](../../mfc/reference/cdaotabledef-class.md#getdatelastupdated) fonction membre de la `CDaoTableDef` objet associé à la table. Pour plus d’informations, consultez les commentaires ci-dessous. Pour plus d’informations, consultez la rubrique « DateCreated, LastUpdated propriétés » dans l’aide de DAO.  
  
 *m_strSrcTableName*  
 Spécifie le nom d’une table attachée, le cas échéant. Pour extraire directement le nom de la table source, appelez le [GetSourceTableName](../../mfc/reference/cdaotabledef-class.md#getsourcetablename) fonction membre de la `CDaoTableDef` objet associé à la table.  
  
 *m_strConnect*  
 Fournit des informations sur la source d’une base de données ouverte. Vous pouvez vérifier cette propriété en appelant le [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) fonction membre de votre `CDaoTableDef` objet. Pour plus d’informations sur les chaînes de connexion, consultez `GetConnect`.  
  
 *m_strValidationRule*  
 Une valeur qui valide les données dans les champs tabledef car ils sont modifiées ou ajoutées à une table. La validation est pris en charge uniquement pour les bases de données qui utilisent le moteur de base de données Microsoft Jet. Pour récupérer directement la règle de validation, appelez le [GetValidationRule](../../mfc/reference/cdaotabledef-class.md#getvalidationrule) fonction membre de la `CDaoTableDef` objet associé à la table. Pour plus d’informations, consultez la rubrique « Propriété ValidationRule » dans l’aide de DAO.  
  
 *m_strValidationText*  
 Une valeur qui spécifie le texte du message que votre application doit afficher si la règle de validation spécifiée par cette propriété n’est pas satisfaite. Pour plus d’informations, consultez la rubrique « ValidationRule Property » dans l’aide de DAO.  
  
 *m_lRecordCount*  
 Le nombre d’enregistrements accédés dans un objet tabledef. Cette propriété est en lecture seule. Pour extraire directement le nombre d’enregistrements, appelez le [GetRecordCount](../../mfc/reference/cdaotabledef-class.md#getrecordcount) fonction membre de la `CDaoTableDef` objet. La documentation de `GetRecordCount` décrit le nombre d’enregistrements supplémentaires. Notez que la récupération de ce nombre peut prendre beaucoup de temps si la table contient de nombreux enregistrements.  
  
## <a name="remarks"></a>Notes  
 Cet objet est un objet de classe [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Les références au principal, secondaire et tous les ci-dessus indiquent comment les informations sont retournées par la [GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) fonction membre dans la classe `CDaoDatabase`.  
  
 Les informations extraites par le [CDaoDatabase::GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) fonction membre est stockée dans un `CDaoTableDefInfo` structure. Appelez le `GetTableDefInfo` fonction membre de la `CDaoDatabase` objet dans dont TableDefs (collection) est stocké l’objet tabledef. `CDaoTableDefInfo` définit également un `Dump` builds de la fonction membre en mode débogage. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoTableDefInfo` objet.  
  
 Les paramètres de date et d’heure sont dérivés de l’ordinateur sur lequel la table de base a été créée ou mises à jour. Dans un environnement multi-utilisateur, les utilisateurs doivent obtenir ces paramètres directement à partir du serveur de fichiers pour éviter des incohérences entre la date et les paramètres de propriété LastUpdated.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdao.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Classe d’objet CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoDatabase, classe](../../mfc/reference/cdaodatabase-class.md)
