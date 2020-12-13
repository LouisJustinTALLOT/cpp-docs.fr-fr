---
description: 'En savoir plus sur : classe CNotSupportedException'
title: CNotSupportedException, classe
ms.date: 11/04/2016
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
ms.openlocfilehash: 61bf729753897e1d30c5a12bc371489ba6f2d64f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331477"
---
# <a name="cnotsupportedexception-class"></a>CNotSupportedException, classe

Représente une exception qui est le résultat d’une requête portant sur une fonctionnalité non prise en charge.

## <a name="syntax"></a>Syntaxe

```
class CNotSupportedException : public CSimpleException
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CNotSupportedException::CNotSupportedException](#cnotsupportedexception)|Construit un objet `CNotSupportedException`.|

## <a name="remarks"></a>Notes

Aucune qualification supplémentaire n’est nécessaire ou possible.

Pour plus d’informations sur l’utilisation de `CNotSupportedException` , consultez l’article [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CNotSupportedException`

## <a name="requirements"></a>Spécifications

**En-tête :** AFX. h

## <a name="cnotsupportedexceptioncnotsupportedexception"></a><a name="cnotsupportedexception"></a> CNotSupportedException::CNotSupportedException

Construit un objet `CNotSupportedException`.

```
CNotSupportedException();
```

### <a name="remarks"></a>Notes

N’utilisez pas ce constructeur directement, mais appelez plutôt la fonction globale [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception). Pour plus d’informations sur le traitement des exceptions, consultez l’article [gestion des exceptions dans MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[CException (classe)](cexception-class.md)<br/>
[Graphique hiérarchique](../hierarchy-chart.md)
