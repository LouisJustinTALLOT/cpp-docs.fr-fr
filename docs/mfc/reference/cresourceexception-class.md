---
title: Classe CResourceException
ms.date: 11/04/2016
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
ms.openlocfilehash: 557bfe1cc41c3dda65bd95d7d687820c0b9862b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368328"
---
# <a name="cresourceexception-class"></a>Classe CResourceException

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

Aucune autre qualification n’est nécessaire ou possible.

Pour plus d’informations sur l’utilisation `CResourceException`, voir l’article Exception Handling [(MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cresourceexceptioncresourceexception"></a><a name="cresourceexception"></a>CResourceException::CResourceException

Construit un objet `CResourceException`.

```
CResourceException();
```

### <a name="remarks"></a>Notes

N’utilisez pas ce constructeur directement, mais appelez plutôt la fonction globale [AfxThrowResourceException](exception-processing.md#afxthrowresourceexception). pour plus d’informations sur les exceptions, voir l’article [Exception Handling dans MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[Classe CException](cexception-class.md)<br/>
[Graphique hiérarchique](../hierarchy-chart.md)
