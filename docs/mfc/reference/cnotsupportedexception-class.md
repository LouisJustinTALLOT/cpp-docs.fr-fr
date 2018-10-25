---
title: CNotSupportedException, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
dev_langs:
- C++
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b52151dba90c0cfd0ed834e2ef351838d598eb90
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068800"
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

Pour plus d’informations sur l’utilisation de `CNotSupportedException`, consultez l’article [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CNotSupportedException`

## <a name="requirements"></a>Configuration requise

**En-tête :** afx.h

##  <a name="cnotsupportedexception"></a>  CNotSupportedException::CNotSupportedException

Construit un objet `CNotSupportedException`.

```
CNotSupportedException();
```

### <a name="remarks"></a>Notes

N’utilisez pas ce constructeur directement, mais plutôt appeler la fonction globale [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception). Pour plus d’informations sur le traitement des exceptions, consultez l’article [gestion des exceptions dans MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[CException, classe](cexception-class.md)<br/>
[Graphique hiérarchique](../hierarchy-chart.md)

