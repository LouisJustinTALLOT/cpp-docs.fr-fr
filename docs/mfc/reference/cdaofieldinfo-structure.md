---
title: CDaoFieldInfo, structure
ms.date: 11/04/2016
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: a5c4013a323c85ad19a3fade20f76852e053362a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275140"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo, structure

Le `CDaoFieldInfo` structure contient des informations sur un objet de champ définie pour les objets d’accès aux données (DAO).

## <a name="syntax"></a>Syntaxe

```
struct CDaoFieldInfo
{
    CString m_strName;           // Primary
    short m_nType;               // Primary
    long m_lSize;                // Primary
    long m_lAttributes;          // Primary
    short m_nOrdinalPosition;    // Secondary
    BOOL m_bRequired;            // Secondary
    BOOL m_bAllowZeroLength;     // Secondary
    long m_lCollatingOrder;      // Secondary
    CString m_strForeignName;    // Secondary
    CString m_strSourceField;    // Secondary
    CString m_strSourceTable;    // Secondary
    CString m_strValidationRule; // All
    CString m_strValidationText; // All
    CString m_strDefaultValue;   // All
};
```

#### <a name="parameters"></a>Paramètres

*m_strName*<br/>
Identifiant de manière unique l’objet de champ. Pour plus d’informations, consultez la rubrique « Propriété de nom » dans l’aide de DAO.

*m_nType*<br/>
Une valeur qui indique le type de données du champ. Pour plus d’informations, consultez la rubrique « Propriété de Type » dans l’aide de DAO. La valeur de cette propriété peut être une des opérations suivantes :

- `dbBoolean` Oui/Non, identique à la valeur TRUE/FALSE

- `dbByte` Byte

- `dbInteger` court

- `dbLong` Long

- `dbCurrency` Devise ; classe MFC de voir [COleCurrency](../../mfc/reference/colecurrency-class.md)

- `dbSingle` Unique

- `dbDouble` Double

