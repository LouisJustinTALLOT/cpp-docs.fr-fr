---
title: Cdaoparameterinfo, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoParameterInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f695d1873a2a5a29393da347567674bf1f08e01
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433248"
---
# <a name="cdaoparameterinfo-structure"></a>CDaoParameterInfo, structure

Le `CDaoParameterInfo` structure contient des informations sur un objet de paramètre définie pour les objets d’accès aux données (DAO).

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
Identifiant de manière unique l’objet de paramètre. Pour plus d’informations, consultez la rubrique « Propriété de nom » dans l’aide de DAO.

*m_nType*<br/>
Une valeur qui indique le type de données d’un objet de paramètre. Pour obtenir la liste des valeurs possibles, consultez le *m_nType* membre de la [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) structure. Pour plus d’informations, consultez la rubrique « Propriété de Type » dans l’aide de DAO.

*m_varValue*<br/>
La valeur du paramètre, qui est stocké dans un [COleVariant](../../mfc/reference/colevariant-class.md) objet.

## <a name="remarks"></a>Notes

Les références au principal et secondaire ci-dessus indiquent la façon dont les informations sont retournées par la [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) fonction membre dans la classe `CDaoQueryDef`.

MFC n’encapsule pas les objets de paramètre DAO dans une classe. Querydef DAO objets MFC sous-jacent `CDaoQueryDef` objets stockent des paramètres dans leurs collections de paramètres. Pour accéder aux objets de paramètre dans un [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) d’objet, appelez l’objet querydef `GetParameterInfo` fonction membre pour un nom de paramètre particulier ou un index dans la collection de paramètres. Vous pouvez utiliser la [CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) fonction membre conjointement avec `GetParameterInfo` pour itérer sur la collection de paramètres.

Les informations récupérées par le [CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) fonction membre est stockée dans un `CDaoParameterInfo` structure. Appelez `GetParameterInfo` pour l’objet querydef dans dont la collection de paramètres est stocké l’objet de paramètre.

> [!NOTE]
>  Si vous souhaitez obtenir ou définir uniquement la valeur d’un paramètre, utilisez le [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) et [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) fonctions membres de classe `CDaoRecordset`.

`CDaoParameterInfo` définit également un `Dump` génère de la fonction membre en mode de débogage. Vous pouvez utiliser `Dump` pour vider le contenu d’un `CDaoParameterInfo` objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoQueryDef, classe](../../mfc/reference/cdaoquerydef-class.md)
