---
description: 'En savoir plus sur : structure Cdaoindexinfo,'
title: CDaoIndexInfo, structure
ms.date: 06/25/2018
f1_keywords:
- CDaoIndexInfo
helpviewer_keywords:
- DAO (Data Access Objects), Indexes collection
- CDaoIndexInfo structure [MFC]
ms.assetid: 251d8285-78ce-4716-a0b3-ccc3395fc437
ms.openlocfilehash: 2e09846789dc91e4d0df67665f3e975b557c07c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250762"
---
# <a name="cdaoindexinfo-structure"></a>CDaoIndexInfo, structure

La `CDaoIndexInfo` structure contient des informations sur un objet index défini pour les objets d’accès aux données (DAO).

## <a name="syntax"></a>Syntaxe

```cpp
struct CDaoIndexInfo {
    CDaoIndexInfo();                    // Constructor
    CString m_strName;                  // Primary
    CDaoIndexFieldInfo* m_pFieldInfos;  // Primary
    short m_nFields;                    // Primary
    BOOL m_bPrimary;                    // Secondary
    BOOL m_bUnique;                     // Secondary
    BOOL m_bClustered;                  // Secondary
    BOOL m_bIgnoreNulls;                // Secondary
    BOOL m_bRequired;                   // Secondary
    BOOL m_bForeign;                    // Secondary
    long m_lDistinctCount;              // All

    // Below the // Implementation comment:
    // Destructor, not otherwise documented
};
```

### <a name="parameters"></a>Paramètres

*m_strName*<br/>
Nomme l’objet de champ de façon unique. Pour plus d’informations, consultez la rubrique « propriété de nom » dans l’aide de DAO.

*m_pFieldInfos*<br/>
Pointeur vers un tableau d’objets [cdaoindexfieldinfo,](../../mfc/reference/cdaoindexfieldinfo-structure.md) indiquant les champs de l’objet TableDef ou Recordset qui sont des champs clés dans un index. Chaque objet identifie un champ dans l’index. L’ordre d’index par défaut est croissant. Un objet index peut avoir un ou plusieurs champs représentant des clés d’index pour chaque enregistrement. Il peut s’agir de l’ordre croissant, décroissant ou d’une combinaison.

*m_nFields*<br/>
Nombre de champs stockés dans `m_pFieldInfos` .

*m_bPrimary*<br/>
Si la propriété primaire a la valeur TRUE, l’objet index représente un index primaire. Un index primaire est constitué d’un ou de plusieurs champs qui identifient de manière unique tous les enregistrements d’une table dans un ordre prédéfini. Étant donné que le champ d’index doit être unique, la propriété unique de l’objet index est également définie sur TRUE dans DAO. Si l’index primaire est constitué de plusieurs champs, chaque champ peut contenir des valeurs dupliquées, mais chaque combinaison de valeurs de tous les champs indexés doit être unique. Un index primaire est constitué d’une clé pour la table et contient généralement les mêmes champs que la clé primaire.

Lorsque vous définissez une clé primaire pour une table, la clé primaire est définie automatiquement comme index primaire de la table. Pour plus d’informations, consultez les rubriques « propriété primaire » et « propriété unique » dans l’aide de DAO.

> [!NOTE]
> Il peut y avoir, au plus, un index principal sur une table.

*m_bUnique*<br/>
Indique si un objet index représente un index unique pour une table. Si cette propriété a la valeur TRUE, l’objet index représente un index unique. Un index unique est constitué d’un ou de plusieurs champs qui réorganisent logiquement tous les enregistrements d’une table dans un ordre prédéfini unique. Si l’index se compose d’un champ, les valeurs de ce champ doivent être uniques pour l’ensemble de la table. Si l’index est constitué de plusieurs champs, chaque champ peut contenir des valeurs dupliquées, mais chaque combinaison de valeurs de tous les champs indexés doit être unique.

Si les propriétés unique et Primary d’un objet index sont toutes les deux définies sur TRUE, l’index est unique et Primary : il identifie de manière unique tous les enregistrements de la table dans un ordre logique prédéfini. Si la propriété Primary est définie sur FALSe, l’index est un index secondaire. Les index secondaires (clés et non-clés) réorganisent logiquement les enregistrements dans un ordre prédéfini sans servir d’identificateur pour les enregistrements de la table.

Pour plus d’informations, consultez les rubriques « propriété primaire » et « propriété unique » dans l’aide de DAO.

*m_bClustered*<br/>
Indique si un objet index représente un index cluster d’une table. Si cette propriété a la valeur TRUE, l’objet index représente un index cluster ; Sinon, ce n’est pas le cas. Un index cluster est constitué d’un ou de plusieurs champs non-clés qui, réunis, réorganisent tous les enregistrements d’une table dans un ordre prédéfini. Avec un index cluster, les données de la table sont littéralement stockées dans l’ordre spécifié par l’index cluster. Un index cluster fournit un accès efficace aux enregistrements d’une table. Pour plus d’informations, consultez la rubrique « propriété en cluster » dans l’aide de DAO.

