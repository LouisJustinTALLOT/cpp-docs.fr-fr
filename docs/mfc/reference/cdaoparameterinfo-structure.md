---
title: CDaoParameterInfo, structure
ms.date: 09/17/2019
f1_keywords:
- CDaoParameterInfo
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
ms.openlocfilehash: 6d594bbeec34e400eb074c136e3467e78b35c4ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368979"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo, structure

La `CDaoParameterInfo` structure contient des informations sur un objet paramètre défini pour les objets d’accès aux données (DAO). DAO 3.6 est la version finale, et il est considéré comme obsolète.

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
Nomme uniquement l’objet de paramètre. Pour plus d’informations, consultez le thème "Nom Propriété" dans DAO Aide.

*m_nType*<br/>
Une valeur qui indique le type de données d’un objet paramètre. Pour une liste des valeurs possibles, voir le *m_nType* membre de la structure [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md) Pour plus d’informations, consultez le thème "Type Property" dans DAO Help.

*m_varValue*<br/>
La valeur du paramètre, stocké dans un objet [COleVariant.](../../mfc/reference/colevariant-class.md)

## <a name="remarks"></a>Notes

Les références au primaire et au secondaire ci-dessus indiquent comment l’information `CDaoQueryDef`est retournée par la fonction membre [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) en classe .

MFC n’encapsule pas les objets paramètreS DAO dans une classe. Les objets DAO requêteref `CDaoQueryDef` sous-jacents aux objets MFC stockent les paramètres de leurs collections De Paramètres. Pour accéder aux objets paramètres d’un objet [CDaoQueryDef,](../../mfc/reference/cdaoquerydef-class.md) appelez la fonction membre de `GetParameterInfo` l’objet de requête pour un nom de paramètre particulier ou un index dans la collection Paramètres. Vous pouvez utiliser la fonction de membre [CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) fonction de membre en conjonction avec `GetParameterInfo` en boucle à travers la collection Paramètres.

Informations récupérées par le [CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) fonction `CDaoParameterInfo` membre est stocké dans une structure. Appelez `GetParameterInfo` l’objet requête dans lequel les Paramètres collectionner l’objet paramètre est stocké.

> [!NOTE]
> Si vous souhaitez obtenir ou définir uniquement la valeur d’un paramètre, utilisez les fonctions `CDaoRecordset`membres [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) et [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) de la classe .

`CDaoParameterInfo`définit également `Dump` une fonction de membre dans les constructions de débogé. Vous pouvez `Dump` utiliser pour vider le contenu d’un `CDaoParameterInfo` objet.

## <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Classe CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)
