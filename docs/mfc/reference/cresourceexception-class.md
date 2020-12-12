---
description: 'En savoir plus sur : classe CResourceException'
title: CResourceException, classe
ms.date: 11/04/2016
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
ms.openlocfilehash: c76635ae2cfa6c55bf54da7e73f6afbb44506fee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264867"
---
# <a name="cresourceexception-class"></a>CResourceException, classe

Générée lorsque Windows ne peut pas trouver ou allouer une ressource demandée.

## <a name="syntax"></a>Syntaxe

```
class CResourceException : public CSimpleException
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CResourceException::CResourceException](#cresourceexception)|Construit un objet `CResourceException`.|

## <a name="remarks"></a>Notes

Aucune qualification supplémentaire n’est nécessaire ou possible.

Pour plus d’informations sur l’utilisation de `CResourceException` , consultez l’article [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cresourceexceptioncresourceexception"></a><a name="cresourceexception"></a> CResourceException::CResourceException

Construit un objet `CResourceException`.

```
CResourceException();
```

### <a name="remarks"></a>Notes

N’utilisez pas ce constructeur directement, mais appelez plutôt la fonction globale [AfxThrowResourceException](exception-processing.md#afxthrowresourceexception). Pour plus d’informations sur les exceptions, consultez l’article [gestion des exceptions dans MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[CException (classe)](cexception-class.md)<br/>
[Graphique hiérarchique](../hierarchy-chart.md)
