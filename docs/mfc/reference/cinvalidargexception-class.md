---
title: Cinvalidargexception, classe
ms.date: 11/04/2016
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
ms.openlocfilehash: d532698b19a6652feb6e42fdb429d89d49e6ac7b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445420"
---
# <a name="cinvalidargexception-class"></a>Cinvalidargexception, classe

Cette classe représente une condition d’exception d’argument non valide.

## <a name="syntax"></a>Syntaxe

```
class CInvalidArgException : public CSimpleException
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CInvalidArgException::CInvalidArgException](#cinvalidargexception)|Constructeur.|

## <a name="remarks"></a>Notes

Un `CInvalidArgException` objet représente une condition d’exception argument non valide.

Pour plus d’informations sur la gestion des exceptions, consultez le [CException (classe)](../../mfc/reference/cexception-class.md) rubrique et [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CInvalidArgException`

## <a name="requirements"></a>Configuration requise

**En-tête :** afx.h

##  <a name="cinvalidargexception"></a>  CInvalidArgException::CInvalidArgException

Constructeur.

```
CInvalidArgException();
```

### <a name="remarks"></a>Notes

N’utilisez pas ce constructeur directement ; Appelez la fonction globale **AfxThrowInvalidArgException**.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CSimpleException, classe](../../mfc/reference/csimpleexception-class.md)