> [!NOTE]
> La propriété Clustered est ignorée pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, car le moteur de base de données Jet ne prend pas en charge les index cluster.

*m_bIgnoreNulls*<br/>
Indique s’il existe des entrées d’index pour les enregistrements qui ont des valeurs NULL dans leurs champs d’index. Si cette propriété a la valeur TRUE, les champs avec des valeurs NULL n’ont pas d’entrée d’index. Pour accélérer la recherche d’enregistrements à l’aide d’un champ, vous pouvez définir un index pour le champ. Si vous autorisez les entrées NULL dans un champ indexé et si vous vous attendez à ce que la plupart des entrées aient la valeur null, vous pouvez définir la propriété IgnoreNulls de l’objet index sur TRUE pour réduire la quantité d’espace de stockage utilisée par l’index. Le paramètre de propriété IgnoreNulls et le paramètre de propriété Required déterminent ensemble si un enregistrement avec une valeur d’index null a une entrée d’index, comme le montre le tableau suivant.

|IgnoreNulls|Obligatoire|NULL dans le champ d’index|
|-----------------|--------------|-------------------------|
|True|False|Valeur null autorisée ; aucune entrée d’index n’a été ajoutée.|
|False|False|Valeur null autorisée ; entrée d’index ajoutée.|
|True ou False|True|Valeur NULL non autorisée ; aucune entrée d’index n’a été ajoutée.|

Pour plus d’informations, consultez la rubrique « propriété IgnoreNulls » dans l’aide de DAO.

*m_bRequired*<br/>
Indique si un objet index DAO requiert une valeur non null. Si cette propriété a la valeur TRUE, l’objet index n’autorise pas de valeur null. Pour plus d’informations, consultez la rubrique « propriété requise » dans l’aide de DAO.

> [!TIP]
> Lorsque vous pouvez définir cette propriété pour un objet d’index DAO ou un objet de champ (contenu dans un objet TableDef, Recordset ou querydef), définissez-le pour l’objet de champ. La validité du paramètre de propriété d’un objet de champ est vérifiée avant celle d’un objet d’index.

*m_bForeign*<br/>
Indique si un objet index représente une clé étrangère dans une table. Si cette propriété a la valeur TRUE, l’index représente une clé étrangère dans une table. Une clé étrangère se compose d’un ou plusieurs champs d’une table étrangère qui identifient de façon unique une ligne dans une table primaire. Le moteur de base de données Microsoft Jet crée un objet d’index pour la table étrangère et définit la propriété Foreign lorsque vous créez une relation qui applique l’intégrité référentielle. Pour plus d’informations, consultez la rubrique « propriété étrangère » dans l’aide de DAO.

*m_lDistinctCount*<br/>
Indique le nombre de valeurs uniques pour l’objet index qui sont incluses dans la table associée. Vérifiez la propriété DistinctCount pour déterminer le nombre de valeurs uniques, ou clés, dans un index. Une clé n’est comptée qu’une seule fois, même s’il peut y avoir plusieurs occurrences de cette valeur si l’index autorise les valeurs en double. Ces informations sont utiles dans les applications qui tentent d’optimiser l’accès aux données en évaluant les informations d’index. Le nombre de valeurs uniques est également appelé la cardinalité d’un objet index. La propriété DistinctCount ne reflète pas toujours le nombre réel de clés à un moment donné. Par exemple, une modification due à une restauration de transaction ne sera pas reflétée immédiatement dans la propriété DistinctCount. Pour plus d’informations, consultez la rubrique « propriété DistinctCount » dans l’aide de DAO.

## <a name="remarks"></a>Notes

Les références à Primary, Secondary et All ci-dessus indiquent comment les informations sont retournées par la `GetIndexInfo` fonction membre dans les classes [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) et [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).

Les objets d’index ne sont pas représentés par une classe MFC. Au lieu de cela, les objets DAO sous-jacents les objets MFC de la classe [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) contiennent une collection d’objets index, appelée la collection Indexes. Ces classes fournissent des fonctions membres pour accéder aux éléments individuels des informations d’index, ou vous pouvez y accéder en même temps avec un `CDaoIndexInfo` objet en appelant la `GetIndexInfo` fonction membre de l’objet conteneur.

`CDaoIndexInfo` a un constructeur et un destructeur pour allouer et libérer correctement les informations de champ d’index dans `m_pFieldInfos` .

Les informations récupérées par la `GetIndexInfo` fonction membre d’un objet TableDef sont stockées dans une `CDaoIndexInfo` structure. Appelez la `GetIndexInfo` fonction membre de l’objet TableDef conteneur dans dont la collection d’index est stockée dans l’objet index. `CDaoIndexInfo` définit également une `Dump` fonction membre dans les versions Debug. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoIndexInfo` objet.

## <a name="requirements"></a>Spécifications

**En-tête :** afxdao. h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef :: GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)
