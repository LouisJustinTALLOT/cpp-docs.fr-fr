---
title: CDaoFieldInfo, structure
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: 9466386fefc6e5ab8fcf89bf497c1d5219e3e807
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368411"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo, structure

La `CDaoFieldInfo` structure contient des informations sur un objet de terrain défini pour les objets d’accès aux données (DAO).

DAO est soutenu par Office 2013. DAO 3.6 est la version finale, et il est considéré comme obsolète.

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
Nomme uniquement l’objet de champ. Pour plus de détails, voir le thème "Nom propriété" dans DAO Aide.

*m_nType*<br/>
Une valeur qui indique le type de données du champ. Pour plus de détails, voir le thème "Type Property" dans DAO Help. La valeur de cette propriété peut être l’une des suivantes :

- `dbBoolean`Oui/Non, comme TRUE/FALSE

- `dbByte`Octet

- `dbInteger`Court

- `dbLong`Long

- `dbCurrency`Monnaie; voir MFC classe [COleCurrency](../../mfc/reference/colecurrency-class.md)

- `dbSingle`Seul

- `dbDouble`Double

- `dbDate`Date/Heure; voir MFC classe [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText`Texte; voir MFC classe [CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary` Long Binary (objet OLE); vous souhaiterez peut-être utiliser la classe MFC [CByteArray](../../mfc/reference/cbytearray-class.md) au lieu de la classe `CLongBinary` comme `CByteArray` est plus riche et plus facile à utiliser.

- `dbMemo`Mémo; voir classe MFC`CString`

- `dbGUID`Un identifiant unique à l’échelle mondiale/identifiant universellement unique utilisé avec des appels de procédure à distance. Pour plus d’informations, consultez le thème "Type Property" dans DAO Help.

> [!NOTE]
> N’utilisez pas de types de données de chaîne pour les données binaires. Cela provoque la passage de vos données à travers la couche de traduction Unicode/ANSI, ce qui entraîne une augmentation des frais généraux et peut-être une traduction inattendue.

*m_lSize*<br/>
Une valeur qui indique la taille maximale, dans les octets, d’un objet de champ DAO qui contient du texte ou la taille fixe d’un objet de champ qui contient du texte ou des valeurs numériques. Pour plus de détails, voir le thème "Propriété de taille" dans DAO Aide. Les tailles peuvent être l’une des valeurs suivantes :

|Type|Taille (octets)|Description|
|----------|--------------------|-----------------|
|`dbBoolean`|1 octet|Oui/Non (même que True/False)|
|`dbByte`|1|Byte|
|`dbInteger`|2|Integer|
|`dbLong`|4|Long|
|`dbCurrency`|8|Monnaie ([COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Unique|
|`dbDouble`|8|Double|
|`dbDate`|8|Date/Heure ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Texte ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Long Binaire (objet OLE; [CByteArray](../../mfc/reference/cbytearray-class.md); utilisation au `CLongBinary`lieu de )|
|`dbMemo`|0|Mémo ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|Un identifiant unique à l’échelle mondiale/identifiant universellement unique utilisé avec des appels de procédure à distance.|

*m_lAttributes*<br/>
Spécifie les caractéristiques d’un objet de champ contenu par un objet de dépôt, d’enregistrement, de requête ou d’index. La valeur retournée peut être une somme de ces constantes, créées avec l’opérateur de bitwise-OR** (&#124;) **:

- `dbFixedField`La taille du champ est fixe (par défaut pour les champs Numeric).

- `dbVariableField`La taille du champ est variable (Champs de texte seulement).

- `dbAutoIncrField`La valeur de champ pour les nouveaux enregistrements est automatiquement incrémentée à un intégrant long unique qui ne peut pas être changé. Seulement pris en charge pour les tables de base de données Microsoft Jet.

- `dbUpdatableField`La valeur du champ peut être modifiée.

- `dbDescending`Le champ est trié dans l’ordre descendant (Z - A ou 100 - 0) (ne s’applique qu’à un objet de champ dans une collection Fields d’un objet index; dans MFC, les objets index sont eux-mêmes contenus dans des objets de table). Si vous ometez cette constante, le champ est trié dans l’ordre ascendant (A - Z ou 0 - 100) (par défaut).

Lors de la vérification du réglage de cette propriété, vous**&** pouvez utiliser l’opérateur bitwise-AND () pour tester un attribut spécifique. Lors de la définition de plusieurs attributs, vous pouvez les combiner en combinant les constantes appropriées avec l’opérateur bitwise-OR (**&#124;). ** Pour plus de détails, voir le sujet "Attributes Property" dans DAO Help.

*m_nOrdinalPosition*<br/>
Une valeur qui spécifie l’ordre numérique dans lequel vous souhaitez qu’un champ représenté par un objet de champ DAO soit affiché par rapport à d’autres champs. Vous pouvez définir cette propriété avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield). Pour plus de détails, voir le thème "OrdinalPosition Property" dans DAO Help.

*m_bRequired*<br/>
Indique si un objet de champ DAO nécessite une valeur non-Null. Si cette propriété est VRAI, le champ ne permet pas une valeur Null. Si requis est réglé sur FALSE, le champ peut contenir des valeurs nulles ainsi que des valeurs qui répondent aux conditions spécifiées par les paramètres de propriété AllowZeroLength et ValidationRule. Pour plus de détails, consultez le thème «Propriété requise» dans DAO Aide. Vous pouvez définir cette propriété pour un tabledef avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_bAllowZeroLength*<br/>
Indique si une chaîne vide ("") est une valeur valide d’un objet de champ DAO avec un type de données textuelle ou de note. Si cette propriété est VRAI, une chaîne vide est une valeur valide. Vous pouvez définir cette propriété à FALSE pour vous assurer que vous ne pouvez pas utiliser une chaîne vide pour définir la valeur d’un champ. Pour plus de détails, voir le sujet "AllowZeroLength Property" dans DAO Help. Vous pouvez définir cette propriété pour un tabledef avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_lCollatingOrder*<br/>
Spécifie la séquence de l’ordre de tri dans le texte pour la comparaison ou le tri des cordes. Pour plus de détails, consultez le thème « Personnaliser les paramètres du registre Windows pour l’accès aux données » dans L’aide DAO. Pour une liste des valeurs possibles `m_lCollatingOrder` retournées, voir le membre de la structure [CDaoDatabaseInfo.](../../mfc/reference/cdaodatabaseinfo-structure.md) Vous pouvez définir cette propriété pour un tabledef avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strForeignName*<br/>
Une valeur qui, en relation, spécifie le nom de l’objet de champ DAO dans une table étrangère qui correspond à un champ dans une table primaire. Pour plus de détails, voir le thème "ForeignName Property" dans DAO Help.

*m_strSourceField*<br/>
Indique le nom du champ qui est la source originale des données d’un objet de champ DAO contenu par un objet de dépôt, de dossiers ou de requête. Cette propriété indique le nom de champ original associé à un objet de champ. Par exemple, vous pouvez utiliser cette propriété pour déterminer la source originale des données dans un champ de requête dont le nom n’est pas lié au nom du champ dans le tableau sous-jacent. Pour plus de détails, voir le sujet "SourceField, SourceTable Properties" dans DAO Help. Vous pouvez définir cette propriété pour un tabledef avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strSourceTable*<br/>
Indique le nom de la table qui est la source originale des données d’un objet de champ DAO contenu par un objet de dépôt, de dossiers ou de requête. Cette propriété indique le nom de table d’origine associé à un objet de champ. Par exemple, vous pouvez utiliser cette propriété pour déterminer la source originale des données dans un champ de requête dont le nom n’est pas lié au nom du champ dans le tableau sous-jacent. Pour plus de détails, voir le sujet "SourceField, SourceTable Properties" dans DAO Help. Vous pouvez définir cette propriété pour un tabledef avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strValidationRule*<br/>
Une valeur qui valide les données dans un champ tel qu’il est modifié ou ajouté à un tableau. Pour plus de détails, voir le sujet "ValidationRule Property" dans DAO Help. Vous pouvez définir cette propriété pour un tabledef avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

Pour plus d’informations sur les `m_strValidationRule` dépôts, consultez le membre de la structure [CDaoTableDefInfo.](../../mfc/reference/cdaotabledefinfo-structure.md)

*m_strValidationText*<br/>
Une valeur qui spécifie le texte du message que votre application affiche si la valeur d’un objet de champ DAO ne satisfait pas à la règle de validation spécifiée par le paramètre de propriété ValidationRule. Pour plus de détails, consultez le thème "ValidationText Property" dans DAO Help. Vous pouvez définir cette propriété pour un tabledef avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

*m_strDefaultValue*<br/>
La valeur par défaut d’un objet de champ DAO. Lorsqu’un nouvel enregistrement est créé, le paramètre de propriété DefaultValue est automatiquement entré comme valeur pour le champ. Pour plus de détails, consultez le sujet "DefaultValue Property" dans DAO Help. Vous pouvez définir cette propriété pour un tabledef avec [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).

## <a name="remarks"></a>Notes

Les références à Primaire, Secondaire, et Tous ci-dessus indiquent comment l’information est retournée `GetFieldInfo` par la fonction membre dans les classes [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo), [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo), et [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo).

Les objets de terrain ne sont pas représentés par une classe MFC. Au lieu de cela, les objets DAO sous-jacents MFC objets des classes suivantes contiennent des collections d’objets de terrain: [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md), et [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Ces classes fournissent des fonctions de membre pour accéder à certains éléments `CDaoFieldInfo` individuels de `GetFieldInfo` l’information sur le terrain, ou vous pouvez y accéder tous à la fois avec un objet en appelant la fonction membre de l’objet contenant.

Outre son utilisation pour l’examen `CDaoFieldInfo` des propriétés de l’objet, vous pouvez également utiliser pour construire un paramètre d’entrée pour créer de nouveaux champs dans un tabledef. Des options plus simples sont disponibles pour cette tâche, mais si vous voulez un contrôle plus fin, `CDaoFieldInfo` vous pouvez utiliser la version de [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield) qui prend un paramètre.

Les informations récupérées par la `GetFieldInfo` fonction membre (de la `CDaoFieldInfo` classe qui contient le champ) sont stockées dans une structure. Appelez `GetFieldInfo` la fonction membre de l’objet contenant dans la collection Fields dont l’objet de champ est stocké. `CDaoFieldInfo`définit également `Dump` une fonction de membre dans les constructions de débogé. Vous pouvez `Dump` utiliser pour vider le contenu d’un `CDaoFieldInfo` objet.

## <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
