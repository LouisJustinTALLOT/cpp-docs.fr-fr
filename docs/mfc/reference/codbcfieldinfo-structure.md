---
description: 'En savoir plus sur : structure Codbcfieldinfo,'
title: CODBCFieldInfo, structure
ms.date: 11/04/2016
f1_keywords:
- CODBCFieldInfo
helpviewer_keywords:
- ODBC [MFC], data source information
- CODBCFieldInfo structure [MFC]
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
ms.openlocfilehash: 7cd7072719bec46cfbfaeb02c5c86d714c4de13c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331418"
---
# <a name="codbcfieldinfo-structure"></a>CODBCFieldInfo, structure

La `CODBCFieldInfo` structure contient des informations sur les champs d’une source de données ODBC.

## <a name="syntax"></a>Syntaxe

```
struct CODBCFieldInfo
{
    CString m_strName;
    SWORD m_nSQLType;
    UDWORD m_nPrecision;
    SWORD m_nScale;
    SWORD m_nNullability;
};
```

#### <a name="parameters"></a>Paramètres

*m_strName*<br/>
Nom du champ.

*m_nSQLType*<br/>
Type de données SQL du champ. Il peut s’agir d’un type de données SQL ODBC ou d’un type de données SQL spécifique au pilote. Pour obtenir la liste des types de données SQL ODBC valides, consultez « SQL Data types » dans le SDK Windows. Pour plus d’informations sur les types de données SQL spécifiques au pilote, consultez la documentation du pilote.

*m_nPrecision*<br/>
Précision maximale du champ. Pour plus d’informations, consultez « précision, échelle, longueur et taille d’affichage » dans le SDK Windows.

*m_nScale*<br/>
Échelle du champ. Pour plus d’informations, consultez « précision, échelle, longueur et taille d’affichage » dans le SDK Windows.

*m_nNullability*<br/>
Indique si le champ accepte une valeur null. Il peut s’agir de l’une des deux valeurs suivantes : SQL_NULLABLE si le champ accepte des valeurs NULL, ou SQL_NO_NULLS si le champ n’accepte pas les valeurs NULL.

## <a name="remarks"></a>Notes

Pour récupérer ces informations, appelez [CRecordset :: GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo).

## <a name="requirements"></a>Spécifications

**En-tête :** AFXDB. h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRecordset :: GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)<br/>
[CRecordset :: GetFieldValue](../../mfc/reference/crecordset-class.md#getfieldvalue)
