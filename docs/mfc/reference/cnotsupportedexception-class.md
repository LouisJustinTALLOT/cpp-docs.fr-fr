---
title: Classe D’origine CNotSupportedException
ms.date: 11/04/2016
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
ms.openlocfilehash: b859b939baef018e69b245e597eea90e608253ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363191"
---
# <a name="cnotsupportedexception-class"></a>Classe D’origine CNotSupportedException

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

Aucune autre qualification n’est nécessaire ou possible.

Pour plus d’informations sur l’utilisation `CNotSupportedException`, voir l’article Exception Handling [(MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CNotSupportedException`

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="cnotsupportedexceptioncnotsupportedexception"></a><a name="cnotsupportedexception"></a>CNotSupportedException::CNotSupportedException

Construit un objet `CNotSupportedException`.

```
CNotSupportedException();
```

### <a name="remarks"></a>Notes

N’utilisez pas ce constructeur directement, mais appelez plutôt la fonction globale [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception). pour plus d’informations sur le traitement des exceptions, voir l’article [Exception Handling dans MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[Classe CException](cexception-class.md)<br/>
[Graphique hiérarchique](../hierarchy-chart.md)