- `dbDate` Date/heure ; classe MFC de voir [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText` Texte ; classe MFC de voir [CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary` Binaire longue (objet OLE) ; Vous souhaiterez peut-être utiliser la classe MFC [CByteArray](../../mfc/reference/cbytearray-class.md) au lieu de la classe `CLongBinary` comme `CByteArray` est plus riche et plus facile à utiliser.

- `dbMemo` Mémo ; classe MFC de voir `CString`

- `dbGUID` Un identificateur global Unique identificateur/universellement Unique utilisé avec les appels de procédure distante. Pour plus d’informations, consultez la rubrique « Propriété de Type » dans l’aide de DAO.

> [!NOTE]
>  N’utilisez pas de types de données de chaîne pour les données binaires. Ainsi, vos données à passer à la couche de traduction Unicode/ANSI, ce qui entraîne une surcharge accrue et inattendue éventuellement la traduction.

*m_lSize*<br/>
Une valeur qui indique la taille maximale, en octets, d’un objet de champ DAO qui contient du texte ou la taille fixe d’un objet de champ qui contient le texte ou des valeurs numériques. Pour plus d’informations, consultez la rubrique « Propriété de taille » dans l’aide de DAO. Tailles peuvent prendre la valeur de l’une des valeurs suivantes :

|Type|Taille (octets)|Description|
|----------|--------------------|-----------------|
|`dbBoolean`|1 octet|Oui/non (identique à la valeur True/False)|
|`dbByte`|1|Byte|
|`dbInteger`|2|Entier|
|`dbLong`|4|Longue|
|`dbCurrency`|8|Devise ([COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Single|
|`dbDouble`|8|Double|
|`dbDate`|8|Date/heure ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Texte ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Binaire longue (objet OLE ; [CByteArray](../../mfc/reference/cbytearray-class.md); utilisez à la place de `CLongBinary`)|
|`dbMemo`|0|Mémo ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|Un identificateur global Unique identificateur/universellement Unique utilisé avec les appels de procédure distante.|

*m_lAttributes*<br/>
Spécifie les caractéristiques d’un objet de champ contenues par un objet tabledef, recordset, querydef ou objet index. La valeur retournée peut être une somme de ces constantes, créé avec le C++ au niveau du bit OR (**&#124;**) opérateur :

- `dbFixedField` La taille du champ est fixe (valeur par défaut pour les champs numériques).

- `dbVariableField` La taille du champ est variable (uniquement pour les champs de texte).

- `dbAutoIncrField` La valeur du champ pour les nouveaux enregistrements est automatiquement incrémentée d’un entier long unique qui ne peut pas être modifié. Prise en charge uniquement pour les tables de base de données Microsoft Jet.

- `dbUpdatableField` La valeur du champ peut être modifiée.

- `dbDescending` Le champ est trié dans l’ordre décroissant (Z - A ou 0-100) ordre (s’applique uniquement à un objet de champ dans une collection de champs d’un objet index ; dans MFC, les objets sont eux-mêmes contenus dans les objets tabledef des index). Si vous omettez cette constante, le champ est trié dans l’ordre croissant (A - Z ou 0 - 100) ordre (par défaut).

Lorsque vous vérifiez le paramètre de cette propriété, vous pouvez utiliser le C++ au niveau du bit- et opérateur (**&**) à tester pour un attribut spécifique. Lorsque vous définissez plusieurs attributs, vous pouvez les combiner en combinant les constantes appropriées avec l’opération de bits OR (**&#124;**) opérateur. Pour plus d’informations, consultez la rubrique « Propriété des attributs » dans l’aide de DAO.

*m_nOrdinalPosition*<br/>
Une valeur qui spécifie l’ordre numérique dans lequel vous voulez un champ représenté par un objet de champ DAO à afficher par rapport à d’autres champs. Vous pouvez définir cette propriété avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield). Pour plus d’informations, consultez la rubrique « Propriété OrdinalPosition » dans l’aide de DAO.

*m_bRequired*<br/>
Indique si un objet de champ DAO requiert une valeur non Null. Si cette propriété est TRUE, le champ n’autorise pas une valeur Null. Si nécessaire est définie sur FALSE, le champ peut contenir des valeurs Null, ainsi que les valeurs qui répondent aux conditions spécifiées par les paramètres de propriété AllowZeroLength et ValidationRule. Pour plus d’informations, consultez la rubrique « Propriété requise » dans l’aide de DAO. Vous pouvez définir cette propriété pour un objet tabledef avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_bAllowZeroLength*<br/>
Indique si une chaîne vide (" ») est une valeur valide d’un objet de champ DAO avec un type de données texte ou Mémo. Si cette propriété est TRUE, une chaîne vide est une valeur valide. Vous pouvez définir cette propriété sur FALSE pour vous assurer que vous ne pouvez pas utiliser une chaîne vide pour définir la valeur d’un champ. Pour plus d’informations, consultez la rubrique « Propriété AllowZeroLength » dans l’aide de DAO. Vous pouvez définir cette propriété pour un objet tabledef avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_lCollatingOrder*<br/>
Spécifie la séquence de l’ordre de tri du texte pour la comparaison de chaînes ou de tri. Pour plus d’informations, consultez la rubrique « Personnalisation de Windows Registre paramètres pour accès aux données » dans l’aide de DAO. Pour obtenir la liste des valeurs possibles retournées, consultez le `m_lCollatingOrder` membre de la [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) structure. Vous pouvez définir cette propriété pour un objet tabledef avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strForeignName*<br/>
Une valeur qui, dans une relation, spécifie le nom de l’objet DAO du champ dans une table étrangère qui correspond à un champ dans une table primaire. Pour plus d’informations, consultez la rubrique « Propriété ForeignName » dans l’aide de DAO.

*m_strSourceField*<br/>
Indique le nom du champ qui est la source d’origine des données pour un objet de champ DAO contenu par un tabledef, un jeu d’enregistrements ou un objet querydef. Cette propriété indique le nom de champ d’origine associé à un objet de champ. Par exemple, vous pouvez utiliser cette propriété pour déterminer la source d’origine des données dans un champ de requête dont le nom n’est pas lié au nom du champ dans la table sous-jacente. Pour plus d’informations, consultez la rubrique « SourceField, SourceTable propriétés » dans l’aide de DAO. Vous pouvez définir cette propriété pour un objet tabledef avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strSourceTable*<br/>
Indique le nom de la table qui est la source d’origine des données pour un objet de champ DAO contenu par un tabledef, un jeu d’enregistrements ou un objet querydef. Cette propriété indique le nom de table d’origine associé à un objet de champ. Par exemple, vous pouvez utiliser cette propriété pour déterminer la source d’origine des données dans un champ de requête dont le nom n’est pas lié au nom du champ dans la table sous-jacente. Pour plus d’informations, consultez la rubrique « SourceField, SourceTable propriétés » dans l’aide de DAO. Vous pouvez définir cette propriété pour un objet tabledef avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strValidationRule*<br/>
Une valeur qui valide les données dans un champ tel qu’il est modifiée ou ajoutée à une table. Pour plus d’informations, consultez la rubrique « Propriété ValidationRule » dans l’aide de DAO. Vous pouvez définir cette propriété pour un objet tabledef avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

Pour plus d’informations sur tabledefs, consultez le `m_strValidationRule` membre de la [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) structure.

*m_strValidationText*<br/>
Une valeur qui spécifie le texte du message que votre application affiche si la valeur d’un objet de champ DAO ne satisfait pas la règle de validation spécifiée par le paramètre de propriété ValidationRule. Pour plus d’informations, consultez la rubrique « Propriété ValidationRule » dans l’aide de DAO. Vous pouvez définir cette propriété pour un objet tabledef avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strDefaultValue*<br/>
La valeur par défaut d’un objet de champ DAO. Lorsqu’un nouvel enregistrement est créé, le paramètre de propriété DefaultValue est automatiquement entré comme valeur pour le champ. Pour plus d’informations, consultez la rubrique « Propriété DefaultValue » dans l’aide de DAO. Vous pouvez définir cette propriété pour un objet tabledef avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

## <a name="remarks"></a>Notes

Les références à principal, secondaire et tous les ci-dessus indiquent comment les informations sont retournées par la `GetFieldInfo` fonction membre dans les classes [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo), [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo), et [ CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo).

Les objets de champ ne sont pas représentées par une classe MFC. Au lieu de cela, les objets DAO sous-jacent objets MFC des classes suivantes contiennent des collections d’objets de champ : [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), et [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Ces classes fournissent des fonctions de membre pour accéder à certains des éléments individuels des informations de champ, ou vous pouvez y accéder à la fois avec un `CDaoFieldInfo` objet en appelant le `GetFieldInfo` fonction membre de l’objet conteneur.

Outre son utilisation pour l’examen des propriétés de l’objet, vous pouvez également utiliser `CDaoFieldInfo` pour construire un paramètre d’entrée pour la création de nouveaux champs dans un objet tabledef. Options plus simples sont disponibles pour cette tâche, mais si vous souhaitez un contrôle plus précis, vous pouvez utiliser la version de [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield) qui accepte un `CDaoFieldInfo` paramètre.

Les informations récupérées par le `GetFieldInfo` fonction membre (de la classe qui contient le champ) est stockée dans un `CDaoFieldInfo` structure. Appelez le `GetFieldInfo` fonction membre de l’objet conteneur dans dont la collection de champs est stocké l’objet de champ. `CDaoFieldInfo` définit également un `Dump` génère de la fonction membre en mode de débogage. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoFieldInfo` objet.

## <a name="requirements"></a>Spécifications

**En-tête :** afxdao.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
