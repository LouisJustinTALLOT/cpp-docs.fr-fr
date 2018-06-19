---
title: Cdaoindexinfo, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoIndexInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Indexes collection
- CDaoIndexInfo structure [MFC]
ms.assetid: 251d8285-78ce-4716-a0b3-ccc3395fc437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d8c98181a9ec049308d7b85e57c028740927cc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367033"
---
# <a name="cdaoindexinfo-structure"></a>CDaoIndexInfo, structure
Le `CDaoIndexInfo` structure contient des informations sur l’objet index défini pour les objets d’accès aux données (DAO).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CDaoIndexInfo {  
    CDaoIndexInfo();
*// Constructor  
    CString m_strName;  // Primary  
    CDaoIndexFieldInfo* m_pFieldInfos;  // Primary  
    short m_nFields;    // Primary  
    BOOL m_bPrimary;    // Secondary  
    BOOL m_bUnique;     // Secondary  
    BOOL m_bClustered;  // Secondary  
    BOOL m_bIgnoreNulls;                // Secondary  
    BOOL m_bRequired;   // Secondary  
    BOOL m_bForeign;    // Secondary  
    long m_lDistinctCount;              // All  
 *// Below the // Implementation comment: *// Destructor, not otherwise documented  
};   
```  
  
#### <a name="parameters"></a>Paramètres  
 `m_strName`  
 Identifie l’objet de champ. Pour plus d’informations, consultez la rubrique « Nom de propriété » dans l’aide de DAO.  
  
 `m_pFieldInfos`  
 Un pointeur vers un tableau de [CDaoIndexFieldInfo](../../mfc/reference/cdaoindexfieldinfo-structure.md) objets indiquant quels champs tabledef ou recordset sont les champs clés dans un index. Chaque objet identifie un champ dans l’index. L’ordre d’index par défaut est croissant. Un objet d’index peut avoir un ou plusieurs champs représentant les clés d’index pour chaque enregistrement. Il peuvent être par ordre croissant, décroissant, ou une combinaison des deux.  
  
 `m_nFields`  
 Le nombre de champs stockés dans `m_pFieldInfos`.  
  
 *m_bPrimary*  
 Si la propriété Primary est **TRUE**, l’objet index représente un index principal. Un index primaire se compose d’un ou plusieurs champs qui identifient de manière unique tous les enregistrements dans une table dans un ordre prédéfini. Étant donné que le champ d’index doit être unique, la propriété Unique de l’objet Index est également définie **TRUE** dans DAO. Si l’index primaire est composée de plusieurs champs, chaque champ peut contenir des valeurs dupliquées, mais chaque combinaison de valeurs à partir de tous les champs indexés doit être unique. Un index primaire est constitué d’une clé pour la table et contient généralement les mêmes champs que la clé primaire.  
  
 Lorsque vous définissez une clé primaire pour une table, la clé primaire est automatiquement définie en tant que l’index primaire de la table. Pour plus d’informations, consultez les rubriques « Propriété principal » et « Propriété Unique » dans l’aide de DAO.  
  
> [!NOTE]
>  Il peut être, au plus, un seul index primaire sur une table.  
  
 *m_bUnique*  
 Indique si un objet index représente un index unique pour une table. Si cette propriété est **TRUE**, l’objet index représente un index unique. Un index unique se compose d’un ou plusieurs champs qui organisent de manière logique tous les enregistrements dans une table dans un ordre prédéfini unique. Si l’index se compose d’un champ, les valeurs dans le champ doivent être uniques pour la table entière. Si l’index se compose de plusieurs champs, chaque champ peut contenir des valeurs dupliquées, mais chaque combinaison de valeurs à partir de tous les champs indexés doit être unique.  
  
 Si les propriétés de l’Unique et le principal d’un objet d’index sont définies sur **TRUE**, l’index est unique et primaire : il identifie de manière unique tous les enregistrements dans la table dans un ordre logique prédéfini. Si la propriété Primary est définie **FALSE**, l’index est un index secondaire. Les index secondaires (clés et non-clés) organiser logiquement les enregistrements dans un ordre prédéfini sans servant d’identificateur pour les enregistrements dans la table.  
  
 Pour plus d’informations, consultez les rubriques « Propriété principal » et « Propriété Unique » dans l’aide de DAO.  
  
 *m_bClustered*  
 Indique si un objet index représente un index cluster pour une table. Si cette propriété est **TRUE**, l’objet index représente un index cluster ; sinon, il n’existe pas. Un index cluster se compose d’un ou plusieurs champs qui, ensemble, organiser tous les enregistrements dans une table dans un ordre prédéfini. Avec un index cluster, les données de la table sont littéralement stockées dans l’ordre spécifié par l’index cluster. Un index ordonné en clusters fournit un accès efficace à des enregistrements dans une table. Pour plus d’informations, consultez la rubrique « Propriété en cluster » dans l’aide de DAO.  
  
> [!NOTE]
>  La propriété Clustered est ignorée pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, car le moteur de base de données Jet ne prend pas en charge les index cluster.  
  
 *m_bIgnoreNulls*  
 Indique s’il existe des entrées d’index pour les enregistrements qui ont des valeurs Null dans les champs d’index. Si cette propriété est **TRUE**, champs avec des valeurs Null n’ont pas une entrée d’index. Pour faciliter la recherche d’enregistrements à l’aide d’un champ plus rapidement, vous pouvez définir un index pour le champ. Si vous autorisez les entrées Null dans un champ indexé et que vous prévoyez de nombreuses entrées NULL, vous pouvez définir la propriété Ignorer Nulls pour l’objet index à **TRUE** pour réduire la quantité d’espace de stockage par l’index. Le paramètre de propriété Ignorer Nulls et le paramètre de propriété requis déterminent si un enregistrement avec une valeur d’index de valeur Null a une entrée d’index, comme le tableau suivant.  
  
|Ignorer Nulls|Obligatoire|Valeur NULL dans le champ de l’index|  
|-----------------|--------------|-------------------------|  
|True|False|Valeur NULL autorisée ; Aucune entrée d’index ajoutée.|  
|False|False|Valeur NULL autorisée ; entrée d’index ajoutée.|  
|True ou False|True|Valeur NULL non autorisée ; Aucune entrée d’index ajoutée.|  
  
 Pour plus d’informations, consultez la rubrique « Ignorer Nulls Property » dans l’aide de DAO.  
  
 `m_bRequired`  
 Indique si un objet d’index DAO requiert une valeur non Null. Si cette propriété est **TRUE**, l’objet index n’autorise pas une valeur Null. Pour plus d’informations, consultez la rubrique « Propriété Required » dans l’aide de DAO.  
  
> [!TIP]
>  Lorsque vous pouvez définir cette propriété pour un objet DAO d’index ou d’un objet field (contenu par recordset, tabledef ou querydef objet), définissez la propriété de l’objet de champ. La validité du paramètre de propriété pour un objet field est vérifiée avant celle d’un objet index.  
  
 *m_bForeign*  
 Indique si un objet index représente une clé étrangère dans une table. Si cette propriété est **TRUE**, l’index représente une clé étrangère dans une table. Une clé étrangère se compose d’un ou plusieurs champs dans une table étrangère qui identifient de manière unique une ligne dans une table primaire. Le moteur de base de données Microsoft Jet crée un objet d’index pour la table étrangère et définit la propriété Foreign lorsque vous créez une relation qui applique l’intégrité référentielle. Pour plus d’informations, consultez la rubrique « Propriété étrangère » dans l’aide de DAO.  
  
 *m_lDistinctCount*  
 Indique le nombre de valeurs uniques pour l’objet index qui sont inclus dans la table associée. Vérifiez la propriété DistinctCount pour déterminer le nombre de valeurs uniques ou des clés, d’un index. N’importe quelle touche est comptée une seule fois, même s’il peut y avoir plusieurs occurrences de cette valeur si l’index autorise les doublons. Ces informations sont utiles dans les applications qui tentent d’optimiser l’accès aux données en évaluant les informations d’index. Le nombre de valeurs uniques est également appelé la cardinalité d’un objet index. La propriété DistinctCount pas toujours reflète le nombre réel de clés à un moment donné. Par exemple, une modification provoquée par la restauration d’une transaction est répercutée immédiatement dans la propriété DistinctCount. Pour plus d’informations, consultez la rubrique « Propriété DistinctCount » dans l’aide de DAO.  
  
## <a name="remarks"></a>Notes  
 Les références au principal, secondaire et tous les ci-dessus indiquent comment les informations sont retournées par la `GetIndexInfo` fonction membre dans les classes [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) et [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).  
  
 Objets d’index ne sont pas représentées par une classe MFC. Au lieu de cela, DAO des objets MFC sous-jacente de la classe d’objets [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) contient une collection d’objets index, appelée la collection d’index. Ces classes fournissent des fonctions de membre pour accéder à des informations sur les index des éléments individuels, ou vous pouvez accéder à la fois avec un `CDaoIndexInfo` objet en appelant le `GetIndexInfo` fonction membre de l’objet conteneur.  
  
 `CDaoIndexInfo` a un constructeur et un destructeur pour allouer et désallouer les informations de champ d’index dans correctement `m_pFieldInfos`.  
  
 Les informations extraites par le `GetIndexInfo` fonction membre d’un objet tabledef est stockée dans un `CDaoIndexInfo` structure. Appelez le `GetIndexInfo` fonction membre de l’objet conteneur tabledef dans dont la collection d’index est stocké l’objet index. `CDaoIndexInfo` définit également un `Dump` builds de la fonction membre en mode débogage. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoIndexInfo` objet.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdao.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)

