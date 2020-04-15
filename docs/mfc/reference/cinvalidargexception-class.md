---
title: Classe CInvalidArgException
ms.date: 11/04/2016
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
ms.openlocfilehash: b28b6e84043b85a8117694a67ff5fff13e7c786b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372374"
---
# <a name="cinvalidargexception-class"></a>Classe CInvalidArgException

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

Un `CInvalidArgException` objet représente une condition d’exception d’argument invalide.

Pour plus d’informations sur le traitement des exceptions, consultez le sujet [de la classe CException](../../mfc/reference/cexception-class.md) et [le traitement des exceptions (MFC).](../../mfc/exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CInvalidArgException`

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="cinvalidargexceptioncinvalidargexception"></a><a name="cinvalidargexception"></a>CInvalidArgException::CInvalidArgException

Constructeur.

```
CInvalidArgException();
```

### <a name="remarks"></a>Notes

N’utilisez pas ce constructeur directement; appeler la fonction globale **AfxThrowInvalidArgException**.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CSimpleException](../../mfc/reference/csimpleexception-class.md)
