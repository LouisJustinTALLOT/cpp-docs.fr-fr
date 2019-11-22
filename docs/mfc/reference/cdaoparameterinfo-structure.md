---
title: CDaoParameterInfo, structure
ms.date: 09/17/2019
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 9f96cba8ea43db7e24e834b1de4ffb593b2c6e0d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303483"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo, structure

La structure `CDaoParameterInfo` contient des informations sur un objet de paramètre défini pour les objets d’accès aux données (DAO). DAO 3,6 est la version finale et est considéré comme obsolète.

## <a name="syntax"></a>Syntaxe

```
struct CDaoParameterInfo
{
    CString m_strName;       // Primary
    short m_nType;           // Primary
    ColeVariant m_varValue;  // Secondary
};
```

#### <a name="parameters"></a>Paramètres

*m_strName*<br/>
Nomme l’objet de paramètre de façon unique. Pour plus d’informations, consultez la rubrique « propriété de nom » dans l’aide de DAO.

*m_nType*<br/>
Valeur qui indique le type de données d’un objet de paramètre. Pour obtenir la liste des valeurs possibles, consultez le membre *m_nType* de la structure [cdaofieldinfo,](../../mfc/reference/cdaofieldinfo-structure.md) . Pour plus d’informations, consultez la rubrique « type Property » dans l’aide de DAO.

*m_varValue*<br/>
Valeur du paramètre, stockée dans un objet [COleVariant](../../mfc/reference/colevariant-class.md) .

## <a name="remarks"></a>Notes

Les références à Primary et Secondary ci-dessus indiquent comment les informations sont retournées par la fonction membre [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) dans la classe `CDaoQueryDef`.

MFC n’encapsule pas les objets de paramètre DAO dans une classe. Les objets querydef DAO sous-jacents aux objets MFC `CDaoQueryDef` stockent des paramètres dans leurs collections de paramètres. Pour accéder aux objets Parameter dans un objet [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) , appelez la fonction membre `GetParameterInfo` de l’objet querydef pour un nom de paramètre particulier ou un index dans la collection Parameters. Vous pouvez utiliser la fonction membre [CDaoQueryDef :: GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) conjointement avec `GetParameterInfo` pour parcourir la collection Parameters.

Les informations récupérées par la fonction membre [CDaoQueryDef :: GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) sont stockées dans une structure `CDaoParameterInfo`. Appelez `GetParameterInfo` pour l’objet querydef dans la collection de paramètres dans laquelle l’objet Parameter est stocké.

> [!NOTE]
>  Si vous souhaitez obtenir ou définir uniquement la valeur d’un paramètre, utilisez les fonctions membres [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) et [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) de la classe `CDaoRecordset`.

`CDaoParameterInfo` définit également une fonction membre `Dump` dans les versions Debug. Vous pouvez utiliser `Dump` pour vider le contenu d’un objet `CDaoParameterInfo`.

## <a name="requirements"></a>Conditions requises

**En-tête :** afxdao. h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef, classe](../../mfc/reference/cdaoquerydef-class.md)
