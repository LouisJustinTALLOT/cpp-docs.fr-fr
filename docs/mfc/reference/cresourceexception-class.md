---
title: Cresourceexception, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
dev_langs:
- C++
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e1fea7db1ef79eed2bc2678bd1e9283c71bb161
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071860"
---
# <a name="cresourceexception-class"></a>Cresourceexception, classe

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

Pour plus d’informations sur l’utilisation de `CResourceException`, consultez l’article [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="cresourceexception"></a>  CResourceException::CResourceException

Construit un objet `CResourceException`.

```
CResourceException();
```

### <a name="remarks"></a>Notes

N’utilisez pas ce constructeur directement, mais plutôt appeler la fonction globale [AfxThrowResourceException](exception-processing.md#afxthrowresourceexception). Pour plus d’informations sur les exceptions, consultez l’article [gestion des exceptions dans MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[CException, classe](cexception-class.md)<br/>
[Graphique hiérarchique](../hierarchy-chart.md)

