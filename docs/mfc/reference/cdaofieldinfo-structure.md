---
title: CDaoFieldInfo, structure
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: e2638ac908e4e286530301bc913173e87008df47
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303698"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo, structure

La structure `CDaoFieldInfo` contient des informations sur un objet de champ défini pour les objets d’accès aux données (DAO).

DAO est pris en charge via Office 2013. DAO 3,6 est la version finale et est considéré comme obsolète.

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
Nomme l’objet de champ de façon unique. Pour plus d’informations, consultez la rubrique « propriété de nom » dans l’aide de DAO.

*m_nType*<br/>
Valeur qui indique le type de données du champ. Pour plus d’informations, consultez la rubrique « type Property » dans l’aide de DAO. La valeur de cette propriété peut être l’une des suivantes :

- `dbBoolean` oui/non, identique à vrai/faux

- `dbByte` octet

- `dbInteger` Short

- `dbLong` long

- `dbCurrency` la devise ; consultez MFC Class [COleCurrency](../../mfc/reference/colecurrency-class.md)

- `dbSingle` unique

- `dbDouble` double

- `dbDate` date/heure ; consultez classe MFC [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText` le texte ; consultez la classe MFC [CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary` Long Binary (objet OLE); vous souhaiterez peut-être utiliser la classe MFC [CByteArray](../../mfc/reference/cbytearray-class.md) au lieu de la classe `CLongBinary` comme `CByteArray` est plus riche et plus facile à utiliser.

- `dbMemo` MEMO ; consultez MFC Class `CString`

- `dbGUID` un identificateur global unique/identificateur unique universel utilisé avec les appels de procédure distante. Pour plus d’informations, consultez la rubrique « type Property » dans l’aide de DAO.

> [!NOTE]
>  N’utilisez pas de types de données de chaîne pour les données binaires. Cela amène vos données à traverser la couche de traduction Unicode/ANSI, ce qui entraîne une surcharge accrue et éventuellement une traduction inattendue.

*m_lSize*<br/>
Valeur qui indique la taille maximale, en octets, d’un objet de champ DAO qui contient du texte ou la taille fixe d’un objet champ qui contient du texte ou des valeurs numériques. Pour plus d’informations, consultez la rubrique « propriété de taille » dans l’aide de DAO. Les tailles peuvent être l’une des valeurs suivantes :

|Type|Taille (octets)|Description|
|----------|--------------------|-----------------|
|`dbBoolean`|1 octet|Oui/non (identique à vrai/faux)|
|`dbByte`|1|Byte|
|`dbInteger`|2|Entier|
|`dbLong`|4|long|
|`dbCurrency`|8|Devise ([COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Single|
|`dbDouble`|8|Double|
|`dbDate`|8|Date/heure ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Texte ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Long Binary (objet OLE ; [CByteArray](../../mfc/reference/cbytearray-class.md); utiliser à la place de `CLongBinary`)|
|`dbMemo`|0|Mémo ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|Identificateur global unique/identificateur unique universel utilisé avec les appels de procédure distante.|

*m_lAttributes*<br/>
Spécifie les caractéristiques d’un objet champ contenu par un objet TableDef, Recordset, querydef ou index. La valeur retournée peut être une somme de ces constantes, créée à C++ l’aide de l' **&#124;** opérateur de bits or () :

- `dbFixedField` la taille du champ est fixe (valeur par défaut pour les champs numériques).

- `dbVariableField` la taille du champ est variable (champs de texte uniquement).

- `dbAutoIncrField` la valeur de champ pour les nouveaux enregistrements est automatiquement incrémentée à un entier long unique qui ne peut pas être modifié. Pris en charge uniquement pour les tables de base de données Microsoft Jet.

- `dbUpdatableField` la valeur du champ peut être modifiée.

- `dbDescending` le champ est trié par ordre décroissant (Z-A ou 100-0) (s’applique uniquement à un objet de champ dans une collection de champs d’un objet d’index ; dans MFC, les objets d’index sont eux-mêmes contenus dans des objets TableDef). Si vous omettez cette constante, le champ est trié dans l’ordre croissant (A-Z ou 0-100) (valeur par défaut).

Lorsque vous vérifiez le paramètre de cette propriété, vous pouvez utiliser C++ l’opérateur de bits and ( **&** ) pour tester un attribut spécifique. Lors de la définition de plusieurs attributs, vous pouvez les combiner en combinant les constantes appropriées à l’aide **&#124;** de l’opérateur de bits or (). Pour plus d’informations, consultez la rubrique « propriété Attributes » dans l’aide de DAO.

*m_nOrdinalPosition*<br/>
Valeur qui spécifie l’ordre numérique dans lequel vous souhaitez qu’un champ représenté par un objet de champ DAO soit affiché par rapport à d’autres champs. Vous pouvez définir cette propriété avec [CDaoTableDef :: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield). Pour plus d’informations, consultez la rubrique « propriété OrdinalPosition » dans l’aide de DAO.

*m_bRequired*<br/>
Indique si un objet de champ DAO requiert une valeur non null. Si cette propriété a la valeur TRUE, le champ n’autorise pas de valeur null. Si Required est défini sur FALSe, le champ peut contenir des valeurs NULL, ainsi que des valeurs qui remplissent les conditions spécifiées par les paramètres de propriété AllowZeroLength et ValidationRule. Pour plus d’informations, consultez la rubrique « propriété requise » dans l’aide de DAO. Vous pouvez définir cette propriété pour un objet TableDef avec [CDaoTableDef :: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_bAllowZeroLength*<br/>
Indique si une chaîne vide ("") est une valeur valide d’un objet de champ DAO avec un type de données texte ou Mémo. Si cette propriété a la valeur TRUE, une chaîne vide est une valeur valide. Vous pouvez définir cette propriété sur FALSe pour vous assurer que vous ne pouvez pas utiliser une chaîne vide pour définir la valeur d’un champ. Pour plus d’informations, consultez la rubrique « propriété AllowZeroLength » dans l’aide de DAO. Vous pouvez définir cette propriété pour un objet TableDef avec [CDaoTableDef :: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_lCollatingOrder*<br/>
Spécifie la séquence de l’ordre de tri dans le texte pour la comparaison ou le tri de chaînes. Pour plus d’informations, consultez la rubrique « Personnalisation des paramètres du Registre Windows pour l’accès aux données » dans l’aide de DAO. Pour obtenir la liste des valeurs possibles retournées, consultez le membre `m_lCollatingOrder` de la structure [cdaodatabaseinfo,](../../mfc/reference/cdaodatabaseinfo-structure.md) . Vous pouvez définir cette propriété pour un objet TableDef avec [CDaoTableDef :: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strForeignName*<br/>
Valeur qui, dans une relation, spécifie le nom de l’objet de champ DAO dans une table étrangère qui correspond à un champ dans une table primaire. Pour plus d’informations, consultez la rubrique « propriété ForeignName » dans l’aide de DAO.

*m_strSourceField*<br/>
Indique le nom du champ qui est la source d’origine des données d’un objet de champ DAO contenu dans un objet TableDef, Recordset ou querydef. Cette propriété indique le nom de champ d’origine associé à un objet de champ. Par exemple, vous pouvez utiliser cette propriété pour déterminer la source d’origine des données dans un champ de requête dont le nom n’est pas lié au nom du champ dans la table sous-jacente. Pour plus d’informations, consultez la rubrique « SourceField, propriétés SourceTable » dans l’aide de DAO. Vous pouvez définir cette propriété pour un objet TableDef avec [CDaoTableDef :: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strSourceTable*<br/>
Indique le nom de la table qui est la source d’origine des données d’un objet de champ DAO contenu dans un objet TableDef, Recordset ou querydef. Cette propriété indique le nom de la table d’origine associé à un objet de champ. Par exemple, vous pouvez utiliser cette propriété pour déterminer la source d’origine des données dans un champ de requête dont le nom n’est pas lié au nom du champ dans la table sous-jacente. Pour plus d’informations, consultez la rubrique « SourceField, propriétés SourceTable » dans l’aide de DAO. Vous pouvez définir cette propriété pour un objet TableDef avec [CDaoTableDef :: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strValidationRule*<br/>
Valeur qui valide les données d’un champ au fur et à mesure qu’elles sont modifiées ou ajoutées à une table. Pour plus d’informations, consultez la rubrique « propriété ValidationRule » dans l’aide de DAO. Vous pouvez définir cette propriété pour un objet TableDef avec [CDaoTableDef :: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

Pour obtenir des informations connexes sur tabledefs, consultez le membre `m_strValidationRule` de la structure [CDaoTableDefInfo](../../mfc/reference/cdaotabledefinfo-structure.md) .

*m_strValidationText*<br/>
Valeur qui spécifie le texte du message affiché par votre application si la valeur d’un objet de champ DAO ne satisfait pas la règle de validation spécifiée par le paramètre de propriété ValidationRule. Pour plus d’informations, consultez la rubrique « propriété MessageSiErreur » dans l’aide de DAO. Vous pouvez définir cette propriété pour un objet TableDef avec [CDaoTableDef :: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strDefaultValue*<br/>
Valeur par défaut d’un objet de champ DAO. Lorsqu’un nouvel enregistrement est créé, le paramètre de propriété DefaultValue est automatiquement entré en tant que valeur du champ. Pour plus d’informations, consultez la rubrique « propriété DefaultValue » dans l’aide de DAO. Vous pouvez définir cette propriété pour un objet TableDef avec [CDaoTableDef :: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

## <a name="remarks"></a>Notes

Les références à Primary, Secondary et All ci-dessus indiquent comment les informations sont retournées par la fonction membre `GetFieldInfo` dans les classes [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo), [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)et [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo).

Les objets de champ ne sont pas représentés par une classe MFC. Au lieu de cela, les objets DAO sous-jacents les objets MFC des classes suivantes contiennent des collections d’objets Field : [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)et [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Ces classes fournissent des fonctions membres pour accéder à certains éléments d’informations de champ, ou vous pouvez y accéder en même temps avec un objet `CDaoFieldInfo` en appelant la fonction membre `GetFieldInfo` de l’objet conteneur.

Outre son utilisation pour l’examen des propriétés de l’objet, vous pouvez également utiliser `CDaoFieldInfo` pour construire un paramètre d’entrée pour la création de nouveaux champs dans un objet TableDef. Des options plus simples sont disponibles pour cette tâche, mais si vous souhaitez un contrôle plus précis, vous pouvez utiliser la version de [CDaoTableDef :: CreateField](../../mfc/reference/cdaotabledef-class.md#createfield) qui accepte un paramètre `CDaoFieldInfo`.

Les informations récupérées par la fonction membre `GetFieldInfo` (de la classe qui contient le champ) sont stockées dans une structure `CDaoFieldInfo`. Appelez la fonction membre `GetFieldInfo` de l’objet conteneur dans dont la collection de champs est stockée. `CDaoFieldInfo` définit également une fonction membre `Dump` dans les versions Debug. Vous pouvez utiliser `Dump` pour vider le contenu d’un objet `CDaoFieldInfo`.

## <a name="requirements"></a>Conditions requises

**En-tête :** afxdao. h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
