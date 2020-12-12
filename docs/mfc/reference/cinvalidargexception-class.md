---
description: 'En savoir plus sur : classe CInvalidArgException'
title: CInvalidArgException, classe
ms.date: 11/04/2016
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
ms.openlocfilehash: f68642747a81d1c45a8246f4f25abfb8b79c81d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202793"
---
# <a name="cinvalidargexception-class"></a>CInvalidArgException, classe

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

Un `CInvalidArgException` objet représente une condition d’exception d’argument non valide.

Pour plus d’informations sur la gestion des exceptions, consultez la rubrique relative à la [classe CException](../../mfc/reference/cexception-class.md) et à la [gestion des exceptions (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CInvalidArgException`

## <a name="requirements"></a>Spécifications

**En-tête :** AFX. h

## <a name="cinvalidargexceptioncinvalidargexception"></a><a name="cinvalidargexception"></a> CInvalidArgException::CInvalidArgException

Constructeur.

```
CInvalidArgException();
```

### <a name="remarks"></a>Notes

N’utilisez pas ce constructeur directement. appelez la fonction globale **AfxThrowInvalidArgException**.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CSimpleException, classe](../../mfc/reference/csimpleexception-class.md)
